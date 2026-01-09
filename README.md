## 🤖 Chatbot Telegram com IA (n8n + Gemini)

Este repositório contém a estrutura e o fluxo de automação para um chatbot inteligente no Telegram, utilizando o **n8n** como orquestrador e o **Google Gemini** como "cérebro" para processamento de linguagem natural.

## 🚀 Sobre o Projeto
O objetivo deste projeto foi criar um assistente virtual capaz de responder mensagens em tempo real no Telegram. Este projeto foi desenvolvido inteiramente com fins de **aprendizado**, utilizando a versão gratuita do **n8n instalada localmente via Docker**. 

Devido à natureza da execução local, foi necessária a utilização da ferramenta **ngrok** para criar um túnel seguro (funil), permitindo que os webhooks do Telegram alcancem o ambiente local de forma estável. O diferencial desta implementação é o uso de ferramentas *no-code/low-code* e a conteinerização, permitindo uma automação robusta sem custos de hospedagem em nuvem.

## 🛠️ Tecnologias Utilizadas
- **n8n**: Plataforma de automação de fluxo de trabalho.
- **Google Gemini API**: Inteligência Artificial para geração de respostas.
- **Telegram Bot API**: Interface de comunicação com o usuário.
- **Docker**: Para rodar o ambiente n8n de forma isolada e segura.
- **ngrok**: Para criar um túnel seguro e permitir que o Telegram envie mensagens para o ambiente local.

## 🏗️ Estrutura do Fluxo (Workflow)
O fluxo no n8n é composto por três etapas principais:
1. **Telegram Trigger**: Escuta novas mensagens enviadas ao bot.
2. **AI Agent + Google Gemini Model**: Processa a intenção da mensagem e gera uma resposta inteligente.
3. **Telegram Send Message**: Devolve a resposta gerada pela IA para o chat do usuário.

## ⚙️ Como Executar
Para rodar este projeto localmente, siga estes passos:

1. **Subir o n8n via Docker:**
   ```powershell
   docker run -d --name n8n -p 5678:5678 -e N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=false -v ${HOME}/.n8n:/home/node/.n8n n8nio/n8n
   
2. **Criar o Túnel Webhook (CMD):**
Para que o Telegram consiga se comunicar com o seu servidor local, inicie o túnel do ngrok na porta 5678:

> ° Powershell: ngrok http 5678
>
> ° Copie o link https://seulink.ngrok-free.app gerado no terminal (substitua pelo seu link).

3. **Acessar o n8n:**
Abra seu navegador no endereço http://localhost:5678 para visualizar e editar o fluxo.

📌 Configurações de Credenciais Para que a automação funcione, é necessário configurar as seguintes chaves dentro da aba Credentials do n8n:

> ° **Google Gemini API:** Obtenha sua chave no Google AI Studio e cole no campo API Key.
>
> ° **Telegram API:** Utilize o token fornecido pelo BotFather ao criar o seu bot no Telegram.
>
> ° **Google Cloud OAuth2:** Caso deseje estender o projeto para salvar logs no Google Sheets, configure o Client ID e Client Secret no Google Cloud Console, lembrando de atualizar sempre a Redirect URI com o link atual do seu ngrok.

***Desenvolvido por [Tayaga Rayanne](https://github.com/TayagaRayanne) durante estudos de automação e IA.***
