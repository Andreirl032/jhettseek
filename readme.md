
---

# 🚀 JhettSeek — Flight Stock Market

**JhettSeek** é uma plataforma de inteligência de dados que trata passagens aéreas como ativos do mercado financeiro. Utilizando Machine Learning e análise de séries temporais, o sistema transforma a volatilidade dos preços em gráficos preditivos, ajudando o usuário a decidir se deve "comprar" (buy) ou "esperar" (hold) uma passagem.

O objetivo central é responder: **"Este é o melhor preço possível para este voo ou a tendência é de queda?"**

---

## ✈️ O Conceito

Diferente de buscadores tradicionais que apenas mostram o preço atual, o JhettSeek foca na **estratégia de compra**.

* **Voo como Ativo:** Cada rota (ex: GRU → JFK) é monitorada como uma ação da bolsa.
* **Pressão de Demanda:** O sistema infere o esgotamento de assentos através de modelos de aceleração de preço e volatilidade.
* **Previsão Probabilística:** Não prevemos o preço exato, mas sim a tendência e a janela de oportunidade ideal.

---

## 🛠️ Tech Stack

### Frontend

* **Framework:** Next.js 14 (App Router) + TypeScript.
* **Styling:** Tailwind CSS + Shadcn/UI.
* **Gráficos:** Recharts / Lightweight Charts (estilo TradingView).
* **Validação:** Zod.

### Backend (Microserviço de Inteligência)

* **API:** FastAPI (Python).
* **ORM:** SQLModel / SQLAlchemy.
* **Database:** PostgreSQL.
* **Arquitetura:** Controller-Service-Repository.

### Machine Learning & Data

* **Modelos:** XGBoost / LightGBM (Regressão para séries temporais).
* **Processamento:** Pandas & Scikit-learn.
* **Coleta:** Web Scraping (Playwright) & APIs (SerpApi / Tequila).

---

## 🏛️ Arquitetura do Sistema

O projeto segue um padrão de **Monolito Modular** no backend para garantir escalabilidade e fácil manutenção:

* **Controllers:** Gerenciam as rotas da API e validação de entrada (Pydantic).
* **Services:** Contêm a lógica de negócio, orquestram as chamadas de ML e processam regras de "Buy/Hold".
* **Repositories:** Abstraem o acesso ao PostgreSQL.
* **ML Engine:** Camada isolada para treinamento e inferência de modelos.

---

## 📋 Funcionalidades (MVP)

* [x] **Dashboard Analítico:** Visualização de preços em formato de gráfico financeiro (Candlesticks/Linhas).
* [x] **Indicador Buy/Hold:** Algoritmo que sugere a melhor ação baseada na tendência prevista.
* [x] **Busca Flexível:** Sugestão de intervalos de datas para maximizar a economia.
* [x] **Histórico de Volatilidade:** Monitoramento de como o preço se comportou nas últimas semanas.
* [ ] **Conversor de Milhas (Roadmap):** Comparação em tempo real entre custo em Reais vs. Pontos.
* [ ] **Price Freeze (Fintech):** Opção de travar o preço mediante uma taxa de reserva.

---

## 📂 Estrutura do Projeto

```text
jhettseek/
├── frontend/                # Next.js Application
│   ├── src/
│   │   ├── app/             # App Router (Pages & Layouts)
│   │   ├── components/      # UI Components (Charts, Forms)
│   │   └── services/        # API Integration
├── backend/                 # FastAPI Application
│   ├── app/
│   │   ├── api/             # Controllers (Routes)
│   │   ├── services/        # Business Logic
│   │   ├── repositories/    # Database Access
│   │   ├── ml/              # Machine Learning Models & Training
│   │   └── db/              # Migrations & Connection
└── scripts/                 # Scrapers e tarefas agendadas (Cron)

```

---

## 🚀 Como Executar

### Pré-requisitos

* Node.js (v18+)
* Python (3.10+)
* PostgreSQL

### 1. Backend

```bash
cd backend
python -m venv venv
source venv/bin/activate  # venv\Scripts\activate no Windows
pip install -r requirements.txt
uvicorn app.main:app --reload

```

### 2. Frontend

```bash
cd frontend
npm install
npm run dev

```

---

## 📈 Roadmap de Evolução

1. **Fase 1 (MVP):** Coleta de dados de 50 rotas principais e modelo de regressão baseline.
2. **Fase 2:** Implementação de alertas via Telegram/WhatsApp para "Sinais de Compra".
3. **Fase 3:** Integração de APIs de GDS (Amadeus/Skyscanner) para escala global.
4. **Fase 4:** Inteligência de Milhas e Arbitragem de passagens.

---

## ⚖️ Licença

Distribuído sob a licença MIT. Veja `LICENSE` para mais informações.

---

**Desenvolvido por [Seu Nome/GitHub]** ✈️📈
"Data is the new fuel, and timing is everything."