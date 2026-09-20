# Evolução do protótipo — Sprint 3

## Referência e situação

[Figma informado pelo grupo](https://www.figma.com/design/LuqIAuOSWLSUjLfNhVX3Km?node-id=0-1). Jean informou nesta conversa que concluiu a montagem no Figma. A revisão independente das conexões permanece pendente: a integração atingiu o limite do plano.

Não foi disponibilizada uma versão anterior do Figma para comparação visual. A referência desta evolução é a documentação de requisitos, design e navegação das Sprints 1 e 2. A inexistência dessa comparação deve ser comunicada ao professor; a aceitação desse enquadramento ainda precisa ser confirmada.

## Escopo reduzido acordado

| Tela | Finalidade | Justificativa / requisitos |
|---|---|---|
| Login | Entrada demonstrativa do supervisor | Fluxo de acesso descrito na documentação anterior; não representa autenticação implementada |
| Monitoramento | Exibir EPIs detectados, não conformidade e acesso ao histórico | Representar RF01–RF05 em interface compreensível |
| Histórico de ocorrências | Exibir registros e filtros por período, setor e situação | Dar visibilidade ao log de RF06 e apoiar consultas de RF05/RF07 |
| Detalhe e tratamento | Mostrar contexto, providência e responsável pelo registro | Aprofundar rastreabilidade de RF04–RF06; resolver não altera a aptidão original |

Histórico e tratamento detalhado são os dois fluxos de evolução propostos. A documentação anterior já previa alertas e indicação de tratamento; portanto, a novidade não é simplesmente marcar um alerta como tratado, mas detalhar seu contexto e registrar a providência com rastreabilidade.

A interface usa dados e imagens demonstrativos. As quatro referências visuais foram produzidas com apoio de IA; a montagem no Figma foi informada pelo usuário. Não há comprovação de API, banco, autenticação ou detecção real por meio das imagens.

## Fluxo de apresentação

Login → Monitoramento → Histórico → Detalhe e tratamento → confirmação na própria tela → Histórico.

Cancelamento retorna ao histórico sem salvar. O acesso ao histórico e o retorno ao monitoramento devem funcionar. A confirmação deve ser distinguível do estado anterior ao envio. Consultas vazias e falhas permanecem refinamentos futuros; não se exigem novas telas completas para elas neste recorte.

## Revisão

Executar o [roteiro de validação](VALIDACAO.md). Não afirmar que filtros são interativos se apenas seus campos foram desenhados. Identificar interações simuladas no protótipo e registrar limitações na Review.
