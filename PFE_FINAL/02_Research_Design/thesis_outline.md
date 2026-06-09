# THESIS OUTLINE — TABLE OF CONTENTS
## Design, Development, and Evaluation of a RAG Conversational Assistant Based on the Model Context Protocol (MCP) for Secure and Intelligent Access to Enterprise Knowledge Stored in SharePoint

**Author:** Jean Direl NZE  
**Program:** PGE5 — Aivancity School for Technology and Business  
**Version:** 1.0 — June 2026  
**Target length:** 80–120 pages (body) + annexes  
**School minimum:** ~50 pages (body, per guidelines)  

---

## FRONT MATTER (not counted in page total)

| Element | Estimated Pages |
|---------|----------------|
| Cover page (Aivancity letterhead) | 1 |
| Abstract (English + French) | 2 |
| Acknowledgements and Declaration | 1 |
| Table of Contents | 2 |
| List of Figures | 1 |
| List of Tables | 1 |
| List of Abbreviations / Glossary | 2 |
| **Front matter total** | **~10** |

---

## BODY — CHAPTER STRUCTURE

---

### CHAPTER 1 — INTRODUCTION
**Estimated pages:** 8–10  
**Estimated figures:** 1 (positioning diagram)  
**Estimated tables:** 0  

| Section | Content |
|---------|---------|
| 1.1 General context | Digital transformation and knowledge management in large organizations; the information access problem in enterprise IT |
| 1.2 Industrial context | DNSI: organization, mission, SharePoint CERP, scale of documentation, current limitations |
| 1.3 Research motivation | Gap between available enterprise knowledge and accessible enterprise knowledge; why LLMs alone are insufficient |
| 1.4 Research problem and questions | Formal problem statement; RQ1–RQ5 presented |
| 1.5 Research objectives | Scientific, technical, and practical objectives |
| 1.6 Thesis contributions | SC1–SC4 and TC1–TC4 presented |
| 1.7 Thesis structure | Chapter-by-chapter roadmap |

**Writing notes:** Must establish the research frame immediately. The introduction must read as a scientific paper introduction, not a company presentation. The DNSI context is background, not the focus.

---

### CHAPTER 2 — BACKGROUND AND STATE OF THE ART
**Estimated pages:** 20–25  
**Estimated figures:** 4–6 (RAG architecture diagram, transformer architecture, MCP architecture, comparison table)  
**Estimated tables:** 3–4 (comparison of retrieval methods, comparison of RAG variants, MCP vs alternatives)  

| Section | Content |
|---------|---------|
| 2.1 Large Language Models | Transformer architecture (Vaswani et al., 2017); capabilities and limitations; hallucination phenomenon; knowledge cutoff problem |
| 2.2 Retrieval-Augmented Generation | RAG foundational paper (Lewis et al., 2020); dense retrieval vs sparse retrieval; RAG variants (modular RAG, corrective RAG, agentic RAG); evaluation of RAG systems (Gao et al., 2024) |
| 2.3 Vector search and semantic indexing | Embedding models (sentence transformers, OpenAI embeddings); FAISS index types (Flat, IVF, HNSW); approximate nearest neighbor search; Johnson et al. (2019) |
| 2.4 Re-ranking in RAG pipelines | Cross-encoder re-ranking; BM25 hybrid; ColBERT; impact on precision |
| 2.5 Enterprise knowledge management | SharePoint architecture and security model; Microsoft Graph API; ACL model; document formats (PDF, DOCX) |
| 2.6 The Model Context Protocol (MCP) | MCP specification (Anthropic, 2024); MCP architecture (client/server/transport layers); MCP vs LangChain vs LlamaIndex; advantages for enterprise integration; adoption state (2024–2026) |
| 2.7 Security in enterprise AI systems | ISO/IEC 27001 requirements; SSO and OAuth 2.0; ACL-aware retrieval; data sovereignty; threat model for conversational AI systems |
| 2.8 RAG evaluation frameworks | RAGAS (Es et al., 2023); faithfulness; groundedness; answer relevancy; context precision; hallucination measurement |
| 2.9 Research gap and positioning | Synthesis table: what existing work covers vs what this thesis contributes |

**Writing notes:** This chapter must be genuinely analytical, not merely descriptive. Each section must conclude with a critical assessment of limitations in the current state of the art that the thesis addresses. The research gap section (2.9) must make the novelty of this work unmistakably clear.

---

