# Mémoire PFE - Version 2

Cette arborescence contient la réécriture contrôlée du mémoire de Jean Direl NZE.

## Sources de vérité

1. `jeandirel/PocChatbotM3-clean` pour l'implémentation, les configurations et le déploiement réels.
2. Les consignes Aivancity présentes dans le dépôt du mémoire.
3. Les sources scientifiques et documentations officielles vérifiées.
4. Le mémoire V1 uniquement pour récupérer les éléments confirmés.

## Règles de rédaction

- aucune fonctionnalité non démontrée dans le projet ne doit être présentée comme réalisée ;
- aucune métrique ne doit être publiée sans résultat traçable ;
- les composants historiques ou legacy doivent être explicitement distingués de la stack active ;
- les perspectives ne doivent jamais être décrites au passé ;
- les informations sensibles doivent être anonymisées.

## Organisation des chapitres

Les chapitres volumineux peuvent être divisés en sous-fichiers LaTeX afin de faciliter leur audit et leur maintenance. Le fichier principal du chapitre conserve les commandes `\input` nécessaires à la compilation.

## État d'avancement

- Chapitre 1 — Contexte organisationnel, besoin métier et problématique : **terminé**.
- Chapitre 2 — État de l'art et fondements techniques de l'Assistant RAG DNSI : **terminé**.
  - recherche lexicale, Transformer, embeddings et `multilingual-e5-large` ;
  - RAG, réécriture de requête, reranking hybride et limites du grounding ;
  - Qdrant, payloads, filtrage ACL, Mistral Small 3.1 24B et vLLM ;
  - SharePoint, Microsoft Graph, Freshservice, RGPD, AI Act et évaluation RAG.
- Chapitre 3 — Méthodologie et démarche projet : **terminé**.
  - Design Science Research adaptée au contexte d'entreprise ;
  - hiérarchie des preuves et traçabilité des affirmations ;
  - phases de cadrage, préparation documentaire, prototypage, industrialisation, sécurité et déploiement ;
  - critères ISO/IEC 25010, stratégie de validation et tests disponibles ;
  - reproductibilité, gestion des risques et menaces à la validité.
- Chapitre 4 — Analyse des besoins et spécifications : **terminé**.
  - périmètre, parties prenantes et dix cas d'usage principaux ;
  - quinze exigences fonctionnelles et exigences relatives aux données ;
  - quatorze exigences non fonctionnelles assorties de critères de vérification ;
  - contrats d'interface entre Streamlit, FastAPI, embeddings, Qdrant, vLLM et PostgreSQL ;
  - critères d'acceptation et matrice de traçabilité vers le code et les tests.

## Éléments explicitement exclus sans nouvelle preuve

- AntiGravity comme nom du produit ;
- MCP comme composant de production ;
- Mistral 7B sur CPU comme modèle actif ;
- `all-mpnet-base-v2` comme modèle d'embeddings actif ;
- FAISS comme base vectorielle principale ;
- métriques, enquêtes ou tests statistiques sans résultats traçables.
