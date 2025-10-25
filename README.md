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

- **Frontend (Web App em React)**  
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

<p align="center">
  <img src="https://s6.imgcdn.dev/Yy0zpH.png" alt="Diagrama de Arquitetura do Sistema de Reembolso" width="800">
</p>

---

## 🛠️ Tecnologias-Chave

| Categoria | Tecnologia |
| :--- | :--- |
| **Linguagens / Frameworks** | .NET 8 (C#), React |
| **Arquitetura** | Microsserviços, Azure Functions, DDD, CQRS |
| **IA / OCR** | Azure AI Vision |
| **Comunicação** | Azure Service Bus |
| **Banco de Dados** | Azure SQL Database |
| **Armazenamento** | Azure Blob Storage |
| **Infraestrutura** | Docker, Docker Swarm, GitHub Actions, Cloudflare Tunnels |
