
# TP04 — Comparatif des approches AutoML

Date de consultation : 20/10/2026

## 1. Tableau comparatif

| Approche | F1 test | Temps humain | Temps machine | Coût estimé | Explicabilité | Export / Réversibilité |
|---|---|---|---|---|---|---|
| Régression logistique | 0,7407 (référence TP) | Faible à moyen | Quelques secondes | Calcul local, sans facturation cloud | Élevée : coefficients interprétables | Élevée : modèle Python exportable |
| Random Forest manuel | 0,8669 (référence TP) | Moyen : configuration manuelle | Quelques secondes à minutes | Calcul local, sans facturation cloud | Moyenne à élevée : importance des variables | Élevée : modèle Python exportable |
| FLAML — 60 s | 0,8582 (mesuré) | Faible : configuration AutoML | Budget de 60 s | Calcul local, sans facturation cloud | Variable selon le modèle retenu | Élevée : modèle réutilisable en Python |
| Google Vertex AI AutoML | Non mesuré | Faible à moyen : configuration du service | Variable selon les données et le budget | Payant selon entraînement, calcul et déploiement | Explications et importance des variables selon le modèle | Export possible sous conditions |
| Amazon SageMaker Autopilot | Non mesuré | Faible à moyen : configuration du service | Variable selon les ressources | Payant selon instances, stockage et déploiement | Rapports et explications de modèles | Artefacts et modèles récupérables selon le type |
| Azure Automated ML | Non mesuré | Faible à moyen : configuration du service | Variable selon les ressources | Payant selon calcul, stockage et déploiement | Importance des variables et outils d'interprétabilité | Export et réutilisation possibles selon le modèle |

**Remarque :** les F1 des deux modèles manuels proviennent du sujet du TP et doivent être remplacés si les résultats réellement mesurés sont différents. Le F1 FLAML provient de notre expérimentation.

## 2. Analyse comparative — 5 lignes

1. La régression logistique convient aux problèmes simples nécessitant une forte interprétabilité.
2. Le Random Forest manuel est pertinent lorsque le Data Scientist souhaite contrôler directement les paramètres du modèle.
3. FLAML est adapté au prototypage rapide et à l'optimisation automatique sur une machine locale avec un budget de calcul limité.
4. Google Vertex AI et Amazon SageMaker Autopilot conviennent aux entreprises disposant d'une infrastructure cloud et souhaitant automatiser l'entraînement et le déploiement.
5. Azure Automated ML est particulièrement pertinent dans un environnement utilisant déjà les services Microsoft Azure, avec des besoins de traçabilité et de gestion des modèles.

## 3. Conclusion

Dans notre expérimentation, le Random Forest manuel obtient un F1 de 0,8669 (valeur de référence du TP), contre 0,8582 pour FLAML avec un budget de 60 secondes.

Cette différence ne signifie pas que l'AutoML est inutile : FLAML automatise la recherche de modèles et d'hyperparamètres, ce qui réduit les interventions manuelles.

Les plateformes cloud proposent des services supplémentaires pour la gestion des ressources, l'entraînement et le déploiement, mais elles nécessitent une analyse des coûts et des contraintes de réversibilité.

## 4. Sources officielles

- Google Vertex AI — Tarification :
  https://cloud.google.com/vertex-ai/pricing

- Google Vertex AI — Documentation :
  https://cloud.google.com/vertex-ai/docs

- AWS SageMaker — Tarification :
  https://aws.amazon.com/sagemaker/pricing/

- AWS SageMaker Autopilot — Documentation :
  https://docs.aws.amazon.com/sagemaker/latest/dg/autopilot-automate-model-development.html

- Azure Machine Learning — Tarification :
  https://azure.microsoft.com/en-us/pricing/details/machine-learning/

- Azure Automated ML — Documentation :
  https://learn.microsoft.com/en-us/azure/machine-learning/concept-automated-ml
