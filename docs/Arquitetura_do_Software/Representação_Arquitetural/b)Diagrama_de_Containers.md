# O que é um Diagrama de Containers?
O Diagrama de Containers faz parte do Modelo C4 (nível 2) e mostra a arquitetura de alto nível do sistema, ou seja:
Quais são os principais containers (blocos executáveis), como:<br>
Aplicativos<br>
APIs<br>
Bancos de dados<br>
Sistemas externos<br>
E como esses containers se comunicam entre si<br>

# Para que serve?
Demonstrar como o sistema é dividido (ex.: app, backend, banco, serviços externos).<br>
Mostrar os fluxos de comunicação (HTTP, Pub/Sub, APIs externas).<br>
Ajudar na compreensão da arquitetura geral do sistema.<br>
Serve como ponte entre o Diagrama de Contexto (macro) e o Diagrama de Componentes (interno de cada container).<br>

## Diagrama de Containers 📦

Esta seção apresenta o Diagrama de Containers do sistema "Dr. Tempo" (Aplicativo de Monitoramento Climático Interativo - AMCI), conforme o Modelo C4. Este diagrama detalha os principais blocos de execução (contêineres) que compõem o sistema, seus papéis individuais e como eles se comunicam entre si e com sistemas externos. Ele fornece uma visão arquitetural mais aprofundada, mostrando a estrutura interna do nosso software.

---

### 4.1. Diagrama de Containers (Visual) 🖼️

O diagrama abaixo ilustra graficamente os contêineres do sistema Dr. Tempo, suas interações e as conexões com sistemas externos.
![Dr tempo](https://github.com/user-attachments/assets/065358f1-8f11-4863-bb4d-f5a9a3320c4b)

---

### 4.2. Descrição Detalhada dos Contêineres

Aqui, descrevemos cada contêiner e sistema externo que compõe a arquitetura do Dr. Tempo.

#### **App Mobile**
* **O que ela é:** É a aplicação mobile principal do Dr. Tempo, um `Container` desenvolvido com **Thunkable** (para o MVP) ou **React Native**.
* **O que ela faz:** Atua como a interface do usuário para usuários finais (Jornalistas, usuários comuns). Permite a visualização da previsão do tempo, o gerenciamento da agenda pessoal, e o envio/recebimento de alertas em tempo real.

#### **Painel Web Admin**
* **O que ela é:** É uma aplicação web, um `Container` desenvolvido com **React.js**.
* **O que ela faz:** Serve como a interface administrativa para os Meteorologistas e Gestores de Segurança. Permite a inserção de boletins meteorológicos, o registro de ocorrências climáticas e a consulta de históricos de dados.

#### **Backend API**
* **O que ela é:** É uma API (Application Programming Interface), um `Container` desenvolvido com **Node.js e Express**.
* **O que ela faz:** Atua como o cérebro do sistema, recebendo e processando dados, executando a lógica de negócio central (incluindo a integração de IA para gerenciamento de agenda), e orquestrando a geração e o envio de alertas e notificações. É responsável também pela gestão de ocorrências e boletins.

#### **Banco de Dados**
* **O que ela é:** É um banco de dados, um `Database` utilizando **PostgreSQL**.
* **O que ela faz:** Armazena de forma persistente todos os dados essenciais do sistema, incluindo perfis de usuários, informações de agendas, configurações de alerta, dados de previsões, registros de ocorrências climáticas, boletins meteorológicos e históricos climáticos.

#### **APIs de Clima Externas**
* **O que ela é:** É um `Software System` externo, composto por APIs de terceiros (como OpenWeatherMap, AccuWeather).
* **O que ela faz:** Fornece ao sistema Dr. Tempo dados meteorológicos em tempo real, previsões estendidas e dados históricos de clima.

#### **Plataformas de Notificação**
* **O que ela é:** É um `Software System` externo, que representa plataformas de envio de e-mails, SMS e notificações push (como SendGrid, Twilio, Firebase Cloud Messaging).
* **O que ela faz:** Permite que o sistema Dr. Tempo envie mensagens automatizadas e alertas aos usuários através de diversos canais de comunicação.

#### **Órgãos de Emergência**
* **O que ela é:** É um `Software System` externo, que representa sistemas de autoridades e serviços de emergência (como Defesa Civil, Bombeiros).
* **O que ela faz:** Recebe alertas de desastre acionados pelo aplicativo Dr. Tempo e informações sobre ocorrências climáticas, permitindo uma resposta rápida a situações críticas.