### CHAPTER 3 — RESEARCH METHODOLOGY
**Estimated pages:** 8–10  
**Estimated figures:** 2 (DSR cycle diagram, experimental design diagram)  
**Estimated tables:** 2 (evaluation metrics summary, experimental conditions)  

| Section | Content |
|---------|---------|
| 3.1 Research paradigm | Design Science Research (Hevner et al., 2004); justification for DSR over alternative paradigms (action research, case study, experiment-only); three DSR cycles applied to this thesis |
| 3.2 Research design overview | Phase-by-phase overview: problem formulation → artifact design → construction → evaluation → analysis |
| 3.3 Artifact design methodology | Architecture decision methodology; design principles; trade-off analysis framework |
| 3.4 Evaluation methodology | Benchmark dataset construction; three experimental conditions (LLM alone, RAG, RAG+MCP); retrieval evaluation protocol; generation evaluation protocol; system evaluation protocol; user study protocol |
| 3.5 Validity and reliability | Internal validity threats and mitigations; external validity; reliability; reproducibility measures |
| 3.6 Ethical considerations | Data privacy (DNSI documents); user consent; AI use declaration; confidentiality |
| 3.7 Limitations of the methodology | Small dataset size; single-organization context; LLM non-determinism; corporate constraints on user study |

---

### CHAPTER 4 — SYSTEM DESIGN AND ARCHITECTURE
**Estimated pages:** 18–22  
**Estimated figures:** 6–8 (overall architecture, data flow, MCP connector design, security model, FAISS index structure, UI wireframe/screenshot)  
**Estimated tables:** 3–4 (component comparison, design decisions, security properties)  

| Section | Content |
|---------|---------|
| 4.1 Requirements analysis | Functional requirements (FR1–FRn); non-functional requirements (security, latency, scalability, maintainability); requirements derived from DNSI context |
| 4.2 Architecture overview | Layered architecture: Presentation → MCP Client → MCP Context Server → LLM + Data Source; architectural patterns chosen; justification |
| 4.3 MCP integration design | MCP protocol applied to SharePoint; client/server separation; transport layer choice; context window management; why MCP vs alternatives (LangChain connectors, Azure Cognitive Search, raw Graph API) |
| 4.4 Document ingestion pipeline | SharePoint extraction (Graph API + SSO); supported formats (PDF, DOCX); chunking strategy (choice of chunk size, overlap — justified with experimentation); text normalization |
| 4.5 Vectorization and indexing | Embedding model selection and justification (trade-off: quality vs latency vs cost); FAISS index type selection (Flat vs IVF — justified with scale analysis); index construction and persistence |
| 4.6 Retrieval and re-ranking | Dense retrieval query flow; re-ranking module design; query classification; hybrid retrieval considerations |
| 4.7 Generation pipeline | Prompt engineering design; context injection strategy; source attribution mechanism; Mistral AI model configuration |
| 4.8 Security architecture | SSO implementation (OAuth 2.0 / SAML); ACL enforcement in the retrieval pipeline; per-user context filtering; threat model and mitigations; compliance with ISO/IEC 27001 principles |
| 4.9 User interface | Streamlit application design; conversation history; source citation display; user feedback mechanism |
| 4.10 Deployment architecture | Containerization design; enterprise proxy compatibility; configuration management |

**Writing notes:** Every design decision must follow the pattern: (1) state the requirement, (2) enumerate alternatives considered, (3) justify the chosen approach, (4) discuss trade-offs and limitations. This is where the engineering contribution lives.

---

### CHAPTER 5 — IMPLEMENTATION
**Estimated pages:** 10–12  
**Estimated figures:** 3–4 (code architecture diagram, pipeline execution trace, screenshot of running system)  
**Estimated tables:** 2 (implementation stack, configuration parameters)  

| Section | Content |
|---------|---------|
| 5.1 Implementation environment | Hardware and software environment; Python ecosystem; dependency management |
| 5.2 MCP-compatible SharePoint connector | Implementation of the connector: Graph API calls, authentication flow, document extraction logic; key engineering challenges encountered |
| 5.3 Ingestion pipeline implementation | Chunking implementation (chunk size chosen: X tokens, overlap: Y tokens — justified); embedding generation; FAISS index construction and persistence |
| 5.4 Context server implementation | MCP server implementation; request/response protocol; ACL filtering logic |
| 5.5 Conversational client implementation | Query classification; re-ranking implementation; prompt template; Mistral AI API calls |
| 5.6 Streamlit UI implementation | Interface components; session state management; source citation rendering |
| 5.7 Implementation challenges | Corporate proxy configuration; authentication complexity; latency bottlenecks encountered; chunking quality issues |
| 5.8 Reproducibility | Configuration file structure; environment setup instructions; known limitations for replication |

