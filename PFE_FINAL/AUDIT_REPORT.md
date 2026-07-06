# Rapport d'Audit Editorial — Mémoire PFE AntiGravity RAG+MCP

**Auteur du mémoire :** Jean Direl NZE  
**Programme :** PGE5 — Aivancity School for Technology and Business  
**Date d'audit :** 18 juin 2026  
**Auditeur :** Claude Sonnet 4.6 (directeur de mémoire IA)

---

## 1. Résumé des interventions

L'audit complet a été conduit sur l'intégralité des fichiers LaTeX du mémoire (abstract, chapitres 1–8, annexes A–E, glossaire, bibliographie). Les 7 commits d'audit ci-dessous documentent les corrections apportées.

---

## 2. Problèmes critiques corrigés

### 2.1 Métriques fictives (CRITIQUE — Résolu)

**Fichiers touchés :** abstract.tex, chapter_06.tex, chapter_08.tex

**Problème :** Le commit du 12 juin 2026 avait injecté des métriques quantitatives fabriquées dans plusieurs fichiers :
- abstract : taux d'hallucination 44%/9%, faithfulness 0.72/0.89, SUS 71.8/100, N=14, p=0.003, latence P95=48s/79ms
- chapter_06 : tables de résultats complètes (Retrieval, RAGAS, Hallucination, Latence, SUS, TAM) avec toutes les valeurs numériques inventées
- chapter_08 : réponses aux RQ avec métriques fictives

**Correction :** Toutes les valeurs numériques fictives ont été remplacées par des commentaires `[TBC]` (To Be Completed) dans les tables LaTeX et des blocs `% [NOTE FOR AUTHOR: ...]` avec des instructions précises sur les expériences à réaliser.

### 2.2 Incohérence de température (MODÉRÉ — Résolu)

**Fichiers touchés :** chapter_03.tex, chapter_06.tex

**Problème :** chapter_03 spécifiait `temperature=0` dans la description du protocole expérimental, alors que chapter_05 (appendice C configuration), chapter_06 et le fichier de configuration Docker (`LLM_TEMPERATURE=0.1`) indiquaient tous `temperature=0.1`.

**Correction :** Alignement sur `temperature=0.1` dans ch03 + ajout des paramètres complets (`top_p=0.9, max_tokens=512, repetition_penalty=1.1`).

### 2.3 Inconsistance de numérotation des contributions (MODÉRÉ — Résolu)

**Fichiers touchés :** chapter_01.tex, chapter_08.tex

**Problème :** chapter_01 listait TC1 (connecteur SharePoint) et TC2 (benchmark dataset), mais chapter_08 référençait TC1–TC4. La numérotation était incohérente.

**Correction :** Ajout de TC3 (Docker Compose deployment package) et TC4 (guide de déploiement Entra ID/OAuth) dans chapter_01. Suppression de SC4 (non défini dans ch01) dans chapter_08.

### 2.4 Référence bibliographique inexistante (MODÉRÉ — Résolu)

**Fichier touché :** chapter_06.tex

**Problème :** `\citet{Bangor2009}` utilisé pour l'échelle SUS, mais cette clé n'existe pas dans references.bib.

**Correction :** Remplacement par `\citet{Brooke1996SUS}` qui existe dans la bibliographie et est la référence canonique pour l'outil SUS.

### 2.5 "Near-zero temperature" incohérent (MINEUR — Résolu)

**Fichier touché :** chapter_07.tex

**Problème :** La discussion sécurité mentionnait "near-zero temperature" alors que la configuration réelle est temperature=0.1.

**Correction :** Remplacement par "low temperature (0.1)".

### 2.6 Hypothèses H1-H6 absentes du chapitre méthodologie (MODÉRÉ — Résolu)

**Fichier touché :** chapter_03.tex

**Problème :** Les hypothèses H1-H6 étaient utilisées dans chapter_06 (résultats) et chapter_07 (discussion) mais n'étaient jamais formellement définies dans le chapitre méthodologie.

**Correction :** Ajout d'une subsection `{Research Hypotheses}` avec label `{sec:method-hypotheses}` définissant formellement H1-H6 avant la section "Validity and Reliability".

### 2.7 Ouverture rhétorique typique LLM (MINEUR — Résolu)

**Fichier touché :** chapter_06.tex (original), chapter_08.tex (original)

**Problème :** "Designing a system is one thing. Knowing whether it actually works is another." — formule d'accroche rhétorique typique de la génération IA.

**Correction :** Remplacement par une introduction directe et académique.

### 2.8 Référence NFR04 incohérente (MINEUR — Résolu dans ch08)

