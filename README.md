![Ideaflow](./banner.svg)
<div align="center">
  # 💡 Ideaflow — Business Validation Agents
  
  **A comprehensive business idea validation pipeline using AI agents within Claude Code. From raw concept to institutional business plan, all inside your terminal.**

  [![Claude AI](https://img.shields.io/badge/Claude_Code-7575FF?style=for-the-badge&logo=anthropic&logoColor=white)](https://anthropic.com/)
  [![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
  [![Business Strategy](https://img.shields.io/badge/Strategy-Lean_Startup-orange?style=for-the-badge)](https://en.wikipedia.org/wiki/Lean_startup)

  <p align="center">
    <a href="#-overview">Overview</a> •
    <a href="#-full-workflow">Workflow</a> •
    <a href="#-agents">Agents</a> •
    <a href="#-installation">Installation</a> •
    <a href="#-output">Output</a>
  </p>
</div>

---

## ✨ Overview

**Ideaflow** is a specialized agent framework that guides you through the entire validation process of a business idea before you spend time and money on development.

The framework consists of chained agents where the output of one serves as the context for the next — forming a streamlined pipeline that moves from **ideation clarity** to a **comprehensive business plan**.

---

## 🔄 Full Workflow

The agents are designed to trigger in a specific sequence:

```text
/agente-ideia (Concept & Problem Root)
        ↓ [Auto-triggers]
/pesquisa-mercado (Market Research & Competitors)
        ↓ Generates: ideia.md + pesquisa-mercado.md
/agente-estrategia (Business Model & Positioning)
        ↓ Generates: estrategia.md
/agente-financeiro (Unit Economics & Projections)
        ↓ Generates: financeiro.md + financeiro.xlsx
/agente-mvp (Validation Strategy & Experiments)
        ↓ Generates: mvp.md
/skill-plano-negocio (Institutional Consolidation)
        ↓ Generates: executive-summary.md + business-plan.docx
```

---

## 🤖 Agents

### 🧠 `/agente-ideia` (The Concept)
The entry point of the pipeline. It transforms a raw idea into a validated root problem and an idealized solution.
* **Root Cause Analysis:** 5 Whys, Ishikawa (Fishbone) diagrams, and Job To Be Done (JTBD).
* **Pain Mapping:** Identifying the ideal intervention point.
* **Team Alignment:** Dao (Sun Tzu) principles and KSA (Knowledge, Skills, Abilities) gap mapping.

### 🔍 `/pesquisa-mercado` (Market Research)
Automatically triggered by the Idea Agent. It performs web research to structure market data.
* **Competitor Analysis:** Direct/Indirect competitors with real pricing and gap analysis.
* **Market Sizing:** TAM/SAM/SOM based on real market average ticket prices.
* **Persona:** Detailed profiles including digital behavior and current alternative solutions.

### 📈 `/agente-estrategia` (Strategy)
Builds the full positioning based on previous research.
* **Business Model Canvas:** 9 blocks with sourced information.
* **Blue Ocean (ERRC):** Eliminate, Reduce, Raise, and Create grid vs. competitors.
* **Revenue Model:** Justified pricing based on market benchmarks.

### 💰 `/agente-financeiro` (Financials)
* **Unit Economics:** LTV, CAC, Payback, and Churn analysis.

### 🧪 `/agente-mvp` (Validation)
Defines the shortest path to validate high-risk hypotheses.
* **Risk Ranking:** Identifies 🔴 High / 🟡 Medium / 🟢 Low risk hypotheses.
* **Experiment Design:** Smoke tests, Concierge MVPs, Landing Pages, or Feature-light builds.
* **KPIs:** Retention, Conversion (Free to Paid), and NPS goals.

### 📄 `/skill-plano-negocio` (Business Plan)
Consolidates all outputs into institutional-grade documents (Markdown and Word).

---

## 📦 Installation & Setup

### Prerequisites
* **Node.js** v20+
* **Claude Code** installed and authenticated.

### Setup
```bash
# 1. Clone the repository
git clone [https://github.com/matheuspereirafx/ideaflow.git](https://github.com/matheuspereirafx/ideaflow.git)

# 2. Enter the directory
cd ideaflow

# 3. Open Claude Code
claude
```

---

## 🏗️ Handoff to Development

Once the idea is validated, you can seamlessly transition to the development phase using **Ideaflow Dev**:

```bash
# Copy outputs to your dev project
cp -r output/ ../my-rails-app/docs/
cd ../my-rails-app

# Start the dev pipeline
claude
> /workflow-spec-completa
```

---

## 🤝 License

MIT — feel free to use, modify, and distribute.

---

<div align="center">
  <p>Envisioned and developed by <a href="https://github.com/matheuspereirafx">Matheus Pereira</a></p>
  
  <p>
    <a href="https://github.com/matheuspereirafx">
      <img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
    </a>
  </p>
</div>
