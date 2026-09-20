## Perfis dos Usuários (Personas)

Para garantir que o sistema atenda perfeitamente às demandas reais de segurança e operação, a solução foi modelada com base em três perfis principais de usuários que interagem com o ecossistema industrial.

---

### 1. O Operador de Chão de Fábrica
* **Nome Fictício:** João Silva (34 anos)
* **Papel/Função:** Operador na linha de fundição de uma indústria metalúrgica.
* **Contexto e Rotina:** É um profissional experiente que conhece muito bem o chão de fábrica. Trabalha em um ambiente dinâmico e focado em produtividade. Pela pressa do dia a dia, cansaço ou pura distração, está sujeito a cometer pequenos lapsos, como esquecer periféricos essenciais na bancada (ex: luvas térmicas ou óculos de segurança).
* **Dores que sofre:** Falta de um mecanismo imediato que o lembre de se proteger antes de iniciar uma tarefa de risco, o que o deixa exposto a acidentes graves (como queimaduras ou lesões por impacto).
* **Relação com o Sistema:** Interação Passiva. Ele não opera o software, não usa mouses ou telas. O sistema funciona como um "anjo da guarda" visual: ao passar pela área de cobertura da câmera, se o modelo identificar a ausência de um dos 6 EPIs obrigatórios, o status de João muda para **INAPTO** e ele é alertado localmente para corrigir sua conduta antes de se acidentar.

---

### 2. O Supervisor de Segurança (Técnico de SST)
* **Nome Fictício:** Carlos Rocha (35 anos)
* **Papel/Função:** Técnico de Segurança do Trabalho e Resposta a Riscos.
* **Contexto e Rotina:** Responsável por garantir a integridade dos colaboradores e a conformidade da planta com as normas regulamentadoras brasileiras (NR-6 e NR-9). Ele precisa monitorar múltiplos setores, turnos e dezenas de funcionários simultaneamente.
* **Dores que sofre:** Fiscalização humana insuficiente. É fisicamente impossível para um único supervisor verificar a conformidade de cada operador, em cada acesso à área de risco, o tempo todo. Sofre também com a subnotificação de incidentes cotidianos.
* **Relação com o Sistema:** Interação Operacional Ativa. Utiliza a interface do dashboard de monitoramento em tempo real. Ele consome os alertas visuais e sonoros de não conformidade emitidos pela IA. O sistema automatiza a ronda de segurança, permitindo que Carlos intervenha de forma cirúrgica e preventiva onde há risco iminente.

---

### 3. O Gestor Industrial / Diretor de Operações
* **Nome Fictício:** Mariana Costa (48 anos)
* **Papel/Função:** Gestora de Unidade Industrial / Diretora de Operações.
* **Contexto e Rotina:** Profissional focada em indicadores estratégicos de performance, eficiência global da fábrica, redução de custos operacionais e governança corporativa.
* **Dores que sofre:** Prejuízos financeiros e institucionais gerados por acidentes de trabalho (afastamentos, processos judiciais, indenizações e queda de produtividade), além da falta de dados estatísticos confiáveis e auditáveis para tomadas de decisão em segurança.
* **Relação com o Sistema:** Interação Estratégica. Não acompanha os alertas de milissegundos do chão de fábrica, mas utiliza o sistema para extrair relatórios gerenciais analíticos (diários, semanais e mensais). Mariana analisa as métricas de conformidade por setor e o histórico de logs auditáveis para direcionar treinamentos de segurança e avaliar o impacto real do sistema na redução de sinistros da planta.
