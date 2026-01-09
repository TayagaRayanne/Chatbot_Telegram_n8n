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
O fluxo no n8n é composto por quatro etapas principais:
| Nó | Função |
| :--- | :--- |
| 🔴 **Trigger** | Escuta novas mensagens enviadas ao bot. |
| 🟣 **Agent** | Orquestra a lógica da conversa. |
| 🔵 **Gemini** | O "cérebro" que gera o conteúdo. |
| 🟢 **Send Msg**| Entrega a resposta ao usuário. |

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

## 📸 Imagens do sistema (Workflow)

<img width="1920" height="927" alt="Captura de tela 2026-01-08 222706" src="https://github.com/user-attachments/assets/c93a9279-cf04-40d3-937f-2c21a015d1f0" />

<img width="1920" height="917" alt="Captura de tela 2026-01-08 222112" src="https://github.com/user-attachments/assets/0ad7f95a-1fe0-46ba-b87e-f91646f9166f" />

<img width="1919" height="924" alt="Captura de tela 2026-01-08 222150" src="https://github.com/user-attachments/assets/80aa9626-04d0-4935-be98-9d574fff905f" />

<img width="1917" height="925" alt="Captura de tela 2026-01-08 222307" src="https://github.com/user-attachments/assets/b990ac3b-01cf-44a4-94c6-1e9344bfbc70" />

<img width="795" height="453" alt="ab18674c-5f79-4354-925e-b1fe0c982667" src="https://github.com/user-attachments/assets/9faa43e3-bfd3-4530-8968-8a218d690525" />

<img width="1920" height="922" alt="Captura de tela 2026-01-09 144547" src="https://github.com/user-attachments/assets/d14df289-20b8-4bdb-af27-83387d6139a7" />

![nova](https://github.com/user-attachments/assets/734d5225-1514-4a5e-b0bb-37ae90e545c6)


***Desenvolvido por [Tayaga Rayanne](https://github.com/TayagaRayanne) durante estudos de automação e IA.***
