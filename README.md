# 🧠 Meu Framework — Agentes de Validação de Ideias

> Pipeline completo de validação de ideias de negócio usando agentes de IA no Claude Code.
> Da ideia bruta ao plano de negócio institucional, sem sair do terminal.

---

## O que é isso?

Um framework de agentes especializados que guia você por todo o processo de validação de uma ideia de negócio antes de investir tempo e dinheiro em desenvolvimento.

Cada agente tem uma responsabilidade específica e passa o output para o próximo — formando um pipeline encadeado que vai da **clareza da ideia** até o **plano de negócio completo**.

---

## Pré-requisitos

- [Node.js](https://nodejs.org) v20+
- [Claude Code](https://claude.ai/code) instalado
- Conta na Anthropic com acesso ao Claude Code

---

## Instalação

```bash
# Clone o repositório
git clone https://github.com/matheuspereirafx/meu-framework.git

# Entre na pasta
cd meu-framework

# Abra o Claude Code
claude
```

---

## Fluxo Completo

```
/agente-ideia
    ↓ [chama automaticamente]
/pesquisa-mercado
    ↓ gera: ideia.md + pesquisa-mercado.md
/agente-estrategia
    ↓ gera: estrategia.md
/agente-financeiro
    ↓ gera: financeiro.md + financeiro.xlsx
/agente-mvp
    ↓ gera: mvp.md
/skill-plano-negocio
    ↓ gera: resumo-executivo.md + plano-negocio.md + plano-negocio.docx
```

---

## Agentes

### `/agente-ideia`
Ponto de entrada do pipeline. Transforma uma ideia bruta em problema raiz validado e solução idealizada.

**Modo 1 — Problema Raiz:**
- Captura do problema
- 5 Porquês até a causa raiz
- Job To Be Done → Job Statement
- Mapa de Dor → ponto de intervenção ideal
- Ishikawa (se multifatorial)
- Scorecard de viabilidade do problema

**Modo 2 — Idealização:**
- Entendimento da solução
- Foco radical (o que NÃO fazer)
- Não clientes em 3 níveis
- Dao — alinhamento de equipe (Sun Tzu)
- CHA — mapa de competências e lacunas
- Síntese + hipóteses por risco

**Output:** `output/ideia.md`

---

### `/pesquisa-mercado`
Chamada automaticamente pelo `/agente-ideia` na Fase 1A. Pesquisa na web e estrutura os dados de mercado.

**Cobre:**
- Concorrentes diretos e indiretos com preços reais
- Ticket médio do mercado (média dos concorrentes)
- Reviews negativos — gap analysis (top 3 gaps)
- TAM/SAM/SOM com ticket médio real como base de cálculo
- Persona detalhada: nome fictício, dores, comportamento digital, o que usa hoje, frase sobre o problema
- Tendências do setor

**Output:** `output/pesquisa-mercado.md`

---

### `/agente-estrategia`
Usa os outputs anteriores para construir o posicionamento completo. Só pergunta ao usuário o que a pesquisa não respondeu.

**Cobre:**
- Business Model Canvas (9 blocos com fonte de cada informação)
- Grade ERRC — Eliminar, Reduzir, Aumentar, Criar vs concorrentes
- TAM/SAM/SOM refinado com receita potencial calculada
- Modelo de receita com justificativa baseada no ticket médio do mercado
- Síntese estratégica consolidada

**Output:** `output/estrategia.md`

---

### `/agente-financeiro`
Coleta premissas uma a uma e calcula a viabilidade financeira completa.

**Coleta:**
- Ticket médio, CAC, churn mensal, custos fixos, investimento inicial, clientes mês 1, crescimento mensal

**Calcula:**
- Unit economics: LTV, LTV/CAC, payback do CAC, break-even em clientes
- Alerta automático se LTV/CAC < 3x
- Projeção 24 meses em 3 cenários: Pessimista (-40%) / Realista / Otimista (+40%)
- Análise de sensibilidade: churn +40%, CAC +40%, ticket -20%
- Parecer final: 🟢 Viável / 🟡 Condicional / 🔴 Inviável

**Output:** `output/financeiro.md` + `output/financeiro.xlsx`

---

### `/agente-mvp`
Define o menor caminho para validar as hipóteses mais arriscadas.

**Faz:**
- Pega hipóteses do `ideia.md` e confirma com o usuário
- Ranqueia por risco: 🔴 Alto / 🟡 Médio / 🟢 Baixo
- Decide por hipótese:
  - **Desejo/Conversão** → experimento sem código (entrevista, landing page, smoke test, concierge)
  - **Funcional/Retenção** → features mínimas necessárias + o que NÃO construir
- Define indicadores de aderência: ativação, retenção semana 1 e 4, conversão free→pago, NPS

**Output:** `output/mvp.md`

---

### `/skill-plano-negocio`
Consolida todos os outputs em documentos institucionais. Identifica gaps e faz perguntas antes de gerar.

**Gera:**
- `resumo-executivo.md` — síntese de 1 página para uso interno
- `plano-negocio.md` — documento completo com 10 seções
- `plano-negocio.docx` — versão Word para investidores/bancos

**Seções do documento completo:**
1. Sumário Executivo
2. O Problema
3. A Solução
4. Mercado
5. Persona
6. Modelo de Negócio
7. Financeiro
8. MVP e Validação
9. Equipe e Estrutura
10. Visão e Roadmap

---

## Estrutura de Pastas

```
meu-framework/
├── README.md
├── .claude/
│   └── skills/
│       ├── agente-ideia/
│       │   ├── SKILL.md
│       │   └── bmad-manifest.json
│       ├── pesquisa-mercado/
│       │   ├── SKILL.md
│       │   └── bmad-manifest.json
│       ├── agente-estrategia/
│       │   ├── SKILL.md
│       │   └── bmad-manifest.json
│       ├── agente-financeiro/
│       │   ├── SKILL.md
│       │   └── bmad-manifest.json
│       ├── agente-mvp/
│       │   ├── SKILL.md
│       │   └── bmad-manifest.json
│       └── skill-plano-negocio/
│           ├── SKILL.md
│           └── bmad-manifest.json
└── output/
    ├── ideia.md
    ├── pesquisa-mercado.md
    ├── estrategia.md
    ├── financeiro.md
    ├── financeiro.xlsx
    ├── mvp.md
    ├── resumo-executivo.md
    ├── plano-negocio.md
    └── plano-negocio.docx
```

---

## Output Final

Ao final do pipeline, a pasta `output/` contém:

| Arquivo | Conteúdo |
|---------|----------|
| `ideia.md` | Problema raiz + solução + hipóteses |
| `pesquisa-mercado.md` | Concorrentes + persona + TAM real |
| `estrategia.md` | Canvas + ERRC + modelo de receita |
| `financeiro.md` | Projeções + LTV/CAC + parecer |
| `financeiro.xlsx` | Planilha com 3 cenários |
| `mvp.md` | Experimentos + indicadores de aderência |
| `resumo-executivo.md` | Síntese de 1 página |
| `plano-negocio.md` | Documento institucional completo |
| `plano-negocio.docx` | Versão Word para investidores |

---

## Handoff para Desenvolvimento

Após validar a ideia, copie os outputs para o projeto de desenvolvimento:

```bash
cp -r output/ ../meu-projeto/docs/
cd ../meu-projeto
claude
# → /agente-prd (próxima fase)
```

---

## Frameworks Utilizados

| Framework | Agente | Finalidade |
|-----------|--------|-----------|
| 5 Porquês | agente-ideia | Causa raiz do problema |
| Job To Be Done | agente-ideia | Trabalho real do cliente |
| Mapa de Dor | agente-ideia | Ponto de intervenção ideal |
| Ishikawa | agente-ideia | Causas multifatoriais |
| Oceano Azul (ERRC) | agente-estrategia | Diferenciação competitiva |
| Business Model Canvas | agente-estrategia | Modelo de negócio |
| TAM/SAM/SOM | pesquisa + estrategia | Tamanho de mercado |
| Unit Economics | agente-financeiro | LTV, CAC, payback |
| Dao (Sun Tzu) | agente-ideia | Alinhamento de equipe |
| CHA | agente-ideia | Mapa de competências |

---

## Licença

MIT — use, modifique e distribua livremente.
