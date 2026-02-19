# Portfolio Project Ideas

Planning repository for a data science portfolio targeting ML engineering and ESG analytics roles. Contains research documents, project ideas, and detailed implementation plans.

## Portfolio Strategy

The portfolio aims for 3-5 projects spanning classical ML, data engineering, LLM/RAG systems, and deep learning — each framed around a real business problem, not a technology. Three top-level documents establish the guiding principles:

### [portfolio-advice-article.md](portfolio-advice-article.md)

Summary of hiring manager perspectives on what makes portfolios work. Key takeaways: lead with business impact (not tech stack), 3-5 quality projects beats 10 mediocre ones, READMEs under 500 words, quantified results, and never copy tutorials. Based on "The Data Portfolio That Actually Gets You Hired" by Sai Kumar Bysani.

### [portfolio-principles-reference.md](portfolio-principles-reference.md)

Seven research-backed principles synthesised from 20+ sources (2024-2026):

1. **Business Problem First** — every project starts from a question a company would pay to answer
2. **End-to-End Pipeline** — raw data through to deployed output, not notebooks
3. **Originality** — novel framing that can't be replicated by following a tutorial
4. **Substantive LLM/DL Work** — evaluation, failure analysis, and cost trade-offs, not just API calls
5. **Communication** — README (30s scan), blog post (5min read), demo (2min experience), STAR narrative
6. **Portfolio Composition** — breadth across skills/domains with strategic coherence
7. **Honest Limitations** — stated assumptions, documented failure modes, what production would do differently

Includes a quick-reference checklist used to audit every project plan.

### [modern-framework-project-ideas.md](modern-framework-project-ideas.md)

Four candidate project ideas to complement the two existing classical projects (Steam recommendation engine + CPG Private Label analysis):

| ID | Project | Framework | Status |
|----|---------|-----------|--------|
| L1 | EU Food Safety Regulatory Intelligence Engine | LangChain + RAG | Full plan complete |
| L2 | Earnings Call Intelligence Extractor | LangChain + extraction | Idea stage |
| P1 | Fine-Tune vs. Prompt Benchmark | PyTorch + HuggingFace | Initial plan complete |
| P2 | Custom ESG Embedding Model for Vertical Search | PyTorch + SentenceTransformers | Full plan complete |

L2 was superseded by B1 (MacroSurveillance). P2 was validated as the stronger PyTorch project over P1.

## Projects

### Active (full plans)

| Project | Directory | Business Question |
|---------|-----------|-------------------|
| **CPG Private Label Opportunity Engine** | [PrivateLabelOpportunities/](PrivateLabelOpportunities/) | Which food categories represent the highest-value private label opportunities for European retailers? |
| **EU Food Safety Regulatory Intelligence** (L1) | [projects/FoodSafetyIntelligence/](projects/FoodSafetyIntelligence/) | For a company launching product X in the EU, which food safety regulations apply and what are the compliance requirements? |
| **Corporate Earnings Macro Surveillance** (B1) | [projects/MacroSurveillance/](projects/MacroSurveillance/) | Can structured extraction from earnings call transcripts replicate central bank macroeconomic surveillance signals? |
| **Custom ESG Embedding Model** (P2) | [projects/CustomEmbeddingsSearch/](projects/CustomEmbeddingsSearch/) | Can a domain-specific sentence-transformer materially improve retrieval quality on ESG sustainability reports? |

### Parked

| Project | Directory | Notes |
|---------|-----------|-------|
| Fine-Tune vs. Prompt Benchmark (P1) | [projects/FineTuneVsPrompt/](projects/FineTuneVsPrompt/) | Has initial plan. P2 validated as stronger on 9/12 dimensions (lower saturation, novel artifact, direct RAG relevance). |

## Skill Coverage Matrix

| Dimension | Private Label | Food Safety (L1) | Macro Surveillance (B1) | ESG Embeddings (P2) |
|-----------|--------------|-------------------|--------------------------|----------------------|
| **Domain** | Retail/CPG | EU regulation | Finance/macro | ESG/sustainability |
| **Core technique** | Competitive analysis, scoring | RAG + structured extraction | NLP extraction + time series | Contrastive learning, IR evaluation |
| **Data sources** | Open Food Facts + scrapers | EUR-Lex corpus | Earnings transcripts (multi-API) | ESGBench + CDP + GRI + TCFD + synthetic |
| **Modern stack** | Classical | LangChain, vector stores | LLM extraction | PyTorch, SentenceTransformers, ONNX |
| **Key artifact** | Scoring dashboard | Compliance extraction API | Macro indicator pipeline | Published HuggingFace model |
| **Deployment** | Streamlit | Streamlit + FastAPI + Docker | Streamlit + FastAPI + Docker | Streamlit + FastAPI + Docker + HF Hub |
