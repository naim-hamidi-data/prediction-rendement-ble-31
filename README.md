Prévision du rendement du blé tendre en Haute-Garonne
Apprentissage sur les campagnes 2010–2025 · Évaluation indépendante sur 2026
Aurait-on pu prévoir le rendement du blé tendre récolté en Haute-Garonne en 2026 à partir des informations disponibles avant la récolte ?

Ce projet explore cette question en croisant des données agricoles et météorologiques avec Python. Il vise à construire une chaîne reproductible, depuis la collecte des données jusqu’à l’évaluation des prévisions et à la visualisation des résultats.
Statut : projet en cours de cadrage et de collecte. Aucun modèle entraîné ni résultat de performance disponible à ce stade.
Objectifs
- Analyser l’évolution des rendements du blé tendre en Haute-Garonne.
- Construire des indicateurs de précipitations et de température pertinents pour le cycle de la culture.
- Comparer des modèles prédictifs à des références simples.
- Évaluer leur capacité à anticiper le rendement 2026 à plusieurs dates avant la récolte.
- Présenter les résultats, leur incertitude et leurs limites de manière accessible.
Ce travail constitue également un projet d’apprentissage de Python en préparation du master DigitalAgri.
Périmètre
Élément	Choix initial
Territoire	Haute-Garonne — département 31
Culture	Blé tendre
Cible	Rendement moyen départemental en quintaux par hectare (q/ha)
Historique de développement	2010–2025
Campagne de test final	2026
Échéance principale proposée	1er mai
Échéances complémentaires	1er mars et 1er juin


Le blé tendre est retenu comme culture de départ pour étudier une production relativement peu irriguée. La situation locale et la disponibilité des données seront vérifiées pendant l’audit. Le rendement départemental peut inclure des surfaces irriguées et non irriguées.
Données envisagées
Données	Source envisagée	Utilisation
Rendements, surfaces et productions	Agreste / DRAAF Occitanie	Historique agricole et variable à prédire
Précipitations et températures quotidiennes	Météo-France	Construction des indicateurs météo
Rendement départemental 2026	Publication officielle à identifier	Évaluation finale
Informations sur l’irrigation et les zones cultivées	Sources agricoles officielles	Interprétation et représentativité géographique


Les sources exactes, dates de publication, unités, licences et éventuelles révisions seront documentées. Les observations de l’automne 2009 pourront être nécessaires pour décrire la campagne 2010.
Points d’entrée :
- Séries départementales COP 2010–2025 — DRAAF Occitanie
- Données climatologiques quotidiennes — Météo-France
Méthode prévue
1. Collecter et auditer les données : couverture temporelle, unités, lacunes et cohérence des séries.
2. Préparer les données : nettoyer les tableaux, sélectionner des stations représentatives et associer la météo aux campagnes agricoles.
3. Construire les indicateurs : cumuls de pluie, températures, jours chauds et séquences sans pluie sur des périodes agronomiques justifiées.
4. Explorer les relations : visualiser les évolutions et les associations entre météo et rendement.
5. Comparer les approches : moyenne des cinq dernières campagnes, tendance temporelle, régression parcimonieuse et régression Ridge.
6. Valider sur les années historiques : apprendre sur les années précédentes et prévoir l’année suivante, avec une fenêtre d’entraînement croissante.
7. Figer le modèle et tester 2026 : produire les prévisions, puis les comparer au rendement observé.
Respecter les informations disponibles à chaque date
Une prévision simulée au 1er mai utilisera uniquement des informations disponibles avant cette échéance. La météo observée ultérieurement sera exclue. L’emploi éventuel de prévisions météo nécessitera des archives correspondant aux prévisions réellement disponibles à l’époque.
Le rendement 2026 ne servira ni à choisir les variables, ni à régler les modèles. Les traitements appris sur les données, comme la standardisation ou l’imputation, seront ajustés uniquement sur les années d’entraînement de chaque découpage.
Un test utilisant les séries aujourd’hui révisées sera distingué d’une reconstitution stricte des informations publiées à l’époque. Cette seconde approche dépendra de la disponibilité des archives.
Évaluation et visualisations
Les modèles seront évalués avec l’erreur absolue moyenne (MAE) et la racine de l’erreur quadratique moyenne (RMSE), exprimées en q/ha. Les erreurs année par année et le gain éventuel par rapport aux références seront également présentés.
Visualisations prévues :
- Évolution des rendements et des indicateurs météo.
- Comparaison entre rendements observés et prévus.
- Erreurs de prévision par campagne.
- Comparaison des modèles et des échéances.
- Résultats 2026 accompagnés d’une estimation de l’incertitude, si les données le permettent.
Limites
L’historique 2010–2025 représente seulement 16 observations annuelles de rendement. Les nombreuses mesures météo ne constituent pas autant de campagnes indépendantes. Le nombre de variables et la complexité des modèles devront donc rester limités.
Les sols, variétés, pratiques, maladies et changements de répartition des cultures peuvent aussi influencer les rendements. Une association météo–rendement ne démontre pas une perte causée exclusivement par la sécheresse, et un déficit de pluie ne décrit pas à lui seul la sécheresse agricole.
Le modèle vise une moyenne départementale, pas le rendement d’une parcelle. Une extension à des départements comparables pourra être étudiée dans une seconde phase.
Organisation prévue du dépôt
prediction-rendement-ble-31/
├── README.md
├── docs/                  # Cahier des charges et documentation
├── data/
│   ├── raw/               # Données brutes partageables
│   └── processed/         # Données préparées
├── notebooks/             # Analyse expliquée étape par étape
├── src/                   # Fonctions et scripts réutilisables
├── results/               # Graphiques et tableaux de résultats
└── requirements.txt       # Dépendances Python
Cette arborescence sera créée au fur et à mesure. Les fichiers volumineux ou non redistribuables resteront hors du dépôt ; leur récupération sera documentée.
Outils envisagés
Python, pandas, matplotlib ou seaborn, scikit-learn et Jupyter / Google Colab. Les instructions d’exécution et les versions des dépendances seront ajoutées avec les premiers notebooks.
Avancement
- [x] Définir la problématique et le périmètre initial.
- [x] Rédiger une première fiche projet.
- [ ] Vérifier et récupérer les rendements 2010–2025.
- [ ] Identifier la source du rendement départemental 2026.
- [ ] Auditer les stations et les données météo.
- [ ] Préparer les données et réaliser l’analyse exploratoire.
- [ ] Développer et valider les modèles.
- [ ] Réaliser le test final sur 2026.
- [ ] Publier les résultats et leurs limites.
Auteur
Naïm Hamidi — Ingénieur agronome, agriculture numérique, data et SIG
Portfolio · GitHub
Favoriser l’autonomie des acteurs du monde agricole et encourager le choix plutôt que la dépendance.
