# PHASE 2 — RESEARCH DESIGN
## Thesis: Design, Development, and Evaluation of a RAG Conversational Assistant Based on the Model Context Protocol (MCP) for Secure and Intelligent Access to Enterprise Knowledge Stored in SharePoint

**Author:** Jean Direl NZE  
**Program:** PGE5 — Aivancity School for Technology and Business  
**Version:** 1.0 — June 2026  

---

## 1. RESEARCH PROBLEM

### 1.1 Industrial Context

Large organizations such as the DNSI (Direction du Numérique et des Systèmes d'Information) accumulate vast quantities of technical and business documentation on collaborative platforms such as SharePoint. This documentation represents an organizational knowledge asset of high strategic value. However, its access remains predominantly manual, fragmented, and non-contextual: employees rely on basic keyword search or folder browsing, which is inadequate for complex, multi-document, or reasoning-intensive queries. The result is information friction — a measurable gap between the knowledge that exists in the organization and the knowledge that employees can practically access and use.

### 1.2 The Technical Gap

The advent of Large Language Models (LLMs) offers a compelling natural language interface to enterprise knowledge. However, direct deployment of LLMs in enterprise environments is blocked by three fundamental problems:

1. **Hallucination:** LLMs generate plausible but factually incorrect responses with no mechanism for self-correction from external knowledge.
2. **Knowledge cutoff:** LLMs are trained on public data up to a fixed date and have no awareness of the organization's private, internal, or post-cutoff documentation.
3. **Security and traceability:** LLMs provide no native mechanism for enforcing document-level access control or for citing the source of a claim.

Retrieval-Augmented Generation (RAG) architectures address these problems by coupling LLMs with an external retrieval system (Lewis et al., 2020). RAG has become the reference architecture for grounding LLM responses in a specific, private knowledge corpus. However, integrating RAG with heterogeneous enterprise data sources (such as SharePoint, with its permission model, file formats, and organizational structure) has historically relied on ad-hoc connectors: brittle, hard to maintain, and difficult to secure.

### 1.3 The Emerging Paradigm: Model Context Protocol (MCP)

In 2024, Anthropic introduced the Model Context Protocol (MCP) — an open standard designed to normalize how AI systems interface with external data sources (Anthropic, 2024). MCP defines a standardized protocol layer between AI models and data providers, promising increased interoperability, security, and maintainability compared to proprietary connectors. As of 2025–2026, MCP represents an emerging but rapidly adopted standard in the AI integration ecosystem.

The scientific and engineering question this thesis investigates is: **can a RAG architecture built on MCP principles deliver a measurably more reliable, secure, traceable, and accessible enterprise knowledge assistant than the alternatives?**

---

## 2. RESEARCH PROBLEM STATEMENT

### Formulation 1 (Technical)
> To what extent does a Retrieval-Augmented Generation architecture grounded in the Model Context Protocol enable more reliable, secure, and traceable access to enterprise knowledge stored in SharePoint, compared to a standalone LLM and a naive RAG implementation?

### Formulation 2 (Scientific)
> How can the standardization of the AI-data interface through the Model Context Protocol improve the groundedness, traceability, and security compliance of an enterprise conversational assistant, and what are the measurable performance trade-offs introduced by this architectural choice?

### Formulation 3 (Engineering)
> What architectural design decisions are required to deploy a production-grade RAG+MCP conversational assistant in an enterprise environment with strict security, confidentiality, and latency constraints, and how can the performance of such a system be rigorously evaluated?

**Selected formulation for the thesis (primary):** Formulation 1, with Formulation 2 as the scientific corollary and Formulation 3 as the engineering sub-question.

---

## 3. RESEARCH QUESTIONS

### RQ1 — Primary Research Question
**How does a RAG+MCP architecture compare to (a) a standalone LLM and (b) a naive RAG implementation in terms of factual correctness, response groundedness, and hallucination rate on an enterprise knowledge corpus?**

*This is the central empirical question. It requires a controlled comparative evaluation.*

### RQ2 — Retrieval Quality
**What retrieval configuration (chunking strategy, embedding model, similarity metric, re-ranking approach) maximizes Precision@K and nDCG on a domain-specific SharePoint document corpus?**

*This question governs the methodology chapter on the retrieval pipeline.*

### RQ3 — MCP Protocol Value
**What specific security, interoperability, and maintainability properties does the Model Context Protocol provide in an enterprise SharePoint integration context, and how do these compare to alternative integration approaches?**

*This question governs the architectural analysis and justification of the MCP design choice.*

### RQ4 — System Performance
**What are the latency, throughput, and scalability characteristics of the designed RAG+MCP system under realistic enterprise workload conditions?**

*This question governs the system evaluation section.*

### RQ5 — User Acceptance
**How do end-users (DNSI employees) perceive the usefulness, trustworthiness, and ease of use of the AntiGravity assistant compared to their current SharePoint search workflow?**

*This question governs the user evaluation section.*

---

## 4. RESEARCH HYPOTHESES

| ID | Hypothesis | Type | Evaluation Method |
|----|-----------|------|-------------------|
| H1 | The RAG+MCP system produces significantly fewer hallucinations than a standalone LLM (Mistral 7B) on DNSI business queries | Primary — empirical | Controlled experiment: hallucination rate comparison |
| H2 | The RAG+MCP system produces responses with higher factual groundedness than a naive RAG implementation (RAG without MCP standardization) | Primary — empirical | Faithfulness metric (RAGAS or equivalent) |
| H3 | Chunked semantic retrieval via FAISS achieves higher Precision@5 than BM25 keyword search on the DNSI SharePoint corpus | Retrieval — empirical | Precision@K comparison |
| H4 | The MCP layer introduces measurable latency overhead compared to direct API calls, but this overhead is within acceptable enterprise SLA bounds (<3 seconds end-to-end) | Performance | Latency benchmarking |
| H5 | Users rate the AntiGravity assistant as significantly more useful than the current SharePoint keyword search for complex multi-document queries | User acceptance | Likert-scale user study (SUS or TAM) |
| H6 | Re-ranking improves MRR by at least 15% compared to retrieval without re-ranking on the DNSI corpus | Retrieval — empirical | MRR comparison with/without re-ranking |

---

## 5. SCIENTIFIC CONTRIBUTIONS

### SC1 — Primary Scientific Contribution
**A formal comparative evaluation framework for RAG+MCP vs RAG vs LLM-alone in an enterprise context**, operationalized through a reproducible experimental protocol on a real organizational knowledge corpus. This framework includes:
- A domain-specific benchmark dataset (Q&A pairs derived from SharePoint documents)
- A standardized evaluation suite (Precision@K, Recall@K, MRR, nDCG, faithfulness, groundedness, hallucination rate)
- A statistical analysis protocol for significance testing

*Novelty:* No published empirical study has evaluated MCP-grounded RAG systems against baseline architectures on an enterprise SharePoint corpus.

### SC2 — Secondary Scientific Contribution
**A reference architecture for secure, ACL-aware RAG+MCP deployment in enterprise environments**, including:
- Design patterns for MCP-compatible SharePoint connectors
- An ACL-enforcement model that propagates SharePoint permissions into the retrieval layer
- A security analysis of the proposed architecture against enterprise threat models

*Novelty:* Existing RAG architectures do not systematically address SharePoint ACL propagation in the retrieval pipeline.

### SC3 — Methodological Contribution
**An application of Design Science Research (DSR) to the evaluation of enterprise AI systems**, demonstrating how DSR can structure both the artifact construction (system design) and the artifact evaluation (experimental validation) in a single cohesive research methodology.

### SC4 — Practical Contribution
**A proof-of-concept implementation** (AntiGravity) that validates the proposed architecture under real enterprise constraints (corporate proxy, latency, DNSI confidentiality requirements), serving as a template for future enterprise RAG deployments.

---

## 6. TECHNICAL CONTRIBUTIONS

### TC1 — MCP-Compatible SharePoint Connector
A documented, reusable connector that extracts documents from SharePoint CERP via the Microsoft Graph API, respects SharePoint ACLs, and exposes documents to the RAG pipeline through an MCP-compatible interface.

### TC2 — Retrieval Pipeline with Hybrid Re-ranking
A retrieval pipeline combining dense semantic search (FAISS) with a re-ranking module, optimized for the domain-specific vocabulary of the DNSI business corpus.

### TC3 — Security-Aware Context Server
An MCP Context Server that enforces user-level document access by filtering retrieval results against the authenticated user's SharePoint permissions before injecting context into the LLM prompt.

### TC4 — Evaluation Dataset
A reproducible benchmark dataset of domain-specific Q&A pairs derived from DNSI SharePoint documents, suitable for evaluating any SharePoint-based conversational assistant.

---

## 7. RESEARCH METHODOLOGY

### 7.1 Paradigm: Design Science Research (DSR)

The research adopts the **Design Science Research** paradigm (Hevner et al., 2004), which is the recognized methodology for research that produces both knowledge artifacts and design knowledge. DSR is particularly appropriate for this thesis because:

1. The primary output is a system artifact (AntiGravity) whose design constitutes the research contribution.
2. The artifact is evaluated against a real-world problem in its natural context (DNSI).
3. The research produces generalizable design principles that extend beyond the specific implementation.

DSR proceeds through three cycles:
- **Relevance Cycle:** Problem articulation from the industrial context (DNSI / SharePoint information access problem)
- **Design Cycle:** Iterative construction and evaluation of the artifact (AntiGravity system)
- **Rigor Cycle:** Grounding in existing scientific knowledge (RAG literature, MCP specification, enterprise AI security)

### 7.2 Research Design Overview

```
PHASE 1: Problem Formulation
    ├── Industrial context analysis (DNSI / SharePoint)
    ├── Literature review (RAG, MCP, enterprise AI, evaluation methods)
    └── Research question formalization

PHASE 2: Artifact Design
    ├── Architecture design (RAG+MCP system)
    ├── Component specification (connector, retrieval, re-ranking, generation)
    └── Security model design (ACL enforcement, SSO)

PHASE 3: Artifact Construction
    ├── MCP-compatible SharePoint connector implementation
    ├── FAISS index construction and optimization
    ├── Streamlit UI and conversational pipeline
    └── Security layer implementation

PHASE 4: Evaluation
    ├── Benchmark dataset construction
    ├── Controlled comparative experiment (LLM vs RAG vs RAG+MCP)
    ├── System performance evaluation (latency, throughput)
    └── User study (usefulness, satisfaction, adoption)

PHASE 5: Analysis and Contribution
    ├── Hypothesis testing
    ├── Results analysis and interpretation
    ├── Design principle extraction
    └── Limitations and future work
```

### 7.3 Evaluation Methodology

#### 7.3.1 Retrieval Evaluation
**Protocol:** Construct a ground-truth dataset of N=50 question-answer pairs from the DNSI SharePoint corpus. For each question, manually annotate the relevant document chunks (ground truth). Measure:

| Metric | Formula | Target |
|--------|---------|--------|
| Precision@K | |Relevant ∩ Retrieved@K| / K | P@5 ≥ 0.70 |
| Recall@K | |Relevant ∩ Retrieved@K| / |Relevant| | R@5 ≥ 0.65 |
| Mean Reciprocal Rank (MRR) | (1/N) Σ (1/rank_i) | MRR ≥ 0.75 |
| nDCG@K | Normalized discounted cumulative gain | nDCG@5 ≥ 0.70 |

**Baselines compared:**
- BM25 (lexical search, no re-ranking)
- Dense retrieval FAISS flat (no re-ranking)
- Dense retrieval FAISS + re-ranking (proposed system)

#### 7.3.2 Generation Evaluation
**Protocol:** For each Q&A pair, generate responses using three conditions: (A) LLM alone, (B) RAG without MCP, (C) RAG+MCP. Evaluate using:

| Metric | Tool | Definition |
|--------|------|-----------|
| Faithfulness | RAGAS framework | Proportion of claims in the response that are grounded in the retrieved context |
| Answer Relevancy | RAGAS | Semantic similarity between response and ground-truth answer |
| Context Precision | RAGAS | Proportion of retrieved context that is relevant to the question |
| Hallucination Rate | Manual annotation | Proportion of responses containing at least one factually incorrect claim |

#### 7.3.3 System Evaluation
**Protocol:** Instrument the pipeline with timing middleware. Measure:

| Metric | Measurement Method |
|--------|-------------------|
| End-to-end latency (P50, P95, P99) | Request timestamps, N=200 queries |
| Retrieval latency | FAISS search timing |
| Generation latency | Mistral AI API response time |
| Throughput (queries/second) | Concurrent load test |

#### 7.3.4 User Evaluation
**Protocol:** Structured usability study with DNSI employees (target N=10 minimum).

- **Instrument:** System Usability Scale (SUS) + Technology Acceptance Model (TAM) questions
- **Task-based evaluation:** 5 realistic business scenarios
- **Comparison condition:** Current SharePoint search vs AntiGravity
- **Metrics:** Task completion rate, time-on-task, SUS score, perceived usefulness, perceived ease of use

### 7.4 Validity and Reliability

| Threat | Type | Mitigation |
|--------|------|-----------|
| Small benchmark dataset (N=50) | Internal validity | Report confidence intervals; acknowledge as limitation |
| Evaluator bias in hallucination annotation | Internal validity | Double annotation with inter-annotator agreement (Cohen's κ) |
| Domain-specific corpus may not generalize | External validity | Discuss generalizability explicitly; suggest replication protocol |
| LLM non-determinism | Reliability | Fix temperature=0 for all generation experiments; report variance |
| Corporate constraints limiting user study size | External validity | Acknowledge; use mixed-methods (quantitative SUS + qualitative interviews) |

---

## 8. POSITIONING RELATIVE TO STATE OF THE ART

### 8.1 What RAG Literature Addresses
- Lewis et al. (2020): foundational RAG architecture — we build on this
- Gao et al. (2024): comprehensive RAG survey — our work is one empirical instantiation
- RAGAS (Es et al., 2023): RAG evaluation framework — we adopt as evaluation tool

### 8.2 What This Thesis Adds (Beyond Existing Literature)

| Dimension | Existing Literature | This Thesis |
|-----------|--------------------|--------------| 
| Data source | Wikipedia, open web, generic QA | Private enterprise SharePoint corpus |
| Protocol layer | Ad-hoc connectors / LangChain | Model Context Protocol (MCP) — standardized |
| Security model | Generally absent | ACL-aware retrieval pipeline |
| Evaluation scope | Retrieval + generation metrics | Retrieval + generation + system + user evaluation |
| Industrial context | Academic benchmarks | Real DNSI production constraints |

### 8.3 Research Gap Being Filled

No published study as of June 2026 has:
1. Evaluated RAG performance on a private SharePoint corpus with ACL enforcement
2. Used MCP as the integration protocol and evaluated its specific contribution
3. Combined retrieval, generation, system, and user evaluation in a single enterprise RAG study

This combination constitutes the primary scientific novelty of the thesis.

---

## 9. ETHICAL CONSIDERATIONS

| Dimension | Consideration | Approach |
|-----------|--------------|----------|
| Data privacy | DNSI business documents may contain confidential information | Anonymize company name if required; use confidentiality agreement (school policy) |
| User study consent | DNSI employees participating in user study | Informed consent; anonymous data collection |
| AI use disclosure | Portions of thesis assisted by Claude (Anthropic) | Declared per Aivancity AI use policy; all analysis and interpretation performed by student |
| Generative AI hallucination | Risk of generating incorrect technical claims | All technical claims cross-referenced against source documents |
| Reproducibility | Benchmark dataset and experiments must be reproducible | Dataset to be included as appendix; experimental conditions fully documented |

---

## 10. THESIS SCOPE AND BOUNDARIES

### In scope
- Design and evaluation of the AntiGravity RAG+MCP system on the DNSI SharePoint corpus
- Comparative evaluation of three conditions: LLM alone, RAG, RAG+MCP
- Retrieval, generation, system, and user evaluation
- Security architecture analysis (ACL enforcement, SSO)
- MCP protocol analysis and justification

### Out of scope
- Training or fine-tuning of the Mistral AI model
- Multi-tenant deployment (thesis focuses on DNSI as a single tenant)
- Real-time document synchronization (SharePoint delta updates)
- Extension to data sources beyond SharePoint (mentioned as future work)
- Production-scale load testing beyond proof-of-concept benchmarks

---

*Phase 2 Research Design complete. Awaiting validation before proceeding to Phase 3 — Table of Contents.*
