# PROJECT AUDIT — COMPLETE REPOSITORY ANALYSIS
## PFE: Design, Development, and Evaluation of a RAG Conversational Assistant Based on the Model Context Protocol (MCP) for Secure and Intelligent Access to Enterprise Knowledge Stored in SharePoint

**Author:** Jean Direl NZE  
**Program:** Programme Grande École (PGE5) — Aivancity School for Technology and Business, Villejuif, France  
**Audit Date:** June 2026  
**Auditor:** Claude Code (AI Research Director)  
**Repository:** `/home/user/PFE-Aivancity`

---

## EXECUTIVE SUMMARY

This audit constitutes the mandatory first phase (Phase 1) of the iterative thesis production process. It provides a complete, honest, and exhaustive inventory of every artifact present in the repository, maps the documented system architecture against the evidence actually available, identifies critical gaps, and establishes the risk register that will govern the writing strategy for the final thesis.

**Critical finding:** The repository contains exclusively documentation artifacts (PDFs and HTML phase reports). No source code, notebooks, Docker/Kubernetes configurations, evaluation datasets, experimental logs, or screenshots are present. The entire technical system described in Phase 1 documents must be treated as *described but not evidenced* within this repository. The thesis writing strategy must account for this gap explicitly.

---

## 1. REPOSITORY ARCHITECTURE

```
/home/user/PFE-Aivancity/
│
├── README.md                                          [55 bytes — minimal]
│
├── cahiers de charges finctionnelles.pdf              [4.4 MB — unreadable: missing poppler-utils]
│
├── phase1/
│   ├── JeanDirel_PFEPhase1_Documentfinal.pdf         [143 KB — unreadable: missing poppler-utils]
│   ├── Phase1_report.pdf                             [118 KB — unreadable: missing poppler-utils]
│   ├── report_phase1_en.html                         [9.4 KB — READABLE — English version]
│   ├── report_phase1_fr (1).pdf                      [145 KB — unreadable: missing poppler-utils]
│   ├── report_phase1_fr.html                         [10.4 KB — READABLE — French version]
│   └── report_phase1_fr.pdf                          [145 KB — unreadable: missing poppler-utils]
│
└── phase2/
    ├── Guide PFE PGE_English.pdf                     [289 KB — FULLY READ — school guidelines]
    ├── Guide PFE PGE_French.pdf                      [961 KB — unreadable: missing poppler-utils]
    ├── PFE PGE.pdf                                   [534 KB — unreadable: missing poppler-utils]
    ├── PFE_example_template.pdf                      [1.05 MB — unreadable: missing poppler-utils]
    └── PGE5_2526PFE_Guidelines.pptx.pdf              [477 KB — unreadable: missing poppler-utils]
```

**Total files:** 13 (excluding .git)  
**Total readable files:** 4 (2 HTML + 1 MD + 1 PDF via tool)  
**Total unreadable files:** 9 PDFs (poppler-utils not installed in environment)  
**Source code files:** 0  
**Notebooks:** 0  
**Infrastructure files:** 0

---

## 2. FUNCTIONAL ARCHITECTURE (Reconstructed from Phase 1 Reports)

The following functional architecture is reconstructed exclusively from the Phase 1 HTML reports. It is **described** but not corroborated by source code evidence in this repository.

### 2.1 System Name
**"AntiGravity"** — internal prototype name for the RAG + MCP conversational assistant.

