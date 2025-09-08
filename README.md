# 🔐 N8N Table App

Este projeto implementa um fluxo completo de **geração, descriptografia e consumo de dados** integrado ao **N8N**.

## 📋 Visão Geral

O sistema é composto por três repositórios principais:

- [**fake-api-service**](https://github.com/pedroita/fake-api-service) - Gera dados **criptografados**
- [**fake-api-project**](https://github.com/pedroita/fake-api-project) - API em Node.js + Express que faz a **descriptografia** e envia para o N8N
- [**n8n-table-app**](https://github.com/pedroita/n8n-table-app/tree/master) - Frontend em React (Vite) para consumir e visualizar os dados

## 🔧 Componentes da Infraestrutura
- AWS EC2 → Hospeda os serviços backend (fake-api-service e fake-api-project)

- PM2 → Gerencia os processos Node.js na EC2

- Nginx → Proxy reverso que organiza as rotas (chemall.com.br/api/...)

- Certbot (Let's Encrypt) → Configuração HTTPS com certificados SSL

- Vercel → Hospedagem do frontend React (n8n-table-app)

- N8N Cloud → Orquestra os workflows (listapersons, deletetabela, etc.)

## 🔄 Fluxo de Dados

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

https://n8n-table-app.vercel.app/