**Writing notes:** Implementation chapter is descriptive but must remain analytical. Every challenge section must link back to a design decision and either validate or challenge the architectural choice.

---

### CHAPTER 6 — EVALUATION AND RESULTS
**Estimated pages:** 15–20  
**Estimated figures:** 8–10 (metric bar charts, precision-recall curves, latency distribution plots, user study results)  
**Estimated tables:** 6–8 (all metrics per condition, statistical tests, user study scores, error analysis)  

| Section | Content |
|---------|---------|
| 6.1 Evaluation protocol | Benchmark dataset description (N questions, source, annotation methodology, inter-annotator agreement); experimental conditions (A: LLM alone, B: RAG, C: RAG+MCP); reproducibility statement |
| 6.2 Retrieval evaluation | Precision@K (K=1,3,5,10) per condition; Recall@K; MRR; nDCG@5; comparison BM25 vs dense vs dense+rerank; statistical significance (paired t-test or Wilcoxon) |
| 6.3 Generation evaluation | Faithfulness scores per condition (A, B, C); answer relevancy; context precision; hallucination rate analysis; qualitative error taxonomy; representative examples (correct vs hallucinated) |
| 6.4 System performance evaluation | End-to-end latency (P50, P95, P99) per component; throughput; FAISS index query time; MCP overhead quantification; memory footprint |
| 6.5 User evaluation | SUS scores; TAM usefulness and ease-of-use scores; task completion rates; qualitative themes from interviews; comparison with current SharePoint search |
| 6.6 Ablation study | Impact of re-ranking (with vs without); impact of chunk size; impact of retrieval K on generation quality |
| 6.7 Results summary | Unified summary table: all hypotheses (H1–H6) tested and confirmed/rejected/partially confirmed with evidence |

**Writing notes:** This is the scientific core of the thesis. Results must never be presented without interpretation. Every table must have a paragraph of analysis. Statistical significance must be reported. Negative results must be discussed honestly — they are as valuable as positive ones.

---

### CHAPTER 7 — DISCUSSION
**Estimated pages:** 10–12  
**Estimated figures:** 1–2 (positioning map, contribution summary diagram)  
**Estimated tables:** 1–2 (limitations vs mitigations, future work prioritization)  

| Section | Content |
|---------|---------|
| 7.1 Interpretation of results | What the results mean in relation to the research questions; confirmation or rejection of each hypothesis with analysis of WHY |
| 7.2 Contribution analysis | What this thesis actually contributes beyond the state of the art; how SC1–SC4 are validated by the experimental results |
| 7.3 The value of MCP | Critical assessment: does MCP actually deliver the promised benefits (interoperability, security, maintainability) in practice? Where does it fall short? What are the costs (overhead, complexity)? |
| 7.4 Strengths of the proposed architecture | What works well and why; cases where RAG+MCP clearly outperforms alternatives |
| 7.5 Weaknesses and limitations | Technical debt identified; architectural limitations; evaluation limitations (dataset size, single organization, LLM non-determinism); honest assessment of what was NOT proven |
| 7.6 Threats to validity | Revisiting the methodology limitations in light of actual results |
| 7.7 Deployment challenges | Real-world friction encountered: enterprise proxy, authentication, document quality, latency constraints; what would need to change for production deployment at scale |
| 7.8 Security analysis | Critical evaluation of the security architecture: what the ACL enforcement covers, what it does not; residual risks; compliance gaps |
| 7.9 Generalizability | To what extent can the AntiGravity architecture and findings be generalized beyond the DNSI context? What conditions need to hold? |
| 7.10 Future work | Prioritized roadmap: (1) real-time SharePoint delta sync, (2) multi-tenant deployment, (3) fine-tuning on DNSI vocabulary, (4) extension to other data sources, (5) agentic RAG exploration, (6) CIFRE PhD continuation directions |

**Writing notes:** This chapter must read as a researcher critically evaluating their own work. No overselling. The limitations section must be thorough and honest — evaluators penalize theses that hide weaknesses more than theses that acknowledge them.

---

### CHAPTER 8 — CONCLUSION
**Estimated pages:** 4–5  
**Estimated figures:** 0  
**Estimated tables:** 0  

