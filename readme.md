# 🚀 JhettSeek — O "Terminal Financeiro" das Viagens

**JhettSeek** é uma plataforma preditiva de dados em formato de SaaS que trata passagens aéreas como ativos financeiros. Focada em otimizar a decisão de compra, a plataforma une Machine Learning, análise de séries temporais e visualização de dados avançada para responder não apenas *se* o usuário deve comprar agora, mas *qual a melhor época do ano* e *quais as melhores datas* para sua viagem.

## 🎯 O Problema e a Solução

A busca tradicional por voos é baseada no preço de hoje. O JhettSeek analisa a **volatilidade e a sazonalidade**.

* **A Visão Macro (O Ano):** Através de *Heatmaps* (Mapas de Calor), o usuário visualiza rapidamente quais meses e semanas oferecem as melhores janelas de preço para uma viagem de *X* dias.
* **A Visão Micro (A Semana/Hora):** Através de gráficos financeiros (*Candlesticks*), o sistema exibe o histórico recente de preços e sinaliza a tendência de curto prazo com recomendações claras de **COMPRA (Buy)** ou **ESPERA (Hold)**.

---

## 🛠️ Tech Stack & Ferramentas

O projeto utiliza uma arquitetura **Monolítica Modular** no backend (padrão *Controller-Service-Repository*) e um frontend altamente reativo, focado na experiência de usuário (UX).

### 🖥️ Frontend (Interface Analítica)

* **Framework:** Next.js 14 (App Router) + TypeScript.
* **Estilização:** Tailwind CSS + Componentes Shadcn/UI.
* **Gráficos (DataViz):** Recharts e Lightweight Charts (TradingView) para os Candlesticks; Nivo ou visx para os Heatmaps anuais.
* **Validação de Dados:** Zod.

### ⚙️ Backend (O Motor de Regras e API)

* **Framework:** FastAPI (Python) para alta performance e suporte nativo a operações assíncronas.
* **Banco de Dados:** PostgreSQL.
* **ORM:** SQLAlchemy + Alembic (para migrações).
* **Autenticação:** JWT (JSON Web Tokens).

### 🧠 Inteligência Artificial & Dados

* **Modelo de Machine Learning:** XGBoost / LightGBM (Regressão para Séries Temporais).
* **Treinamento Base (Sazonalidade):** Datasets públicos de aviação (ex: Kaggle) para entender a "geometria" da variação de preços.
* **Coleta de Dados em Tempo Real:** Integração com APIs especializadas (SerpApi / ScrapingDog) contornando bloqueios de scraping tradicional.

### 💳 Infraestrutura e SaaS

* **Pagamentos/Assinaturas:** Stripe (Foco Global) e Mercado Pago (Foco Brasil/PIX).
* **Alertas e Mensageria:** Resend ou SendGrid para envio assíncrono de "Sinais de Compra" via e-mail.

---

## 📋 Funcionalidades Principais (MVP)

* **Busca Macro a Micro:** Pesquisa de rotas com sugestão inteligente de melhores épocas para viajar baseado na duração da viagem.
* **Dashboard de Ativos (Página da Rota):** Exibição do gráfico financeiro do voo, probabilidade de aumento de preço (medidor de risco) e listagem dos voos reais disponíveis para compra.
* **Watchlist & Alertas (Feedback Loop):** O usuário adiciona uma rota à sua carteira. O sistema roda rotinas diárias (CRON) e dispara um e-mail automaticamente quando o preço atinge a zona ideal de compra.
* **Sistema de Contas:** Perfis de usuário com gerenciamento de rotas monitoradas e controle de assinatura (SaaS).

---

## 📂 Estrutura de Diretórios (Monorepo)

```text
jhettseek/
├── frontend/                  # App Next.js
│   ├── src/
│   │   ├── app/               # Rotas (ex: /search, /route/[id], /profile)
│   │   ├── components/        # UI (Gráficos, Heatmaps, Botões)
│   │   └── lib/               # Validações (Zod) e utilitários
│
└── backend/                   # API FastAPI
    ├── app/
    │   ├── api/               # Controllers (Rotas HTTP: /flights, /users, /alerts)
    │   ├── services/          # Regras de Negócio (Orquestração de Busca e ML)
    │   ├── repositories/      # SQLAlchemy (Acesso ao PostgreSQL)
    │   ├── models/            # Schemas Pydantic e Modelos do Banco
    │   └── ml/                # Pipeline de Treinamento e Inferência (XGBoost)
    ├── worker/                # CRON Jobs para atualizar preços e disparar e-mails
    └── requirements.txt

```

**Desenvolvido com visão de engenharia e foco em dados.** ✈️📈