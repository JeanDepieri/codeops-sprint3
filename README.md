# Code&Ops

## Integrantes
* Davi da Silva Biaggioli - RM: 552581
* Jean Lucas Loureiro Depieri - RM: 555797
* João Gabriel De Bortoli Ribeiro - RM: 554601
* Lucas Akira Watanabe - RM: 554875
* Luiz Guilherme de Souza Varischi - RM: 559028      
* Francisco Ferrara Neto - RM: 557209

## Escopo da Solução & O Problema
No cenário industrial tradicional, a segurança do trabalho opera sob um modelo **punitivo e reativo**: o trabalhador é advertido ou multado após a infração ser detectada (muitas vezes após o acidente ocorrer). 

A nossa solução propõe a transição para um modelo de **Segurança Industrial Proativa** dentro do ecossistema da **Metaindústria**. Utilizando monitoramento contínuo baseado em inteligência artificial e computação na borda (Edge Computing), o sistema identifica riscos — como a ausência de Equipamentos de Proteção Individual (EPIs) em funções industriais — e emite **alertas visuais e sonoros em tempo real** diretamente no chão de fábrica. O foco é a **prevenção imediata**, atuando antes que a infração se converta em um acidente de trabalho.

### Delimitação do Escopo
* **Dentro do Escopo:** Detecção de 6 EPIs prioritários (capacete, óculos de segurança, luvas, protetor auricular/abafador, máscara e colete refletivo), emissão de alertas em tempo real, lógica de aptidão customizada por função, integração com câmeras e geração de relatórios de conformidade.
* **Fora do Escopo Atual:** Controle de acesso físico (catracas/portas), armazenamento de vídeos em nuvem, identificação nominal do colaborador (reconhecimento facial), emissão automática de advertências/penalidades e gestão de estoque de EPIs.

## Escolhas Tecnológicas e Justificativa Técnica
A arquitetura do projeto foi estruturada focando em máxima performance e estabilidade para o ecossistema industrial:

* **Linguagem Principal: Python**
  * *Justificativa:* Linguagem padrão e extremamente robusta para o desenvolvimento de soluções baseadas em Inteligência Artificial, oferecendo ecossistema maduro para manipulação de fluxos de vídeo.
* **Framework de Visão Computacional: YOLOv8**
  * *Justificativa:* Inicialmente, testamos a API pronta do Roboflow Universe, que apresentou instabilidades e travamentos constantes para o processamento em tempo real. Optamos por baixar o dataset e treinar de forma nativa o modelo YOLOv8, com meta de baixa latência e precisão superior a 90%, ainda dependente de avaliação documentada. O material fornecido não contém medições que comprovem esses resultados.
* **Ambiente de Prototipagem e Dataset: Roboflow**
  * *Justificativa:* Utilizado estritamente para a coleta, organização e exportação do dataset unificado (mesclando dados públicos e capturas reais de EPIs do Makerlab da FIAP).
* **Interface e Dashboard: Flask / FastAPI + Painel Web**
  * *Justificativa:* Frameworks Python leves para servir a lógica de regras de aptidão, processar os dados da webcam em tempo real e alimentar o dashboard de monitoramento com os alertas visuais e sonoros necessários.
* **Banco de Dados Relacional: Oracle Database**
  * *Justificativa:* Garante a persistência confiável e íntegra dos logs de auditoria (data, hora e tipo de desconformidade) para a geração de relatórios gerenciais e suporte a auditorias de SST.


## Sprint 3 — Evolução do protótipo e gestão ágil

O protótipo desta Sprint utiliza a documentação das entregas anteriores como referência. Não foi disponibilizada uma versão anterior do Figma para comparação visual. O escopo acordado contém quatro telas: login, monitoramento, histórico e detalhe/tratamento de ocorrência.

### Artefatos

- [Protótipo no Figma](https://www.figma.com/design/LuqIAuOSWLSUjLfNhVX3Km?node-id=0-1)
- [Board Scrum no Trello](https://trello.com/b/ntk03CPj/to-do)
- [Product Backlog priorizado](docs/sprint3/PRODUCT_BACKLOG.md)
- [Sprint Backlog](docs/sprint3/SPRINT_BACKLOG.md)
- [Definição de Pronto](docs/sprint3/DEFINITION_OF_DONE.md)
- [Cerimônias Scrum — registros pendentes](docs/sprint3/CERIMONIAS.md)
- [Refinamento da arquitetura](docs/sprint3/ARQUITETURA.md)
- [Evolução do protótipo](docs/sprint3/EVOLUCAO_PROTOTIPO.md)
- [Roteiro de validação](docs/sprint3/VALIDACAO.md)
- [Pendências para entrega](docs/sprint3/PENDENCIAS.md)

### Justificativa das mudanças

| Evolução | Razão | Requisitos |
|---|---|---|
| Histórico com período, setor e situação | Permitir consultar ocorrências além do monitoramento atual e tornar o log de auditoria acessível | RF05, RF06, RF07 |
| Detalhe e tratamento com providência registrada | Contextualizar a não conformidade e documentar a ação administrativa; a resolução não comprova aptidão atual | RF04, RF05, RF06 |
| Navegação concentrada em quatro telas | Reduzir a complexidade da demonstração e tornar explícito o caminho de consulta e atendimento | Refinamento de usabilidade |

A base já previa alertas e tratamento simples. A evolução proposta aprofunda a consulta histórica e o registro detalhado da providência. Não se alega comparação com telas anteriores não disponíveis. A aceitação dessa referência documental para o requisito de evolução deve ser confirmada com o professor.

### Situação da entrega

Jean informou a conclusão do Figma. A navegação e o acesso do avaliador ainda precisam de revisão registrada. Os documentos técnicos e os backlogs estão preparados; cerimônias e aprovação do grupo permanecem pendentes. Os dados das telas são demonstrativos e não comprovam implementação de autenticação, API, inferência ou persistência.

O ZIP original contém documentação e diagramas, não uma aplicação executável. A arquitetura da Sprint 3 é uma proposta técnica para implementação e validação.
