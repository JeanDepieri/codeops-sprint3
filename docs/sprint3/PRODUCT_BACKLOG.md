# Product Backlog priorizado — Code&Ops

Proposta de priorização para validação na Planning. P0 = essencial ao ciclo de segurança e rastreabilidade; P1 = consolidação/gestão; P2 = expansão. A ordem dentro de cada prioridade indica a sequência sugerida. Não representa funcionalidades já implementadas.

A Sprint 3 seleciona a evolução **do protótipo** de PB03/PB04 e o refinamento arquitetural. Não promete implementar todo o produto. Responsáveis serão definidos no Sprint Backlog, sem atribuir retroativamente trabalho aos integrantes.

| Ordem | Prioridade | Item | Requisitos | Recorte da Sprint 3 |
|---|---|---|---|---|
| PB01 | P0 | Capturar vídeo e indicar perda de sinal | RF01, RNF01, RNF03 | Revisar arquitetura e estados |
| PB02 | P0 | Detectar seis EPIs e avaliar aptidão | RF02, RF03, RNF02 | Revisar regras e limitações |
| PB03 | P0 | Detalhar e tratar alertas com rastreabilidade | RF04, RF05, RF06 | Evoluir protótipo |
| PB04 | P0 | Consultar histórico com filtros | RF05, RF06, RF07 | Evoluir protótipo |
| PB05 | P1 | Configurar regras de EPIs por função | RF03 | Documentado; fora das quatro telas da Sprint 3 |
| PB06 | P1 | Emitir relatório de conformidade | RF07 | Documentado; fora das quatro telas da Sprint 3 |
| PB07 | P1 | Alertas visuais e sonoros locais | RF04 | Revisar responsabilidades técnicas |

A ordem prioriza o ciclo de detecção e resposta, seguido de rastreabilidade e gestão. Os critérios abaixo descrevem o resultado pretendido do produto; sua existência neste documento não comprova implementação.

## PB01 — Capturar vídeo e indicar perda de sinal

**Valor:** Supervisor acompanha câmera e sabe quando a análise está indisponível.

**Critério de aceite:** Vídeo ativo quando maquinário operante; sinal perdido resulta em INDETERMINADO; estado standby distinguível.

## PB02 — Detectar os seis EPIs e avaliar aptidão

**Valor:** Supervisor identifica não conformidade conforme regras da função.

**Critério de aceite:** Confrontar EPIs obrigatórios e detectados; separar confiança por detecção de métricas do modelo; validar desempenho antes de alegar precisão.

## PB03 — Detalhar e tratar alertas com rastreabilidade

**Valor:** Supervisor registra a providência tomada e acompanha o estado do alerta.

**Critério de aceite:** Abrir detalhe, iniciar atendimento, exigir observação ao resolver e exibir histórico; resolver alerta não significa declarar APTO.

## PB04 — Consultar histórico de ocorrências com filtros

**Valor:** Gestor encontra ocorrências por período, setor, EPI e situação.

**Critério de aceite:** Filtros combinados, limpeza, período inválido, vazio, falha e acesso ao detalhe preservando filtros.

## PB05 — Configurar regras de EPIs por função

**Valor:** Supervisor atualiza os requisitos de cada função.

**Critério de aceite:** Salvar configuração com confirmação, validar campos e preservar versão das regras em cada ocorrência.

## PB06 — Emitir relatório de conformidade

**Valor:** Gestor analisa indicadores por período e setor.

**Critério de aceite:** Escopo do relatório visível; estados sem dados, erro e sucesso; arquivo consistente com filtros.

## PB07 — Integrar alertas visuais e sonoros locais

**Valor:** Operador recebe orientação imediata e não punitiva.

**Critério de aceite:** Alerta visual e sonoro testável; evitar repetição contínua por frame; falha de saída identificável.

## Limites de escopo

Apenas os requisitos do ZIP de Engenharia de Software fundamentam este backlog. Câmeras IP, totem, smartwatch e análise de pose eventualmente presentes no board não fazem parte desta proposta. RNF04–RNF06 permanecem como restrições transversais: execução local, privacidade e ausência de controle físico de acesso.

## Vínculos de referência no Trello

Links registrados durante a preparação anterior; este documento não confirma o status atual do board.


- [PB01](https://trello.com/c/wN1dtxnD/77-pb01p0-capturar-v%C3%ADdeo-e-indicar-perda-de-sinal)
- [PB02](https://trello.com/c/OY9C4HMQ/78-pb02p0-detectar-os-seis-epis-e-avaliar-aptid%C3%A3o)
- [PB03](https://trello.com/c/T5xgA3dY/79-pb03p0-detalhar-e-tratar-alertas-com-rastreabilidade)
- [PB04](https://trello.com/c/QOtQGDOQ/80-pb04p0-consultar-hist%C3%B3rico-de-ocorr%C3%AAncias-com-filtros)
- [PB05](https://trello.com/c/XWmkXRIr/81-pb05p1-configurar-regras-de-epis-por-fun%C3%A7%C3%A3o)
- [PB06](https://trello.com/c/Gp383kNk/82-pb06p1-emitir-relat%C3%B3rio-de-conformidade)
- [PB07](https://trello.com/c/2NeACaph/83-pb07p1-integrar-alertas-visuais-e-sonoros-locais)