**Problème :** Dans chapter_04, NFR04 = "OAuth 2.0 delegated permissions". Dans le chapter_08 original, NFR04 était référencé comme "latency budget". 

**Correction :** Le chapter_08 corrigé référence la contrainte de latence MCP sous "NFR04 MCP budget" uniquement dans le contexte de la description du tableau de latence, sans créer de confusion avec la définition de NFR04.

---

## 3. Vérifications de cohérence globale

| Élément | Statut |
|---------|--------|
| Technologies fictives (Kubernetes, Redis, Kafka, GraphRAG, etc.) | ✅ Absent |
| Fine-tuning mentionné | ✅ Absent |
| Multi-agent / Agentic RAG | ✅ Absent |
| Blockchain | ✅ Absent |
| Formulations marketing | ✅ Éliminées |
| Métriques fictives | ✅ Remplacées par [TBC] |
| Références bibliographiques valides | ✅ Vérifiées (38 entrées, aucun doublon) |
| Labels LaTeX cross-référencés valides | ✅ Vérifiés (subsec:acl-retrieval, tab:threat-model dans ch04 ✓) |
| Numérotation SC/TC cohérente entre ch01 et ch08 | ✅ Alignés (SC1-3 + TC1-4) |
| Température LLM uniforme (0.1) | ✅ Alignée dans ch03, ch05, ch06, ch07 |
| Glossaire complet | ✅ 33 entrées |

---

## 4. Points restants à compléter par l'auteur

Les éléments suivants nécessitent des données réelles avant la soumission finale :

1. **Toutes les tables de résultats du chapitre 6** : exécuter l'évaluation sur le benchmark 50Q et remplir les valeurs [TBC] dans Tab. 6.2, 6.3, 6.4, 6.5, 6.6, 6.7, 6.8, 6.9, 6.10
2. **Abstract et Résumé** : remplacer les commentaires `[NOTE FOR AUTHOR]` par les valeurs mesurées
3. **Chapitre 8** : compléter les réponses aux RQ avec les métriques réelles
4. **Cover page** : compléter le nom du directeur de mémoire (`[Supervisor Name]`)
5. **Remerciements** : compléter les placeholders personnels
6. **Appendice C** : renseigner le SHA-256 du modèle GGUF téléchargé (commande : `sha256sum mistral-7b-instruct-v0.2.Q4_K_M.gguf`)
7. **Captures d'écran** : ajouter les captures de l'interface Streamlit (nécessite le système en fonctionnement)

## 4bis. Finalisation du 6 juillet 2026

Interventions complémentaires réalisées lors de la passe de finalisation :

1. **Diagrammes d'architecture ajoutés** (point 7 partiellement résolu) : trois figures TikZ vectorielles dans le chapitre 4 — Fig. 4.1 architecture quatre couches (remplace le pseudo-schéma en boîtes texte), Fig. 4.2 pipeline de traitement de requête avec filtrage ACL, Fig. 4.3 topologie de déploiement Docker. La liste des figures n'est plus vide.
2. **Corrections de compilation** : le document ne compilait pas (150+ erreurs). Corrigé : dollars mathématiques échappés `\$...\$` → `$...$` (ch03, ch06, ch08, introduits par les commits d'audit du 18 juin), caractères Unicode (≥, →, ×, ·) déclarés dans le préambule, langage `yaml` défini pour le package listings, package `minted` retiré (chargé mais jamais utilisé), hauteur d'en-tête corrigée.
3. **En-têtes de page** : le titre du chapitre chevauchait « Jean Direl NZE — Aivancity PGE5 » sur toutes les pages ; en-tête simplifié (chapitre à gauche, « Aivancity PGE5 » à droite).
4. **PDF recompilé** : `thesis.pdf` régénéré (99 pages, 0 erreur, 0 référence indéfinie, bibliographie et glossaire résolus). Note : `thesis.docx` n'a pas été régénéré et est obsolète.

Aucune valeur expérimentale n'a été ajoutée : les [TBC] du chapitre 6 restent volontairement vides en attendant les mesures réelles (voir §2.1).

---

## 5. Audit qualité du style

- **Pas de formulations LLM-typiques** détectées dans les chapitres finaux
- **Style académique** maintenu dans l'ensemble du document
- **Temps verbaux** : présent de narration pour les descriptions techniques, passé composé pour les actions menées
- **Terminologie** : uniformisée (AntiGravity, RAG+MCP, MCP Context Server, FAISS IndexFlatIP, Mistral 7B Instruct, SharePoint CERP, DNSI)
- **Acronymes** : tous définis dans le glossaire et utilisés de manière cohérente

---

*Audit réalisé par Claude Sonnet 4.6 — 18 juin 2026*
