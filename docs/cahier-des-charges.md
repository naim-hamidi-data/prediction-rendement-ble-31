# Fiche projet — Cahier des charges initial

**Prévision du rendement du blé tendre en Haute-Garonne : apprentissage sur 2010–2025 et évaluation sur 2026**

Version 0.1 — 4 octobre 2026 — Porteur : Naïm Hamidi

## 1. Contexte et finalité

Ce projet prépare l’entrée en master DigitalAgri par la réalisation d’une chaîne complète d’analyse agricole avec Python : collecte, nettoyage, exploration, modélisation, validation et visualisation. Il vise à déterminer si les informations disponibles avant la récolte auraient permis d’anticiper le rendement départemental du blé tendre en 2026.

## 2. Problématique

Un modèle développé sur les campagnes 2010–2025 permet-il de prévoir le rendement moyen du blé tendre en Haute-Garonne en 2026 mieux qu’une référence simple ? À quelle échéance la prévision devient-elle utile ?

L’analyse examinera le rôle prédictif des précipitations et des températures. Elle ne prétendra pas attribuer causalement une perte de rendement à la sécheresse.

## 3. Périmètre et cible

- Territoire : Haute-Garonne, département 31.
- Culture : blé tendre, choix initial à confirmer par la disponibilité des séries et les informations locales sur l’irrigation.
- Variable cible : rendement moyen départemental, exprimé en q/ha.
- Historique de développement : campagnes 2010 à 2025 incluses.
- Test final : campagne 2026, tenue à l’écart de la sélection des variables et des modèles.
- Échéance principale proposée : 1er mai ; analyses secondaires : 1er mars et 1er juin.
- Le modèle départemental ne prédit pas directement le rendement d’une parcelle.

## 4. Données et audit préalable

| Données | Source envisagée | Contrôles nécessaires |
|---|---|---|
| Rendement, surface, production 2010–2025 | Agreste / DRAAF Occitanie | Unités, catégorie de culture, données provisoires, révisions et continuité |
| Rendement 2026 | Publication départementale officielle à identifier | Source, périmètre, date de publication et statut provisoire ou définitif |
| Pluie et températures quotidiennes | Météo-France | Stations, localisation, couverture 2009–2026, lacunes et indicateurs de qualité |
| Irrigation et répartition des cultures | Sources agricoles officielles | Représentativité des stations et interprétation du rendement agrégé |

Les données météo de l’automne 2009 peuvent être nécessaires pour la campagne 2010. Le calendrier des indicateurs sera défini selon le cycle cultural, sans assimiler une campagne à une année civile.

Deux niveaux seront distingués : un test utilisant les séries aujourd’hui révisées, puis, si les archives le permettent, une reconstitution des informations réellement publiées à chaque échéance. Une donnée provisoire 2025 publiée après une échéance de prévision 2026 ne sera pas présentée comme connue à cette échéance.

## 5. Méthode prévue

1. Télécharger les sources, conserver les fichiers bruts et documenter leur provenance.
2. Nettoyer les données, harmoniser les unités et constituer une table avec une ligne par campagne.
3. Sélectionner des stations représentatives des zones de culture et documenter leur agrégation ; éviter une moyenne indifférenciée incluant les zones de montagne.
4. Construire un petit nombre d’indicateurs agronomiques : pluie cumulée par période, températures, jours chauds et séquences sans pluie. Les fenêtres et seuils seront justifiés avant le test 2026.
5. Explorer les séries et la tendance de rendement sans utiliser 2026 pour orienter les choix.
6. Comparer une moyenne mobile sur cinq campagnes et une tendance temporelle simple à une régression parcimonieuse et une régression Ridge.
7. Choisir le modèle d’après ses performances historiques, le figer et produire les estimations 2026.

À chaque échéance, les variables utiliseront uniquement des observations antérieures. L’emploi éventuel de météo prévisionnelle exigera des prévisions archivées disponibles à l’époque. Une analyse utilisant la météo complète de la campagne sera identifiée séparément comme une estimation rétrospective.

## 6. Validation et prévention des biais

La validation suivra l’ordre du temps : entraînement initial proposé sur 2010–2017, prévision de 2018, puis extension annuelle jusqu’au test de 2025. Le nombre exact de découpages sera confirmé après l’audit.

Les traitements appris sur les données — imputation, standardisation, tendance, sélection et réglage des modèles — seront ajustés uniquement sur les années d’entraînement de chaque découpage. Aucun partage aléatoire des campagnes ne sera utilisé. Les réglages resteront limités et, si nécessaire, évalués dans une validation temporelle interne.

Les mesures principales seront l’erreur absolue moyenne (MAE) et la RMSE, en q/ha, complétées par les erreurs année par année et la comparaison aux références. L’incertitude sera estimée si les données le permettent, avec ses limites explicitées ; aucun niveau de précision ne sera garanti à l’avance.

## 7. Livrables

- Un dictionnaire des données et une documentation des sources.
- Les données préparées et un notebook Python pédagogique reproductible.
- Une chaîne de préparation, entraînement et prévision réutilisable.
- Des graphiques : rendements historiques, observations/prévisions, erreurs et résultats 2026 par échéance.
- Un tableau comparatif des modèles et des références.
- Une synthèse présentant les résultats, l’incertitude et les limites.
- Un README permettant de reproduire le projet et de le présenter dans un portfolio.

Outils envisagés : Python, pandas, matplotlib ou seaborn, scikit-learn et Jupyter. Les versions et dépendances seront fixées lors de l’implémentation.

## 8. Critères de réussite et limites

Le projet sera réussi si les sources sont traçables, les calculs reproductibles, la validation temporelle respectée et les résultats interprétés honnêtement. Conclure que le modèle météo ne fait pas mieux que la référence constitue un résultat valable.

Les 16 campagnes historiques offrent peu d’observations indépendantes. Les sols, variétés, pratiques, maladies et changements de localisation des cultures peuvent influencer le rendement sans être observés. Le manque de pluie n’est pas, seul, une mesure complète de sécheresse agricole.

Une extension à des départements comparables pourra être étudiée si nécessaire. Elle constituera une seconde phase documentée, avec séparation des années entre entraînement et test, sans inclure aucune donnée de rendement 2026 pendant le développement.

## 9. Prochaine étape

Auditer les données : récupérer les rendements 2010–2025, identifier le résultat départemental 2026 et inventorier les stations météo. Cet audit confirmera le périmètre avant la programmation du modèle.

## Ressources de départ

- Séries COP 2010–2025 : https://draaf.occitanie.agriculture.gouv.fr/cop-surfaces-rendements-et-productions-de-2010-a-2025-par-departement-d-a8145.html
- Pratiques culturales des céréales à paille : https://draaf.occitanie.agriculture.gouv.fr/les-pratiques-culturales-pour-les-cereales-a-paille-agreste-etudes-no4-juin-a10022.html
- Données météo quotidiennes : https://www.data.gouv.fr/datasets/donnees-climatologiques-de-base-quotidiennes

Ces ressources constituent des points d’entrée ; les fichiers précis et leurs métadonnées seront vérifiés pendant l’audit.