### 2.2 System Purpose
An intelligent conversational assistant designed to provide semantic, sourced, and traceable access to enterprise business documents stored on SharePoint CERP (the collaborative platform of the DNSI — Direction du Numérique et des Systèmes d'Information).

### 2.3 Core Functional Components (as described)

| Component | Description | Status in Repo |
|-----------|-------------|----------------|
| SharePoint Connector | MCP-compatible connector for document extraction from SharePoint CERP | Described only |
| Document Ingestion Pipeline | Secure ingestion of PDF and DOCX files | Described only |
| Chunking/Segmentation Engine | Unstructured data pre-processing (segmentation) | Described only |
| Vectorization Engine | Embedding generation for semantic search | Described only |
| Vector Index (FAISS) | Dense semantic similarity search index | Described only |
| Re-ranking Module | Query optimization and result re-ranking | Described only |
| Query Classification | Request type classification for routing | Described only |
| LLM Interface (Mistral AI) | Generation layer using Mistral AI models | Described only |
| Conversational UI (Streamlit) | Python-based web interface for end-users | Described only |
| SSO/ACL Security Layer | Single Sign-On + Access Control Lists enforcement | Described only |
| MCP Context Server | Standardized context management server | Described only |
| MCP Conversational Client | Client-side MCP interface | Described only |

### 2.4 Key Functional Flows (as described)

**User Query Flow:**
```
User Query (Streamlit UI)
    → Query Classification
    → Semantic Search (FAISS vector index)
    → Re-ranking of retrieved chunks
    → Context assembly (MCP Context Server)
    → LLM Generation (Mistral AI)
    → Sourced + Traceable Response
    → User Interface Display
```

**Document Ingestion Flow:**
```
SharePoint CERP (PDF/DOCX documents)
    → Secure Extraction (MCP-compatible connector)
    → Document Segmentation (chunking)
    → Embedding Generation (vectorization)
    → FAISS Index Storage
```

**Security Flow:**
```
User Authentication (SSO)
    → ACL Verification (SharePoint permissions)
    → Filtered Document Access
    → Context Scoped to User Permissions
```

---

## 3. TECHNICAL ARCHITECTURE (Reconstructed from Phase 1 Reports)

### 3.1 Architecture Pattern
- **Paradigm:** Modular RAG Architecture + Model Context Protocol (MCP)
- **Design Principle:** Separation of the context server (FAISS index + documents) from the conversational client
- **Research Methodology:** Design Science Research (DSR) — iterating between theoretical design and practical implementation

### 3.2 Logical Architecture
```
┌─────────────────────────────────────────────────────────────┐
│                    PRESENTATION LAYER                        │
│              Streamlit UI (Python)                           │
└─────────────────────────┬───────────────────────────────────┘
                          │ MCP Protocol
┌─────────────────────────▼───────────────────────────────────┐
│                  MCP CONVERSATIONAL CLIENT                   │
│         Query Classification + Re-ranking                    │
└─────────────────────────┬───────────────────────────────────┘
                          │
┌─────────────────────────▼───────────────────────────────────┐
│                   MCP CONTEXT SERVER                         │
│     FAISS Vector Index | Document Store | ACL Engine        │
└──────────┬──────────────────────────────┬───────────────────┘
           │                              │
┌──────────▼──────────┐      ┌────────────▼────────────────────┐
│   MISTRAL AI (LLM)  │      │  SharePoint CERP Connector      │
│   Generation Layer  │      │  (MCP-compatible, SSO/ACL)      │
└─────────────────────┘      └─────────────────────────────────┘
```

### 3.3 Deployment Target (as described)
- **Infrastructure:** Containerized deployment
- **Compliance:** Enterprise security standards
- **Constraints noted:** Corporate proxy, latency, confidentiality

### 3.4 Architecture Qualities Claimed
- Horizontal scalability (via server/client separation)
- Increased maintainability
- Security-first design (SSO + ACL enforcement)
- Traceability of responses (sourcing)

---

## 4. DATA FLOW MAPPING

### 4.1 Data Sources
| Source | Format | Nature | Access Method |
|--------|--------|--------|---------------|
| SharePoint CERP | PDF, DOCX | Unstructured, private enterprise | MCP-compatible connector with SSO |

### 4.2 Data Processing Pipeline
```
Raw Documents (PDF/DOCX)
    [STAGE 1 — Extraction]
    → MCP-compatible SharePoint Connector
    → Authenticated extraction respecting ACLs
    
    [STAGE 2 — Pre-processing]
    → Document Segmentation (chunking strategy: not specified)
    → Text normalization (details: not available in repository)
    
    [STAGE 3 — Vectorization]
    → Embedding Model: not specified in available documents
    → FAISS Index construction (index type: not specified)
    
    [STAGE 4 — Retrieval]
    → Dense Retrieval: semantic similarity search via FAISS
    → Re-ranking: algorithm not specified
    
    [STAGE 5 — Generation]
    → Context injection into Mistral AI prompt
    → Response generation with source attribution
    
    [STAGE 6 — Output]
    → Sourced, traceable response delivered via Streamlit UI
```

### 4.3 Data Governance
- ACL enforcement: described (respects SharePoint permission model)
- Data sovereignty: mentioned as a key concern
- Confidentiality: enterprise-grade requirements stated
- No data retention policies documented in repository

---

## 5. TECHNOLOGIES INVENTORY

### 5.1 Confirmed Technologies (mentioned in Phase 1 reports)

| Technology | Category | Role | Evidence Level |
|------------|----------|------|----------------|
| Python | Programming Language | Primary development language | Mentioned |
| Streamlit | Web Framework | Conversational UI | Mentioned |
| FAISS (Facebook AI Similarity Search) | Vector Database | Dense retrieval index | Mentioned |
| Mistral AI (Mistral 7B) | LLM | Response generation | Mentioned |
| Model Context Protocol (MCP) | Protocol/Standard | Standardized AI-data interface | Core architecture |
| SharePoint CERP | Enterprise Platform | Primary data source | Mentioned |
| SSO (Single Sign-On) | Security | Authentication | Mentioned |
| ACL (Access Control Lists) | Security | Authorization | Mentioned |
| PDF/DOCX processing | Document handling | Ingestion pipeline | Mentioned |

### 5.2 Inferred Technologies (not explicitly mentioned but architecturally required)

| Technology | Inference Basis | Confidence |
|------------|----------------|------------|
| Sentence Transformers / OpenAI Embeddings | Vectorization required by FAISS pipeline | High |
| Microsoft Graph API | SharePoint access in enterprise environment | High |
| OAuth 2.0 / SAML | SSO implementation | High |
| Docker | "Containerized infrastructure" mentioned | High |
| Some chunking library (LangChain, LlamaIndex, etc.) | RAG pipeline segmentation stage | Medium |
| A re-ranking model (cross-encoder or BM25 hybrid) | Re-ranking mentioned | Medium |

### 5.3 Technologies NOT Evidenced in Repository
- No requirements.txt / pyproject.toml
- No Docker or docker-compose files
- No Kubernetes manifests
- No environment configuration files
- No dependency specifications of any kind

---

## 6. EXISTING EXPERIMENTS INVENTORY

### 6.1 Experiments Documented in Phase 1

| Experiment | Description | Results Available | Reproducible |
|------------|-------------|-------------------|--------------|
| Initial prototype validation | "First tests validate the system's ability to synthesize complex information from multiple SharePoint documents" | Qualitative mention only | No |
| Hallucination rate assessment | "Minimal hallucination rate" claimed | No quantitative data | No |
| Multi-document synthesis | System can synthesize from multiple SharePoint documents | Qualitative mention only | No |

### 6.2 Assessment
**Critical Gap:** No experimental data, evaluation logs, benchmark datasets, or quantitative results exist in the repository. All experiment references in Phase 1 are qualitative assertions without numerical backing. This is the most critical gap for the thesis.

---

## 7. EXISTING METRICS INVENTORY

### 7.1 Metrics Planned (mentioned in Phase 1)
| Metric Type | Metric | Status |
|-------------|--------|--------|
| Quantitative | Document retrieval precision | Planned, not measured |
| Qualitative | User satisfaction | Planned, not measured |
| Qualitative | Response fluency | Planned, not measured |
| Implicit | Hallucination rate | Mentioned as "minimal" — no data |

### 7.2 Metrics NOT Present in Repository
- No Precision@K measurements
- No Recall@K measurements
- No MRR (Mean Reciprocal Rank) scores
- No nDCG scores
- No BLEU/ROUGE scores
- No latency benchmarks
- No throughput measurements
- No user study data
- No comparative evaluation data (LLM alone vs RAG vs RAG+MCP)
- No confusion matrices
- No evaluation datasets (question-answer pairs)

---

## 8. DOCUMENTATION INVENTORY

### 8.1 Available Documentation

| Document | Language | Content | Quality |
|----------|----------|---------|---------|
| `report_phase1_en.html` | English | Phase 1 research report: context, literature review, proposed solution, methodology, contributions | Good academic quality, 10 paragraphs |
| `report_phase1_fr.html` | French | Same as above in French | Good academic quality |
| `cahiers de charges finctionnelles.pdf` | Unknown | Functional specifications | Unreadable in this environment |
| `JeanDirel_PFEPhase1_Documentfinal.pdf` | Unknown | Final Phase 1 document | Unreadable in this environment |
| `Phase1_report.pdf` | Unknown | Phase 1 report (alternate version) | Unreadable in this environment |
| `Guide PFE PGE_English.pdf` | English | Aivancity school guidelines for PFE | Fully read — 12 pages |
| `Guide PFE PGE_French.pdf` | French | Same guidelines in French | Unreadable in this environment |
| `PFE PGE.pdf` | Unknown | Additional PFE specifications | Unreadable in this environment |
| `PFE_example_template.pdf` | Unknown | Example thesis template | Unreadable in this environment |
| `PGE5_2526PFE_Guidelines.pptx.pdf` | Unknown | PGE5 presentation guidelines | Unreadable in this environment |

### 8.2 School Guidelines Summary (from `Guide PFE PGE_English.pdf`)

**Mandatory thesis components:**
1. A clearly formulated research problem
2. A rigorous methodology (justified, with limitations identified)
3. Results and recommendations (analyzed, not merely descriptive)
4. Executive summary
5. Brief host company presentation
6. Glossary
7. Table of contents
8. Bibliography (must include scientific/academic references)

**Formal requirements:**
- Body: approximately **50 pages** (excluding annexes, cover, acknowledgements, executive summary, bibliography)
- Cover page: Aivancity letterhead, company, title, year, student name, supervising professor
- Front matter sequence: Abstract → Acknowledgements/Declaration → Table of Contents → List of Tables/Figures → Body
- References: Author-date format (e.g., Dumoulin et al., 1998) in-text; full references in bibliography section
- Page numbering: all pages except title page and the four front matter pages
- Generative AI use: permitted but must be declared, referenced, and non-dominant

**Evaluation criteria (supervisor assessment):**
- Relevance and formalization of the research problem
- Validity of methods used (vs. alternatives not chosen)
- Debatability and rigor of results
- Quality and reliability of reasoning
- Generalizability of conclusions
- Admissibility of thesis structure

**Timeline:**
- February: Research question + problem + bibliography (10 refs, 5 scientific)
- March: Intermediate report (Phase 1) with problem, plan, literature synthesis, implementation description
- April: Progress report, problem identification
- June: Results and analysis finalization
- July: Supervisor verification
- September: Final defense (20-min presentation + 20-min Q&A + 10-min debriefing)

**Defense:** Jury = Supervising Professor + qualified assessor (program director or permanent professor) + optional company representative.

---

## 9. MISSING INFORMATION INVENTORY

### 9.1 Critical Missing Elements (Thesis Cannot Be Written Without These)

| Missing Element | Impact | Mitigation Strategy |
|----------------|--------|---------------------|
| Source code of the AntiGravity system | Cannot verify implementation claims or architecture details | Must be added to repository OR thesis must clearly distinguish design from implementation |
| Evaluation dataset (Q&A pairs for benchmarking) | Cannot produce quantitative RAG evaluation | Must be created: design synthetic benchmark from SharePoint document set |
| Quantitative retrieval metrics (Precision@K, Recall@K, MRR, nDCG) | Entire evaluation chapter absent | Must run experiments or document why experiments were limited |
| Generation quality metrics (faithfulness, relevance, groundedness) | Hallucination analysis impossible without data | Must design and execute evaluation protocol |
| Latency / throughput benchmarks | System evaluation chapter impossible | Must instrument and measure or reference proxy benchmarks |
| User evaluation data (satisfaction survey) | User study absent | Must design and conduct a user study OR document why it was not possible |
| Comparative evaluation (LLM alone vs RAG vs RAG+MCP) | Core scientific contribution not demonstrated | Must design controlled experiment or discuss why comparison was not feasible |
| Embedding model specification | Vectorization pipeline incomplete | Must identify the embedding model actually used |
| Chunking strategy details | Data processing chapter incomplete | Must document chunk size, overlap, strategy rationale |
| FAISS index type and configuration | Technical implementation incomplete | Must specify index type (Flat, IVF, HNSW, etc.) |
| Deployment environment details | Infrastructure chapter impossible | Must document: OS, hardware, container runtime, resource allocation |

### 9.2 Important Missing Elements (Weaken Thesis Quality)

| Missing Element | Impact |
|----------------|--------|
| Architecture diagrams (visual) | No figures available for technical chapters |
| SharePoint integration details (API version, Graph API calls) | Integration chapter is purely textual |
| Re-ranking algorithm specification | Methodology chapter incomplete |
| Query classification model details | Methodology chapter incomplete |
| Mistral AI model version and configuration | Reproducibility compromised |
| Prompt engineering documentation | Generation pipeline not reproducible |
| Error analysis / failure cases | Critical discussion lacks evidence |
| Screenshots of the running application | UI chapter cannot be illustrated |
| Performance comparison with baseline systems | Positioning of contribution is weakened |

### 9.3 Academically Missing Elements (Required by School Guidelines)

| Missing Element | Guideline Reference |
|----------------|---------------------|
| Formal research question (3 proposed formulations) | Chapter IV, First step |
| 10 bibliographic references including 5 scientific articles | Chapter IV, First step |
| Detailed thesis plan (organized structure) | Chapter IV, Second stage |
| Literature synthesis document | Chapter IV, Second stage |
| Executive summary | Chapter II, Section 4 |
| Glossary | Chapter II, Section 4 |
| Host company presentation (DNSI: activities, org chart, etc.) | Chapter II, Section 4 |

---

## 10. RISKS AND GAPS REGISTER

### 10.1 Risk Matrix

| ID | Risk | Probability | Impact | Severity | Mitigation |
|----|------|-------------|--------|----------|------------|
| R01 | No source code available — implementation claims cannot be verified | Confirmed | Critical | **CRITICAL** | Reconstruct from descriptions; be transparent in thesis about evidence level |
| R02 | No quantitative evaluation data — thesis lacks scientific rigor | Confirmed | Critical | **CRITICAL** | Design and execute evaluation experiments before writing evaluation chapter |
| R03 | Most PDFs unreadable in current environment — functional specs unknown | Confirmed | High | **HIGH** | Install poppler-utils OR access PDFs via other means to extract content |
| R04 | No user study data — qualitative evaluation missing | Confirmed | High | **HIGH** | Design a user study protocol; even limited (5-10 users) is better than absent |
| R05 | No comparative baseline — RAG vs LLM-alone vs RAG+MCP not measured | Confirmed | High | **HIGH** | Design controlled experiment; document limitations of partial comparison |
| R06 | Thesis risk becoming internship report | Structural risk | Critical | **CRITICAL** | Maintain research frame throughout; all decisions must serve the research question |
| R07 | Generative AI detection — if thesis is primarily AI-generated | School policy risk | High | **HIGH** | All AI-generated content must be declared per school policy; student must provide critical analysis layer |
| R08 | Chunking/embedding strategy undocumented | Medium | Medium | **MEDIUM** | Reconstruct from implementation or justify choices academically |
| R09 | MCP protocol maturity risk — very recent standard (2024) | Scientific | Medium | **MEDIUM** | This is also an opportunity: novelty of the research axis. Document carefully |
| R10 | DNSI confidentiality constraints | Legal/Academic | Medium | **MEDIUM** | Use confidentiality agreement per school guidelines; anonymize as needed |

### 10.2 Scientific Gaps

| Gap | Description | Thesis Consequence |
|-----|-------------|-------------------|
| G01 | No formal definition of "MCP-compatible" in the context of this system | Research contribution is weakly defined |
| G02 | No comparison with alternative architectures (LangChain, LlamaIndex, Azure Cognitive Search) | Positioning of contribution lacks rigor |
| G03 | No ablation study (RAG without MCP, MCP without RAG) | Cannot isolate the contribution of each component |
| G04 | Hallucination measurement methodology undefined | Core claim ("minimal hallucination rate") is unverified |
| G05 | Security evaluation not conducted | Security claims (SSO, ACL) are architectural, not validated |

---

## 11. BIBLIOGRAPHY EXTRACTED FROM PHASE 1 REPORTS

The following references were cited in the Phase 1 HTML reports and form the starting point for the thesis bibliography:

| # | Reference | Type |
|---|-----------|------|
| 1 | Lewis, P., et al. (2020). "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks". *Advances in Neural Information Processing Systems*, 33. | Scientific article (foundational RAG paper) |
| 2 | Anthropic (2024). "Model Context Protocol: An Open Standard for Connecting AI Systems to Data". *Technical Specification*. | Technical specification |
| 3 | Jiang, A., et al. (2023). "Mistral 7B". *arXiv preprint arXiv:2310.06825*. | Scientific article |
| 4 | Microsoft (2024). "SharePoint Online Architecture and Security Model". *Microsoft Technical Documentation*. | Technical documentation |
| 5 | Johnson, J., Douze, M., & Jégou, H. (2019). "Billion-scale similarity search with GPUs". *IEEE Transactions on Big Data*. | Scientific article (FAISS) |
| 6 | Gao, Y., et al. (2024). "Retrieval-Augmented Generation for Large Language Models: A Survey". *arXiv preprint arXiv:2312.10997*. | Survey article |
| 7 | Vaswani, A., et al. (2017). "Attention Is All You Need". *Advances in Neural Information Processing Systems*, 30. | Scientific article (Transformer) |
| 8 | Hevner, A. R., et al. (2004). "Design Science in Information Systems Research". *MIS Quarterly*, 28(1). | Scientific article (DSR methodology) |
| 9 | OpenAI (2023). "GPT-4 Technical Report". *arXiv preprint arXiv:2303.08774*. | Technical report |
| 10 | ISO/IEC 27001 (2022). "Information security, cybersecurity and privacy protection". *International Organization for Standardization*. | Standard |

**Assessment:** 10 references identified. 5+ are scientific articles (items 1, 3, 5, 6, 7, 8). This meets the minimum school requirement for Phase 1 but is **insufficient** for a final thesis. Target: 40–60 references for the final thesis.

**Missing bibliography areas:**
- Enterprise AI deployment literature
- Semantic search / dense retrieval literature (beyond Lewis 2020)
- Knowledge management in enterprises
- LLM hallucination and grounding literature
- Evaluation methodologies for RAG systems (RAGAS, ARES, etc.)
- Data governance and AI security in enterprise environments
- MCP protocol technical papers (beyond Anthropic 2024)
- Comparative studies of RAG architectures

---

## 12. SYNTHESIS AND STRATEGIC RECOMMENDATIONS FOR THE THESIS

### 12.1 What the Repository Provides
- A well-articulated research problem rooted in a real industrial context (DNSI / SharePoint)
- A credible system design (AntiGravity) with architectural coherence
- A methodological framing (Design Science Research) that is academically recognized
- A novel research axis (MCP applied to enterprise RAG) that is timely and differentiating
- A Phase 1 report of good academic quality in both French and English
- Full school guidelines to align the final thesis structure

### 12.2 What the Repository Does NOT Provide
- Source code (the system as implemented)
- Any form of quantitative evaluation data
- Architecture diagrams or visual artifacts
- User study data
- Deployment evidence (logs, performance benchmarks)
- The functional specifications document content (cahiers des charges — unreadable)
- Any experimental protocols or evaluation datasets

### 12.3 Thesis Writing Strategy (Recommended)

Given the evidence available, the thesis must be written under the following principles:

**Principle 1 — Honesty about evidence level:** Clearly distinguish in each chapter between (a) architectural design decisions (which are evidenced by Phase 1 documents) and (b) implementation claims (which must either be corroborated by code/data or qualified with appropriate epistemic humility).

**Principle 2 — Design Science Research framing:** The DSR methodology explicitly supports a thesis that contributes an *artifact* (the designed system) as its primary scientific contribution. The system design, its theoretical justification, and its partial empirical validation are all valid contributions under DSR.

**Principle 3 — Evaluation must be constructed:** Before the evaluation chapter can be written, an evaluation protocol must be designed and executed. At minimum, a synthetic benchmark (20–50 Q&A pairs from the SharePoint document corpus) must be created and run through the system.

**Principle 4 — The comparison experiment is the scientific core:** The central scientific contribution is the demonstration that RAG + MCP outperforms alternatives (LLM alone, naive RAG) on measurable dimensions. This experiment must be designed and run.

**Principle 5 — MCP novelty is the differentiator:** No published thesis at Master's level has evaluated MCP in the context of enterprise RAG (as of June 2026, given MCP was released in late 2024). This novelty must be foregrounded as the primary scientific contribution.

### 12.4 Immediate Next Steps Required

Before Phase 2 (Research Design) can be finalized:

1. **[CRITICAL]** Access and read the functional specifications PDF (`cahiers de charges finctionnelles.pdf`) — requires poppler-utils installation
2. **[CRITICAL]** Access and read `PFE_example_template.pdf` — needed for thesis format compliance
3. **[CRITICAL]** Confirm whether source code exists elsewhere (e.g., a separate private repository) — if so, it must be cloned here
4. **[HIGH]** Design the evaluation protocol (benchmark dataset, metrics, experimental conditions)
5. **[HIGH]** Create architecture diagrams for the system
6. **[MEDIUM]** Expand bibliography to 40+ references

---

## APPENDIX A — FILE CHECKSUMS AND ACCESSIBILITY

| File | Size | Readable | Tool Used |
|------|------|----------|-----------|
| README.md | 55 bytes | Yes | Read tool |
| cahiers de charges finctionnelles.pdf | 4.4 MB | No (missing poppler) | — |
| phase1/JeanDirel_PFEPhase1_Documentfinal.pdf | 143 KB | No (missing poppler) | — |
| phase1/Phase1_report.pdf | 118 KB | No (missing poppler) | — |
| phase1/report_phase1_en.html | 9.4 KB | Yes | Read tool |
| phase1/report_phase1_fr (1).pdf | 145 KB | No (missing poppler) | — |
| phase1/report_phase1_fr.html | 10.4 KB | Yes | Read tool |
| phase1/report_phase1_fr.pdf | 145 KB | No (missing poppler) | — |
| phase2/Guide PFE PGE_English.pdf | 289 KB | Yes | Read tool (8 pages) |
| phase2/Guide PFE PGE_French.pdf | 961 KB | No (missing poppler) | — |
| phase2/PFE PGE.pdf | 534 KB | No (missing poppler) | — |
| phase2/PFE_example_template.pdf | 1.05 MB | No (missing poppler) | — |
| phase2/PGE5_2526PFE_Guidelines.pptx.pdf | 477 KB | No (missing poppler) | — |

---

## APPENDIX B — SCHOOL GUIDELINES COMPLIANCE CHECKLIST

| Requirement | Status | Notes |
|-------------|--------|-------|
| Research problem formulated | Partial | Phase 1 has a problem statement; needs formalization for thesis |
| Methodology described | Partial | DSR mentioned; needs full methodological chapter |
| Results analyzed (not merely described) | Missing | No results in repository |
| Recommendations developed | Missing | |
| Executive summary | Missing | |
| Host company presentation (DNSI) | Partial | Brief description in Phase 1; needs full section |
| Glossary | Missing | |
| Table of contents | Missing | |
| Bibliography with scientific references | Partial | 10 refs identified; 40+ needed for final thesis |
| ~50 pages body | Missing | Nothing written yet |
| Aivancity cover page | Missing | Template needed |
| Page numbering | Missing | |
| Annexes summary | Missing | |
| Declaration of AI use | Missing | Required per school policy |

---

*Audit completed. Awaiting validation before proceeding to Phase 2 — Research Design.*
