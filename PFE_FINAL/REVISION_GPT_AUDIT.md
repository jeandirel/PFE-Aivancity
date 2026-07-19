# Audit de correction du mémoire

## Source de vérité

Le mémoire doit être réécrit à partir de la stack active du dépôt `jeandirel/PocChatbotM3-clean`, et non à partir des hypothèses du document généré précédemment.

## Stack active vérifiée

- Interface : Streamlit (`services/ui/MistralChat_sharepoint.py`)
- Backend : FastAPI (`services/backend/app/main.py`)
- Orchestration RAG : `services/backend/app/rag_pipeline.py`
- Embeddings : service SentenceTransformers avec `multilingual-e5-large`
- Base vectorielle : Qdrant
- LLM : Mistral Small 3.1 24B Instruct servi par vLLM sur GPU
- Persistance : PostgreSQL en production
- Sources : SharePoint et Freshservice
- Sécurité : authentification Microsoft, métadonnées ACL et filtrage documentaire
- Déploiement : Docker Compose, Nginx hôte, health checks, volumes persistants et service systemd
- Supervision : page Streamlit de monitoring, journalisation des interactions et feedbacks

## Éléments fictifs ou obsolètes à supprimer

- le nom `AntiGravity` ;
- la présentation de MCP comme composant implémenté et évalué ;
- Mistral 7B exécuté sur CPU avec `llama-cpp-python` comme stack active ;
- `all-mpnet-base-v2` comme modèle d'embeddings actif ;
- FAISS comme base vectorielle principale de production ;
- l'architecture à trois services `ingestion worker + MCP server + Streamlit` ;
- les résultats inventés : taux d'hallucination 44 % à 9 %, RAGAS 0,89, SUS 71,8, N=14 utilisateurs, benchmark N=50 et latences détaillées ;
- les affirmations de première publication scientifique ou de preuve formelle de sécurité ;
- les annexes présentant des données expérimentales qui ne sont pas réellement disponibles.

## Positionnement corrigé

Le projet est un assistant conversationnel RAG d'entreprise conçu, industrialisé et déployé pour faciliter l'accès à des connaissances documentaires issues de SharePoint et Freshservice. Sa contribution principale est l'évolution d'un prototype vers une architecture modulaire et exploitable : ingestion documentaire, recherche vectorielle, contrôle d'accès, génération locale, persistance, supervision et déploiement reproductible.

MCP peut être traité dans l'état de l'art ou les perspectives, mais ne doit pas apparaître comme une réalisation actuelle tant qu'aucun serveur/client MCP actif n'est démontré dans le chemin de production.

## Titre recommandé

**Design, Development and Deployment of a Secure Retrieval-Augmented Generation Conversational Assistant for Enterprise Knowledge Access from SharePoint and Freshservice**

## Règle éditoriale

Toute affirmation du mémoire doit être classée dans l'une des catégories suivantes :

1. implémentée et vérifiable dans le code ;
2. mesurée et accompagnée de données brutes ;
3. observée qualitativement et présentée comme telle ;
4. proposée comme perspective, sans être présentée comme réalisée.

Aucun chiffre, test utilisateur, résultat RAGAS, benchmark ou propriété de sécurité ne doit être conservé sans preuve exploitable.