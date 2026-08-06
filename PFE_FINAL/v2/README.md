# Mémoire PFE - Version 2 finalisée

Cette arborescence contient la réécriture contrôlée du mémoire de Jean Direl NZE consacrée à l'**Assistant RAG DNSI**.

## Sources de vérité

1. `jeandirel/PocChatbotM3-clean` pour l'implémentation, les configurations et le déploiement réels.
2. Les consignes Aivancity présentes dans le dépôt du mémoire.
3. Les publications scientifiques et documentations officielles vérifiées.
4. Le mémoire V1 uniquement pour récupérer les éléments confirmés.

## Règles de rédaction

- aucune fonctionnalité non démontrée dans le projet n'est présentée comme réalisée ;
- aucune métrique n'est publiée sans résultat traçable ;
- les composants historiques ou legacy sont distingués de la stack active ;
- une perspective n'est jamais décrite comme une réalisation ;
- les informations sensibles doivent être anonymisées ;
- le code actif et `docker-compose.prod.yml` priment sur les documents historiques.

## État des chapitres

1. Contexte organisationnel, besoin métier et problématique - **terminé**.
2. État de l'art et fondements techniques - **terminé**.
3. Méthodologie et démarche projet - **terminé**.
4. Analyse des besoins et spécifications - **terminé**.
5. Architecture de la solution - **terminé**.
6. Implémentation de la solution - **terminé**.
7. Évaluation, résultats traçables et discussion - **terminé**.
8. Conclusion générale, limites et perspectives - **terminé**.

## Compilation

Le fichier `main.tex` assemble les huit chapitres et les huit bibliographies :

```bash
cd PFE_FINAL/v2
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex
```

## Positionnement de la version finale

La V2 décrit la stack active : Streamlit, FastAPI, `multilingual-e5-large`, Qdrant, vLLM, Mistral Small 3.1 24B, PostgreSQL, Nginx, SharePoint et Freshservice.

Le chapitre 7 distingue explicitement :

- les mécanismes confirmés dans le code ;
- les 66 fonctions de test présentes ;
- les tests dont l'exécution n'est pas archivée ;
- les métriques qui restent à produire.

Les notes d'audit sur les composants historiques sont conservées dans ce README et dans l'historique Git, pas dans le corps académique du mémoire.
