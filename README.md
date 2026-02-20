# Portfolio Project Ideas

Planning repository for a data science portfolio targeting ML engineering and ESG analytics roles. Contains research documents, project ideas, and detailed implementation plans.

## Portfolio Strategy

The portfolio aims for 3-5 projects spanning classical ML, data engineering, LLM/RAG systems, and deep learning — each framed around a real business problem, not a technology. Two top-level documents establish the guiding principles:

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

## Projects

| Project | Repo | Domain | Stack | Status |
|---------|------|--------|-------|--------|
| Steam Game Market Intelligence Engine | [SteamMarketGapAnalysis](https://github.com/DrPrettyman/SteamMarketGapAnalysis) | Gaming | Classical ML (implicit, scikit-learn) | Implemented |
| CPG Private Label Opportunity Engine | [PrivateLabelOpportunities](https://github.com/DrPrettyman/PrivateLabelOpportunities) | Retail/CPG | Classical ML (scikit-learn, DuckDB) | Implemented |
| EU Food Safety Regulatory Intelligence | [FoodSafetyIntelligence](https://github.com/DrPrettyman/FoodSafetyIntelligence) | EU regulation | LangChain, vector stores | Planned |
| Corporate Earnings Macro Surveillance | [MacroSurveillance](https://github.com/DrPrettyman/MacroSurveillance) | Finance/macro | LLM extraction | Planned |
| Custom ESG Embedding Model | [CustomEmbeddingsSearch](https://github.com/DrPrettyman/CustomEmbeddingsSearch) | ESG/sustainability | PyTorch, SentenceTransformers, ONNX | Planned |
| Fine-Tune vs. Prompt Benchmark | [FineTuneVsPrompt](https://github.com/DrPrettyman/FineTuneVsPrompt) | ML engineering | PyTorch, HuggingFace | Parked |

### Steam Game Market Intelligence Engine

A multi-source data pipeline and recommendation system that identifies underserved game market niches with quantified revenue estimates. Collected player behaviour data from Steam Web API (10,000 users via friend-graph BFS crawling), market data from SteamSpy (50,005 games), and metadata from RAWG API (9,951 matches). Built a hybrid recommendation engine (ALS collaborative filtering + content-based fallback) that surfaces high-value games 3x more effectively than a popularity baseline (revenue-weighted HR@20: 14.8% vs 4.8%). Scored 140,136 tag-pair niches on demand, engagement, satisfaction, and supply — top opportunities include "Multiplayer + Open World" ($200K–$21M new-entrant revenue) and "Adventure + Open World" (2.9x recency trend). Modelled price sensitivity across 27 genres with log-linear regression.

**Tech:** Python, pandas, numpy, scikit-learn, implicit, matplotlib, seaborn, plotly | Steam Web API, SteamSpy API, RAWG API

### CPG Private Label Opportunity Engine

A data-driven framework that identifies food categories where European retailers can launch health-positioned private label products into underserved nutritional gaps. Analysed 2.57M food products from Open Food Facts across 27 EU markets, enriched with pricing scraped from Mercadona (Spain) and Albert Heijn (Netherlands). Computed Nutri-Score for 706K products missing official scores, increasing coverage from 32% to 59%. Found that 73% of products score C or worse while healthy private label penetration is only ~10%. Ranked categories by a 6-component composite opportunity score with Monte Carlo sensitivity analysis — top opportunities: Snacks (119K products, 88% unhealthy), Condiments & Sauces (77% gap), and Breakfast (93% gap). Trained an interpretable gradient boosted classifier (CV AUC 0.65) and brand classifier (CV F1 0.996).

**Tech:** Python, pandas, numpy, scikit-learn, DuckDB, rapidfuzz, matplotlib, seaborn | Open Food Facts, Mercadona/Albert Heijn scraped data

### EU Food Safety Regulatory Intelligence

RAG system over the EU food safety regulatory corpus (~120 regulations) that answers: for a company launching product X in the EU, which food safety regulations apply and what are the compliance requirements? Regulatory consulting firms bill €300–500/hour for this work; compliance SaaS platforms charge €10K–50K/year. The system extracts every regulated entity from EUR-Lex documents to build structured input options and deterministic routing, then uses LLM extraction to generate compliance checklists. Evaluation targets 82% precision against expert-validated ground truth. The key technical challenges are chunking dense cross-referential legal text and resolving amendment chains ("Regulation X as amended by Directive Y").

**Planned tech:** LangChain, FAISS/Chroma, Streamlit, FastAPI, Docker | EUR-Lex corpus

### Corporate Earnings Macro Surveillance

Structured extraction pipeline over earnings call transcripts that replicates central bank macroeconomic surveillance signals. Ingests transcripts from multiple APIs, extracts reported numbers, forward guidance, risk themes, sentiment shifts, and competitor mentions per call. Aggregates extracted signals across companies and quarters to identify sector-level trends and leading macro indicators. Evaluation compares extracted guidance against actual reported numbers and extracted sentiment against market reaction.

**Planned tech:** LLM extraction, Streamlit, FastAPI, Docker | Earnings call transcripts (multi-API)

### Custom ESG Embedding Model

Fine-tuned sentence-transformer for ESG/sustainability information retrieval. General-purpose embeddings show a 20–40% performance drop on domain-specific retrieval (arXiv 2409.18511); sustainability reports use specialised vocabulary ("Scope 3 Category 15", "TCFD Pillar 2", "GRI 305-1") that general models were not trained on. The project constructs 15K+ query-passage pairs from sustainability reports (ESGBench, CDP, GRI, TCFD), fine-tunes all-mpnet-base-v2 with contrastive learning, and evaluates with NDCG@10 / MRR / Recall@K against BM25 and off-the-shelf embedding baselines. The final model is published to HuggingFace Hub with a side-by-side search comparison demo.

**Planned tech:** PyTorch, SentenceTransformers, ONNX, Streamlit, FastAPI, Docker | ESGBench, CDP, GRI, TCFD reports

### Fine-Tune vs. Prompt Benchmark (parked)

Decision framework for when to fine-tune a small model vs. use LLM API calls for text classification. P2 (Custom ESG Embedding Model) was validated as stronger on 9/12 evaluation dimensions (lower saturation, novel artifact, direct RAG relevance), so this project is parked.

## Skill Coverage Matrix

| Dimension | Steam Market Gap | Private Label | Food Safety (L1) | Macro Surveillance (B1) | ESG Embeddings (P2) |
|-----------|-----------------|--------------|-------------------|--------------------------|----------------------|
| **Domain** | Gaming/entertainment | Retail/CPG | EU regulation | Finance/macro | ESG/sustainability |
| **Core technique** | ALS collaborative filtering, market gap scoring | Competitive analysis, scoring | RAG + structured extraction | NLP extraction + time series | Contrastive learning, IR evaluation |
| **Data sources** | Steam Web API + SteamSpy + RAWG | Open Food Facts + scrapers | EUR-Lex corpus | Earnings transcripts (multi-API) | ESGBench + CDP + GRI + TCFD + synthetic |
| **Modern stack** | Classical (implicit, scikit-learn) | Classical | LangChain, vector stores | LLM extraction | PyTorch, SentenceTransformers, ONNX |
| **Key artifact** | Market niche rankings + recommender | Scoring dashboard | Compliance extraction API | Macro indicator pipeline | Published HuggingFace model |
| **Deployment** | Streamlit | Streamlit | Streamlit + FastAPI + Docker | Streamlit + FastAPI + Docker | Streamlit + FastAPI + Docker + HF Hub |