| Section | Content |
|---------|---------|
| 8.1 Summary of contributions | Concise restatement of SC1–SC4 and TC1–TC4 with the evidence base for each |
| 8.2 Answers to research questions | RQ1–RQ5 answered explicitly, one paragraph each |
| 8.3 Scientific and practical implications | What this work means for the field of enterprise AI; recommendations for practitioners deploying RAG in enterprise environments |
| 8.4 Toward a CIFRE PhD | How this work establishes a foundation for a doctoral continuation: open problems, CIFRE positioning, potential research directions |

---

## BACK MATTER

| Element | Estimated Pages |
|---------|----------------|
| Bibliography (40–60 references) | 4–6 |
| Annex A: Benchmark dataset (Q&A pairs) | 5–8 |
| Annex B: User study questionnaire | 2–3 |
| Annex C: System configuration and deployment guide | 3–5 |
| Annex D: Evaluation raw data | 3–5 |
| Annex E: Declaration of AI tool use | 1 |
| **Back matter total** | **~18–28** |

---

## COMPLETE PAGE BUDGET

| Section | Min Pages | Max Pages |
|---------|-----------|-----------|
| Front matter | 10 | 10 |
| Chapter 1 — Introduction | 8 | 10 |
| Chapter 2 — Background & State of the Art | 20 | 25 |
| Chapter 3 — Methodology | 8 | 10 |
| Chapter 4 — System Design & Architecture | 18 | 22 |
| Chapter 5 — Implementation | 10 | 12 |
| Chapter 6 — Evaluation & Results | 15 | 20 |
| Chapter 7 — Discussion | 10 | 12 |
| Chapter 8 — Conclusion | 4 | 5 |
| Back matter | 18 | 28 |
| **TOTAL** | **121** | **154** |
| **Body only (school metric)** | **93** | **116** |

**Assessment:** Body target of 93–116 pages comfortably meets and exceeds the school's minimum of ~50 pages and aligns with the thesis instruction target of 80–120 pages.

---

## FIGURES BUDGET

| Chapter | Figures (min) | Figures (max) |
|---------|--------------|--------------|
| 1 | 1 | 1 |
| 2 | 4 | 6 |
| 3 | 2 | 2 |
| 4 | 6 | 8 |
| 5 | 3 | 4 |
| 6 | 8 | 10 |
| 7 | 1 | 2 |
| 8 | 0 | 0 |
| **Total** | **25** | **33** |

**Figures to be created:** All 25–33 figures must be created (system diagrams, evaluation charts, architecture diagrams). None currently exist in the repository.

---

## TABLES BUDGET

| Chapter | Tables (min) | Tables (max) |
|---------|-------------|-------------|
| 1 | 0 | 0 |
| 2 | 3 | 4 |
| 3 | 2 | 2 |
| 4 | 3 | 4 |
| 5 | 2 | 2 |
| 6 | 6 | 8 |
| 7 | 1 | 2 |
| 8 | 0 | 0 |
| **Total** | **17** | **22** |

---

## BIBLIOGRAPHY TARGET

| Category | Target Count |
|----------|-------------|
| Foundational AI / NLP papers | 8–10 |
| RAG and retrieval papers | 8–12 |
| Enterprise AI and knowledge management | 5–8 |
| LLM evaluation and hallucination | 5–8 |
| Security and enterprise IT | 4–6 |
| MCP and protocol standards | 2–4 |
| DSR methodology | 3–5 |
| Additional context / background | 5–10 |
| **Total** | **40–63** |

**Currently available:** 10 references (from Phase 1). **Need to add:** 30–50 additional references.

---

## WRITING SCHEDULE (RECOMMENDED)

| Week | Target |
|------|--------|
| Week 1–2 | Chapter 2 (Background & State of the Art) — literature-based, no new data needed |
| Week 3 | Chapter 3 (Methodology) — formalize DSR design, evaluation protocol |
| Week 4–5 | Chapter 4 (System Design & Architecture) — reconstruct from Phase 1 + supplement |
| Week 6 | Chapter 5 (Implementation) — document technical implementation |
| Week 7–8 | Run evaluation experiments; construct benchmark dataset |
| Week 9–10 | Chapter 6 (Evaluation & Results) — write from experimental data |
| Week 11 | Chapter 7 (Discussion) — critical analysis |
| Week 12 | Chapter 1 (Introduction) + Chapter 8 (Conclusion) |
| Week 13 | Front matter, bibliography, annexes, formatting |
| Week 14 | Supervisor review and revisions |

---

*Thesis outline complete. Awaiting validation before proceeding to Chapter writing.*
