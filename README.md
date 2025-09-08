# 🔐 N8N Table App

Este projeto implementa um fluxo completo de **geração, descriptografia e consumo de dados** integrado ao **N8N**.

## 📋 Visão Geral

O sistema é composto por três repositórios principais:

- [**fake-api-service**](https://github.com/pedroita/fake-api-service) - Gera dados **criptografados**
- [**fake-api-project**](https://github.com/pedroita/fake-api-project) - API em Node.js + Express que faz a **descriptografia** e envia para o N8N
- [**n8n-table-app**](https://github.com/pedroita/n8n-table-app/tree/master) - Frontend em React (Vite) para consumir e visualizar os dados

## 🗄️ Banco de Dados
O sistema utiliza PostgreSQL como banco de dados principal para armazenamento das informações processadas.

## 🔧 Componentes da Infraestrutura
- AWS EC2 → Hospeda os serviços backend (fake-api-service e fake-api-project)

- PM2 → Gerencia os processos Node.js na EC2

- Nginx → Proxy reverso que organiza as rotas (chemall.com.br/api/...)

- Certbot (Let's Encrypt) → Configuração HTTPS com certificados SSL

- Vercel → Hospedagem do frontend React (n8n-table-app)

- N8N Cloud → Orquestra os workflows (listapersons, deletetabela)
- PostgreSQL → Banco de dados para armazenamento das informações

# 🚀 Performance

### Latest Performance Report for:
https://n8n-table-app.vercel.app/

**Report generated:**  
Mon, Sep 8, 2025 7:30 AM -0700  
Test Server Location: Vancouver, Canada  
Using: Chrome 125.0.0.0, Lighthouse 12.3.0  

---

### GTmetrix Grade

| Metric | Score | Value |
|---|---|---|
| **Performance** | 99% | A |
| **Structure** | 94% | A |
| **Largest Contentful Paint** | - | 821ms |
| **Total Blocking Time** | - | 0ms |
| **Cumulative Layout Shift** | - | 0 |

## 🏗️ Arquitetura do Sistema

<img width="4332" height="261" alt="deepseek_mermaid_20250908_231d27" src="https://github.com/user-attachments/assets/14629087-e1c1-4aad-8fea-e5e5a1d5e2b3" />


## 🔄 Fluxo de Dados

<img width="5340" height="2709" alt="deepseek_mermaid_20250908_a1d29d" src="https://github.com/user-attachments/assets/0a460ea2-e4ba-4b58-9c3d-5d6688dfc293" />


## 📂 Estrutura dos Repositórios
📦 fake-api-service
API Node.js responsável por gerar dados criptografados. Simula uma fonte de dados segura.

## 📦 fake-api-project
API Node.js responsável por:

- Buscar dados criptografados do fake-api-service

- Descriptografar os dados

- Enviar para o N8N

# Endpoints principais:

- GET /api/fetch-and-decrypt → Busca, descriptografa e envia para o N8N

## 📦 n8n-table-app
Frontend em React (Vite + Axios + MUI) que:

- Consome a API (/api/fetch-and-decrypt)

- Interage com os webhooks do N8N (listapersons, deletetabela)

- Deploy automatizado na Vercel

# 🌐 Configuração de Domínio e SSL
- Domínio principal: chemall.com.br

- Certificado SSL configurado via Certbot (Let's Encrypt)

- Nginx como proxy reverso para roteamento das APIs

🚀 Demonstração

![Vídeo do WhatsApp de 2025-09-08 à(s) 11 01 17_8f08f8a7 mp4](https://github.com/user-attachments/assets/41da1584-475d-4b0e-a1e7-ff88868fd2f1)

https://n8n-table-app.vercel.app/
