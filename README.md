# 🚀 Sistema de Avaliação Automática de Reembolso - Backend

Este projeto é o **Backend** da solução de reembolso, desenvolvido como parte do curso **FIAP DevLeadership**. Seu foco é a **automação completa** do processo de avaliação de solicitações via **microsserviços** e **Inteligência Artificial**.

## 🔗 Links do Projeto

| Recurso | Link |
| :--- | :--- |
| **Repositório Backend** | [jucelioalencar/FIAP_DevLeadership_Projeto_Reembolso_Backend](https://github.com/jucelioalencar/FIAP_DevLeadership_Projeto_Reembolso_Backend) |
| **Repositório Frontend** | [jucelioalencar/FIAP_DevLeadership_Projeto_Reembolso_Frontend](https://github.com/jucelioalencar/FIAP_DevLeadership_Projeto_Reembolso_Frontend) |
| **Acesso à Aplicação** | [https://fiap.jucelio.work/](https://fiap.jucelio.work/) |

## 💡 Resumo da Arquitetura (Microsserviços)

A solução é baseada em uma arquitetura de **microsserviços** em **.NET 8 (C#)**, utilizando o **Azure** como plataforma. Os serviços são desacoplados e comunicam-se de forma assíncrona via **Azure Service Bus**.

*   **API Gateway (YARP)**: Ponto de entrada unificado.
*   **Processamento Assíncrono**: Serviços de Ingestão, OCR (**Azure AI Vision**), Validação (APIs externas), Análise (Regras de Negócio) e Notificação.
*   **Dados**: **Azure SQL Database** e **Azure Blob Storage**.
*   **Padrões Aplicados**: Demonstração de DDD, CQRS e Event Sourcing.

## 🗺️ Diagrama de Arquitetura

O diagrama abaixo ilustra o fluxo de dependências e a comunicação entre os componentes do sistema.

![Diagrama de Arquitetura do Sistema de Reembolso](https://private-us-east-1.manuscdn.com/sessionFile/tUB6Z4VfJkZShiHilpfQji/sandbox/Bo1inOidTzh83gsb26FFky-images_1761432434420_na1fn_L2hvbWUvdWJ1bnR1L2FyY2hpdGVjdHVyZV9kaWFncmFt.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvdFVCNlo0VmZKa1pTaGlIaWxwZlFqaS9zYW5kYm94L0JvMWluT2lkVHpoODNnc2IyNkZGa3ktaW1hZ2VzXzE3NjE0MzI0MzQ0MjBfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwyRnlZMmhwZEdWamRIVnlaVjlrYVdGbmNtRnQucG5nIiwiQ29uZGl0aW9uIjp7IkRhdGVMZXNzVGhhbiI6eyJBV1M6RXBvY2hUaW1lIjoxNzk4NzYxNjAwfX19XX0_&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=b~~dWf5~NOZeaxMszLBHFuTUcP~BH5P5LmDa8QFs25rFWW6FpIeSHiJMIuIy0gSFR~2sY9sRA1mhhTxLOa904t4W4K1Sr~LBcKCpbK8Tojb1Wwx-hJEp~ZlSlTkLgEo2tuboFpWUkDIwsQJgva-56BtzUxTvyUWRy6aC6GZ62BL92j6x3BGNSRQn4jnQqRFScIkpSUmElPs5Lo8TPjitG~IyeEQqYlvRog3wnJV-6S93DI5n7jAkVHyRfFb9kyeEuu04YTUT550QHOSfctACFG4sv2O6-xiyby3Z61PNmKmU3aMh1EY8mUjJsin-02-NmIVylX0sHHyN~pkEIlcw0A__)

## 🛠️ Tecnologias Chave

| Categoria | Tecnologia |
| :--- | :--- |
| **Linguagem/Framework** | **.NET 8** e **C#** |
| **Arquitetura** | Microsserviços, Azure Functions |
| **IA/Processamento** | Azure AI Vision (OCR) |
| **Comunicação** | Azure Service Bus (Mensageria) |
| **Dados** | Azure SQL Database, Azure Blob Storage |




