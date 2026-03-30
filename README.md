# Portfólio & Automação de CI/CD 🚀

Este repositório contém o código-fonte do meu portfólio profissional, mas seu principal objetivo é servir como um **Case Prático de DevOps e Infraestrutura Web**.

Acesse o site em produção: **[INSERIR SEU IP DA AWS OU DOMÍNIO AQUI]**

## 🎯 Objetivo do Projeto
Demonstrar na prática o gerenciamento do ciclo de vida de uma aplicação, desde o versionamento do código até a sua entrega contínua em um ambiente de produção na nuvem, aplicando conceitos de segurança e metodologias de automação ágil.

## 🏗️ Arquitetura da Solução
* **Cloud Provider:** Amazon Web Services (AWS)
* **Servidor:** Instância EC2 rodando Amazon Linux 2023
* **Web Server:** Nginx
* **Versionamento:** Git / GitHub
* **CI/CD:** GitHub Actions

## ⚙️ Como a Esteira (Pipeline) Funciona
1. O desenvolvimento é feito no ambiente local.
2. Ao realizar um `git push` para a branch `main`, o **GitHub Actions** é acionado automaticamente.
3. A pipeline realiza o *checkout* do código atualizado.
4. Utilizando o protocolo SSH via `appleboy/scp-action`, o GitHub conecta-se à instância EC2 e sincroniza os arquivos diretamente na pasta `/usr/share/nginx/html`.

## 🔒 Práticas de Segurança Implementadas
Para garantir a segurança do servidor e seguir o **Princípio do Menor Privilégio**:
* O deploy automátizado **não** utiliza o usuário root ou o usuário padrão.
* Foi provisionado um usuário específico chamado `deployer`.
* A autenticação da esteira de CI/CD é feita exclusivamente via chave assimétrica (SSH RSA), armazenada de forma segura nas *Secrets* do GitHub.
* O usuário `deployer` possui permissão de escrita apenas no diretório de destino do Nginx, protegendo o restante do sistema operacional.

---
*Desenvolvido por Fernando Gadelha - Analista de Sistemas / DevOps*