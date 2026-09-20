## Engenharia de Requisitos

A especificação dos requisitos abaixo delimita o escopo de atuação do protótipo desenvolvido para a ABDI, garantindo o alinhamento entre as necessidades do chão de fábrica e a viabilidade técnica da solução de visão computacional.

---

### Requisitos Funcionais (RF)
*Os Requisitos Funcionais descrevem as ações, comportamentos e funcionalidades que o sistema deve executar.*

* **RF01 - Captura de Fluxo de Vídeo:** O sistema deve ser capaz de capturar e processar continuamente o fluxo de vídeo proveniente de uma webcam comum ou câmera integrada.
* **RF02 - Detecção Automatizada de EPIs:** O sistema deve identificar, por meio do modelo de visão computacional treinado, a presença ou a ausência de 6 EPIs prioritários: capacete, óculos de segurança, luvas, protetor auricular/abafador, máscara e colete refletivo.
* **RF03 - Lógica de Aptidão por Função:** O sistema deve executar uma inteligência de regras configurável que cruza os EPIs detectados com as exigências específicas da área ou função, emitindo o veredito de **APTO** ou **INAPTO** para o trabalho em tempo real.
* **RF04 - Disparo de Alertas Visuais e Sonoros:** O sistema deve emitir um aviso sonoro e alertas visuais imediatos na tela de monitoramento assim que uma situação de não conformidade (colaborador inapto) for detectada.
* **RF05 - Painel de Monitoramento (Dashboard):** O sistema deve disponibilizar uma interface gráfica (dashboard) centralizada para exibição do status de conformidade atual e dos alertas gerados.
* **RF06 - Registro de Log de Auditoria:** O sistema deve armazenar em banco de dados o histórico de cada detecção de risco, salvando dados cruciais como data, hora e a respectiva inconformidade para fins de rastreabilidade.
* **RF07 - Geração de Relatórios Periódicos:** O sistema deve permitir a consolidação de relatórios diários, semanais e mensais focados em estatísticas de segurança e conformidade de SST (Saúde e Segurança do Trabalho).

---

### Requisitos Não Funcionais (RNF) & Restrições
*Os Requisitos Não Funcionais definem os critérios de qualidade, desempenho e os limites operacionais do sistema.*

* **RNF01 - Processamento em Tempo Real:** O tempo de resposta entre a captura da imagem pela câmera, o processamento analítico pela inteligência artificial e a emissão do alerta visual/sonoro deve ocorrer em tempo real (baixa latência).
* **RNF02 - Confiabilidade da Detecção:** O modelo de visão computacional desenvolvido com a arquitetura YOLOv8 deve atingir e manter uma taxa de precisão superior a 90% na classificação dos EPIs essenciais.
* **RNF03 - Ativação Vinculada ao Status do Maquinário (Gatilho Operacional):** O sistema de monitoramento por visão computacional e emissão de alertas deve operar sob demanda, sendo ativado automaticamente se, e enquanto, as máquinas e equipamentos do respectivo setor estiverem ligados/operantes. Caso o maquinário seja desligado, o módulo de processamento de imagem daquela área entra em modo de espera (standby), otimizando o uso de hardware.
* **RNF04 - Restrição de Infraestrutura Atual:** Durante a fase atual de MVP e prototipagem, o sistema é restrito a rodar utilizando a infraestrutura local dos notebooks do grupo e captação de imagens via webcams convencionais.
* **RNF05 - Proteção à Privacidade (Sem Reconhecimento Facial):** O escopo do sistema é estritamente limitado à identificação de objetos (EPIs), estando parametrizado para ficar **fora do escopo** qualquer tipo de identificação nominal ou reconhecimento facial dos colaboradores.
* **RNF06 - Limitação de Escopo de Entrega:** O projeto restringe-se à entrega de um protótipo funcional validado para a ABDI apresentado no NEXT de 2026, deixando fora desta etapa a implantação em ambiente industrial real, escalabilidade massiva ou controle de acesso físico (como travas de catracas).
