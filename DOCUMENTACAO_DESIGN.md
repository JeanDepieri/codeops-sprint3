# Documentação de Design de Interface e UX/UI — Sistema Code&Ops (Metaindústria)

## 1. Introdução
Este documento serve como a documentação oficial de design de interface e experiência do usuário (UX/UI) do Sistema Code&Ops para o ecossistema Metaindústria. O objetivo deste arquivo é registrar formalmente as decisões de design, a arquitetura das telas, o fluxo de navegação e a rastreabilidade direta entre os elementos visuais apresentados no protótipo final de alta fidelidade e os casos de uso, requisitos e diagramas UML estabelecidos na Sprint 1.

Com foco em Segurança Industrial Proativa, esta documentação descreve as escolhas de interface voltadas para a usabilidade do Supervisor de Segurança no chão de fábrica, garantindo coesão absoluta entre a percepção por inteligência artificial (YOLOv8) e a gestão administrativa da plataforma.

---

## 2. Arquitetura das Telas

### Tela 1: Portal de Autenticação (Login)
* **Objetivo:** Restringir o acesso à plataforma e identificar o profissional de SST responsável pela supervisão do turno.
* **Quem utiliza:** Supervisor de Segurança (Carlos Rocha).
* **Principais componentes:** Logotipo oficial da equipe `Code&Ops`, campos de entrada falsos (placeholders) para `ID Supervisor...` e `Senha...`, e botão de ação `Acessar Plataforma`.
* **Ações possíveis:** Digitar credenciais e disparar a validação de acesso.
* **Fluxo:** Tela 1 (Login) → Tela 2 (Monitoramento)

### Tela 2: Dashboard de Monitoramento (Real Time)
* **Objetivo:** Exibir em tempo real o fluxo de processamento de imagem com as bounding boxes da IA e os indicadores lógicos de aptidão do operador.
* **Quem utiliza:** Supervisor de Segurança.
* **Principais componentes:** Menu lateral fixo (Monitoramento, Gestão de EPIs, Central de Alerta, Relatórios), painel esquerdo com indicadores (`Status maquinário: operante`, `ID Operador: 46`, `Não-conformidades: 0`, lista de `EPI's requeridos` com tags dinâmicas e indicador master `APTO`), e o feed de vídeo centralizado simulando a inferência em tempo real da rede neural (`welding helmet xx%`, `gloves xx%`, `person xx%`).
* **Ações possíveis:** Supervisionar a linha de produção e alternar de tela através do menu de navegação.
* **Fluxo:**
  * Tela 2 → Tela 3 (Gestão de EPIs)
  * Tela 2 → Tela 4 (Central de Alerta)
  * Tela 2 → Tela 5 (Relatórios)

### Tela 3: Gestão de EPIs por Função
* **Objetivo:** Parametrizar e consultar quais equipamentos de proteção são obrigatórios para cada área ou cargo industrial cadastrado.
* **Quem utiliza:** Supervisor de Segurança / Engenheiro de Systems.
* **Principais componentes:** Menu lateral de navegação fixo, coluna esquerda de seleção de funções (`Soldagem`, `Fundição`, `Usinagem`, `Manutenção Industrial`, `Eletricista`, `Logística e Carga`, `Processos Químicos`), botão `+ Nova Função`, listagem centralizada de checkboxes de EPIs disponíveis (Capacete, Óculos, Luvas, Protetor Auricular, Máscara, Colete Refletivo) e botão `Confirmar Configuração`.
* **Ações possíveis:** Selecionar um cargo, customizar as regras de obrigatoriedade e salvar as diretrizes do setor.
* **Fluxo:**
  * Tela 3 → Tela 7 (Popup de Confirmação de EPIs)

### Tela 4: Central de Alerta (Lista em Tempo Real)
* **Objetivo:** Listar e documentar cronologicamente os incidentes críticos e as não-conformidades de segurança identificadas pelas câmeras de visão computacional.
* **Quem utiliza:** Supervisor de Segurança.
* **Principais componentes:** Menu lateral fixo, cards empilhados de infrações contendo o carimbo visual de exclamação em vermelho (`Status: INAPTO`), identificação passiva (`Colaborador: João Silva Santos`, `Recorrência: 2`, `Setor: Linha de Fundição`), infração mapeada (`Ausência de Luvas Térmicas Obrigatórias`) e a diretriz automática de contenção do sistema (`Ação: Máquina Parada até Regularização de EPI's`).
* **Ações possíveis:** Auditar a lista de infrações recorrentes e verificar o plano de ação sugerido pelo sistema.
* **Fluxo:** Tela 4 → Menu Lateral Livre

### Tela 5: Painel de Relatórios Gerenciais
* **Objetivo:** Consolidar os logs armazenados no banco de dados Oracle em forma de indicadores gráficos para auditorias e análise da gerência industrial.
* **Quem utiliza:** Gestor Industrial / Diretora de Operações (Mariana Costa).
* **Principais componentes:** Menu lateral fixo, gráfico de rosca (`Distribuição de Detecção de EPIs Ausentes` detalhando `Gloves 42,9%`, `Glasses 23,8%`, `Reflective Vest 14,3%`, etc.), gráfico de linhas (`Evolução Mensal de Incidentes — Primeiro Semestre 2026`), gráfico de barras horizontais (`Taxa de Conformidade Geral por Setor`) e botão `EXPORTAR`.
* **Ações possíveis:** Analisar as estatísticas de segurança do trabalho e exportar o relatório gerencial unificado.
* **Fluxo:** Tela 5 → Tela 6 (Popup de Sucesso do Relatório)

### Tela 6: Feedback de Impressão / Relatório Emitido
* **Objetivo:** Modal/Popup de feedback visual confirmando que a exportação e persistência física dos dados em PDF foram finalizadas com sucesso.
* **Quem utiliza:** Gestor Industrial / Diretora de Operações.
* **Principais componentes:** Ícone de check de validação verde, mensagem de sistema: `"Relatório Gerencial de SST processado com sucesso. Arquivo exportado para a pasta local de auditoria de logs"`, e botão de controle `Voltar a Home`.
* **Ações possíveis:** Fechar a notificação e retornar à navegação padrão do sistema.
* **Fluxo:** Tela 6 → Tela 2 (Dashboard)

### Tela 7: Confirmação de Cadastro de Regras
* **Objetivo:** Modal/Popup de feedback que valida o salvamento físico das alterações na matriz de regras de aptidão por função no banco de dados.
* **Quem utiliza:** Supervisor de Segurança.
* **Principais componentes:** Ícone de check centralizado, mensagem textual: `"Configuração de EPIs obrigatórios para essa função concluído!"`, e botão `Voltar a Home`.
* **Ações possíveis:** Fechar o modal e retornar para a tela inicial estável.
* **Fluxo:** Tela 7 → Tela 2 (Dashboard)

---

## 3. Mapa Completo de Navegação

```text
Tela 1: Portal de Autenticação (Login)
 └── Tela 2: Dashboard de Monitoramento (Real Time)
      ├── Tela 3: Gestão de EPIs por Função
      │     └── Tela 7: Confirmação de Cadastro de Regras (Popup)
      │           └── Tela 2: Dashboard de Monitoramento (Retorno)
      ├── Tela 4: Central de Alerta (Lista em Tempo Real)
      └── Tela 5: Painel de Relatórios Gerenciais
            └── Tela 6: Feedback de Impressão / Relatório Emitido (Popup)
                  └── Tela 2: Dashboard de Monitoramento (Retorno)
