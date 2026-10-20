# Code&Ops — Metaindústria | Sprint 4

> **Status: documentação preparada; aplicação executável NÃO incluída neste pacote.** Este repositório exportado contém material de planejamento da Sprint 3 e consolidação documental da Sprint 4. **Não é uma entrega funcional pronta**. Substituir esta nota somente depois de incluir e validar o código.

## Proposta de solução
A Code&Ops propõe uma plataforma de segurança industrial preventiva para apoiar a identificação de ausência de EPIs, a visualização de alertas, o registro e tratamento de ocorrências e a consulta de histórico. A detecção por IA (YOLOv8), câmeras e avisos em tempo real fazem parte da visão do produto, mas **não são demonstrados nem comprovados pelos arquivos deste ZIP**. O MVP de integração proposto utiliza API Spring Boot e app React Native/Expo para gerenciar ocorrências.

## Equipe — FIAP
- Davi da Silva Biaggioli — RM 552581
- Jean Lucas Loureiro Depieri — RM 555797
- João Gabriel De Bortoli Ribeiro — RM 554601
- Lucas Akira Watanabe — RM 554875
- Luiz Guilherme de Souza Varischi — RM 559028
- Francisco Ferrara Neto — RM 557209

## Links
- [Board Scrum / Sprint 4](https://trello.com/b/ntk03CPj/to-do)
- [Figma — protótipo](https://www.figma.com/design/LuqIAuOSWLSUjLfNhVX3Km?node-id=0-1)
- **GitHub do frontend final:** PREENCHER_URL_FRONTEND
- **GitHub do backend final:** PREENCHER_URL_BACKEND
- **Vídeo de pitch (YouTube não listado):** PREENCHER_URL_YOUTUBE

## Estado comprovado dos artefatos
| Item | Situação nesta cópia |
|---|---|
| Diagramas, requisitos, Product Backlog e documentação da Sprint 3 | Presentes |
| Sprint Backlog da Sprint 4, revisão e documentação de arquitetura | Preparados nesta atualização |
| Código-fonte React Native / Expo | **Ausente** |
| Código-fonte Java / Spring Boot | **Ausente** |
| Testes de CRUD, persistência, navegação e integração | **Não executados; exigem os códigos** |
| Inferência YOLOv8 e câmeras em tempo real | **Não verificadas** |
| Vídeo e Sprint Review executada | **Pendentes** |

## Stack prevista para a integração
- **Backend:** Java 17, Spring Boot, Maven, Spring Web/Data JPA, banco H2 persistido em arquivo, CORS configurado.
- **Frontend:** React Native com Expo, TypeScript, Axios, pasta `src/services/`.
- **IA (proposta de produto):** Python, YOLOv8 e pipeline de vídeo, dependente de código, modelo e medição para validação.

> O README antigo sugeria Flask/FastAPI e Oracle como stack da solução; esses componentes continuam descritos como alternativas/proposta histórica. **Não declarar que estão integrados à aplicação Spring Boot sem código ou evidências.**

## Como executar — roteiro para ser validado quando o código for anexado
**Pré-requisitos:** JDK 17 (`java -version`), Maven (`mvn -version`) ou Maven Wrapper, Node.js LTS, npm e Expo Go / emulador compatível.

### Backend
1. Abra a pasta do backend **real**. Verifique se existe `pom.xml`.
2. Configure `application.properties` para porta `8080` e H2 em arquivo (por exemplo `jdbc:h2:file:./data/codeops`), conforme o projeto real. Evite inserir credenciais de produção no Git.
3. Execute `./mvnw spring-boot:run` (Linux/macOS, se houver wrapper), `mvn spring-boot:run` (se Maven instalado) ou `mvnw.cmd spring-boot:run` (Windows).
4. Teste o endpoint **real do projeto** (a URL de exemplo `/api/ocorrencias` não deve ser assumida até validação), documentando GET/POST/PUT/DELETE e códigos HTTP.

### Frontend
1. Abra a pasta do frontend **real**, que deverá possuir `package.json`.
2. Rode `npm install` e `npx expo start` (adaptar se o projeto utilizar outro gerenciador).
3. Configure a base URL da API na pasta `src/services/`. **Celular físico:** usar IP LAN do computador, na mesma rede e com firewall liberado. **Emulador Android:** em geral `http://10.0.2.2:8080`. **iOS Simulator/web local:** `http://localhost:8080`, conforme o ambiente.
4. Valide lista, cadastro, detalhes/tratamento, atualização, exclusão se aplicável, histórico, sem mocks no fluxo principal.
5. Desligue o backend e comprove uma mensagem de erro visível no app, sem apresentar dados locais como se fossem da API.

**Importante:** os comandos acima são instruções condicionais, não resultado de teste. Revisar com o código integrado, endpoints reais, versões e prints antes da submissão.

## Arquitetura, processo e validação
- [Arquitetura final — estado proposto e lacunas](docs/sprint4/ARQUITETURA_FINAL.md)
- [Backlog Sprint 4](docs/sprint4/SPRINT_BACKLOG.md)
- [Ata de Review final — modelo a preencher após reunião](docs/sprint4/REVIEW_FINAL.md)
- [Casos de teste e validação de entrega](docs/sprint4/VALIDACAO_FINAL.md)
- [Roteiro do pitch](docs/sprint4/ROTEIRO_PITCH.md)
- [Rastreabilidade e evolução Sprint 1–4](docs/sprint4/EVOLUCAO_SPRINTS.md)
- [Documentos originais da Sprint 3](docs/sprint3/)

## Manual resumido do produto (fluxo-alvo)
1. Abrir app, acessar tela inicial/login conforme implementação real.
2. Consultar dashboard/ocorrências persistidas pela API.
3. Cadastrar ocorrência com validações.
4. Abrir detalhe e registrar a providência ou alterar status; distinguir alerta resolvido de aptidão atual do trabalhador.
5. Consultar o histórico e filtros, quando implementados.

## Entrega acadêmica
Enviar **somente** o arquivo `.txt` com nomes/RMs e links válidos de GitHub, Trello e YouTube. Modelo em `SPRINT4_ENTREGA_CODEOPS.txt`. O pacote de documentação não substitui a aplicação nem o vídeo.
