# 🚀 Sistema de Avaliação Automática de Reembolso — Backend e Frontend

Este projeto é composto por **dois módulos principais** que, juntos, formam a solução completa de **automação inteligente de reembolsos** desenvolvida no curso **FIAP DevLeadership**.  
A aplicação foi desenhada sob uma **arquitetura de microsserviços**, com foco em **IA, integração e escalabilidade**.

---

## 🔗 Links do Projeto

| Módulo | Repositório / Acesso |
| :--- | :--- |
| **Backend (API e Processamento)** | [jucelioalencar/FIAP_DevLeadership_Projeto_Reembolso_Backend](https://github.com/jucelioalencar/FIAP_DevLeadership_Projeto_Reembolso_Backend) |
| **Frontend (Portal Web)** | [jucelioalencar/FIAP_DevLeadership_Projeto_Reembolso_Frontend](https://github.com/jucelioalencar/FIAP_DevLeadership_Projeto_Reembolso_Frontend) |
| **Aplicação Online** | [https://fiap.jucelio.work/](https://fiap.jucelio.work/) |

---

## 🧠 Arquitetura Geral (Microsserviços)

A solução é baseada em **microsserviços independentes**, desenvolvidos em **.NET 8 (C#)** e hospedados em **Azure**, com comunicação assíncrona via **Azure Service Bus** e integração com **Azure AI Vision** para leitura automática de comprovantes.

### 🧩 Componentes Principais

- **Frontend (Web App em Angular/HTML/CSS)**  
  Interface de solicitação e acompanhamento de reembolsos pelos colaboradores.  
  Comunicação direta com o API Gateway do backend.  

- **Backend (APIs e Microsserviços em .NET 8)**  
  Responsável por todo o fluxo de automação, análise, aprovação e notificações.  
  Implementa padrões modernos como **DDD, CQRS e Event Sourcing**.  

- **API Gateway (YARP)**  
  Centraliza o acesso a todos os microsserviços e gerencia autenticação e roteamento.  

- **Serviços Assíncronos**
  - **Ingestão:** Recebe solicitações e armazena dados no Azure SQL.  
  - **OCR / IA:** Extrai texto de imagens usando **Azure AI Vision**.  
  - **Validação:** Checa integridade e regras de negócio.  
  - **Análise:** Aplica lógica de decisão automatizada.  
  - **Notificação:** Informa resultados via e-mail e API de integração.  

- **Infraestrutura de Dados**
  - **Azure SQL Database** para persistência.  
  - **Azure Blob Storage** para arquivos e comprovantes.  

---

## 🗺️ Diagrama de Arquitetura

O diagrama abaixo ilustra a comunicação entre os módulos Frontend, Backend e os serviços Azure:

![Diagrama de Arquitetura do Sistema de Reembolso](https://private-us-east-1.manuscdn.com/sessionFile/tUB6Z4VfJkZShiHilpfQji/sandbox/Bo1inOidTzh83gsb26FFky-images_1761432434420_na1fn_L2hvbWUvdWJ1bnR1L2FyY2hpdGVjdHVyZV9kaWFncmFt.png)

---

## 🛠️ Tecnologias-Chave

| Categoria | Tecnologia |
| :--- | :--- |
| **Linguagens / Frameworks** | .NET 8 (C#), Angular |
| **Arquitetura** | Microsserviços, Azure Functions, DDD, CQRS |
| **IA / OCR** | Azure AI Vision |
| **Comunicação** | Azure Service Bus |
| **Banco de Dados** | Azure SQL Database |
| **Armazenamento** | Azure Blob Storage |
| **Infraestrutura** | Docker, Docker Swarm, GitHub Actions, Cloudflare Tunnels |

---

## ⚙️ Pipeline CI/CD — Docker Compose + GitHub Actions

O sistema utiliza **GitHub Actions** com **Docker Compose** para construir, versionar e publicar automaticamente os containers do **Frontend** e **Backend** no **Docker Hub**, seguidos por **deploy automatizado em produção** via SSH no Swarm.

### Exemplo Simplificado do Pipeline

```yaml
name: Docker Image CI

on:
  push:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: docker/setup-buildx-action@v3
      - uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      - name: Build and Push Docker Compose services
        run: |
          docker compose -f docker-compose.yml build
          docker compose -f docker-compose.yml push

  deploy:
    runs-on: ubuntu-latest
    needs: [build]
    if: github.ref == 'refs/heads/main'
    steps:
      - uses: actions/checkout@v4
      - uses: docker/setup-buildx-action@v3
      - name: Deploy to Production Server
        env:
          SSH_PRIVATE_KEY: ${{ secrets.SSH_PRIVATE_KEY }}
          DEPLOY_SERVER: ${{ secrets.DEPLOY_SERVER }}
        run: |
          echo "$SSH_PRIVATE_KEY" > private_key.pem
          chmod 600 private_key.pem
          scp -i private_key.pem docker-compose.yml root@$DEPLOY_SERVER:/opt/reembolso/
          ssh -i private_key.pem root@$DEPLOY_SERVER << 'EOF'
            cd /opt/reembolso
            docker compose pull
            docker compose up -d
            docker image prune -f
          EOF
