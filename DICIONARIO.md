## Dicionário de Classes e Estrutura Lógica (UML — Padrão Aula ES 08)

Para dar sustentação ao fluxo de monitoramento do sistema desenvolvido pela equipe *Code&Ops*, mapeamos as entidades lógicas do software utilizando os conceitos de visibilidade, atributos (dados) e métodos (ações) em conformidade com o padrão UML:

### 1. PerfilFuncao
* *Descrição:* Entidade responsável por gerenciar as regras de negócio de forma parametrizável. Ela dita quais dos 6 EPIs prioritários (Capacete, Óculos, Luvas, Protetor Auricular, Máscara e Colete) são obrigatórios para um determinado setor ou cargo industrial.
* *Atributos:*
    *  idPerfil: int — Identificador único do perfil de regras.
    *  nomeFuncao: String — Nome do cargo ou área monitorada (ex: "Operador de Solda").
    *  episObrigatorios: List<String> — Características contendo a lista de EPIs exigidos por lei para o setor.
* *Métodos:*
    *  verificarAptidao(episDetectados: List<String>): bool — Ação que cruza os dados recebidos da IA com as exigências do perfil para retornar o veredito do operador.

### 2. InferenciaEPI
* *Descrição:* Objeto gerado dinamicamente a cada frame capturado pela câmera e processado pelo pipeline de Visão Computacional (*YOLOv8*).
* *Atributos:*
    *  idInferencia: Guid — Identificador único global do evento de varredura.
    *  dataHora: DateTime — Característica de timestamp do momento exato da captura.
    *  episIdentificados: List<String> — Lista contendo os EPIs efetivamente reconhecidos pela IA no frame.
    *  precisaoPercentual: double — Confidence score reportado pelo modelo matemático.
* *Métodos:*
    *  processarFrame(frameBytes: byte[]): InferenciaEPI — Ação que recebe os dados brutos da webcam e invoca o modelo YOLOv8, retornando a instância preenchida.

### 3. RegistroLog
* *Descrição:* Entidade de persistência que registra o histórico contínuo e auditável das conformidades e não-conformidades no banco de dados.
* *Atributos:*
    *  idLog: long — Identificador sequencial no banco de dados.
    *  timestamp: DateTime — Data e hora do registro físico.
    *  estaApto: bool — Estado final de segurança do operador detectado no frame.
    *  setorIndustrial: String — Localização física de onde o evento foi gerado.
* *Métodos:*
    *  salvar(): bool — Ação que persiste a instância corrente no banco de dados.
    *  obterPorPeriodo(inicio: DateTime, fim: DateTime): List<RegistroLog> — Recupera registros históricos para alimentar os relatórios do dashboard.

### 4. AlertaRisco
* *Descrição:* Gatilho de ação imediata que opera na camada de interface e periféricos sempre que uma infração (status estaApto == false) é detectada.
* *Atributos:*
    *  idAlerta: int — Identificador único do alerta gerado.
    *  mensagem: String — Texto descritivo detalhando a violação (ex: "ATENÇÃO: Operador sem Capacete").
    *  foiTratado: bool — Controle indicando se o supervisor já tomou providências em campo.
* *Métodos:*
    *  dispararSinalSonoro(): void — Aciona o sinalizador sonoro no ambiente industrial.
    *  renderizarNaTela(): void — Envia a notificação visual em tempo real para o Dashboard do Supervisor.

---

## Relacionamentos — Justificativa das Conexões

Seguindo a analogia de como as coisas do mundo real se conectam e gerenciam seus ciclos de vida, definimos as conexões do nosso software:

* **InferenciaEPI ─ PerfilFuncao (Associação Simples — Multiplicidade 0.. * para 1)*
  * *Justificativa:* Uma InferenciaEPI usa ou conhece uma instância de PerfilFuncao para realizar o cruzamento lógico dos dados. Nenhum controla o ciclo de vida do outro; a inferência apenas referencia o perfil para consumir o método de validação.
* *RegistroLog ─ InferenciaEPI (Agregação — Multiplicidade 1 para 1)*
  * *Justificativa:* Relação de "todo-parte" fraca. O RegistroLog tem uma InferenciaEPI que gerou aquele evento. Se o log histórico for deletado do banco por regras de retenção, os dados brutos da inferência gerados pela IA continuam fazendo sentido de forma isolada na camada de percepção. A parte sobrevive sem o todo.
* *RegistroLog ─ AlertaRisco (Composição — Multiplicidade 1 para 0.. 1)*
  * *Justificativa:* Relação de "todo-parte" forte ("a diferença entre ser sócio e ser dono"). O AlertaRisco pertence estritamente ao seu RegistroLog de origem. Se o registro de log de uma infração for excluído ou resetado, o alerta em tela perde o sentido existencial, sumindo junto com o todo. A parte *não existe* sem o todo.
