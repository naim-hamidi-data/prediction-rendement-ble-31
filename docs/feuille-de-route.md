# Feuille de route

Projet : prévision du rendement du blé tendre en Haute-Garonne.
Historique : 2010–2025. Test final indépendant : 2026.

## État actuel

Cadrage initial terminé. Organisation préparée ; ajout sur GitHub à confirmer. Collecte des données non commencée.

## 1. Installer le cadre de travail

- [x] Rédiger le README et le cahier des charges initial.
- [x] Préparer les dossiers et les documents de suivi.
- [ ] Ajouter cette organisation au dépôt GitHub.
- [ ] Noter l’URL du dépôt dans le journal de bord.
- [ ] Ouvrir et enregistrer un premier notebook Google Colab.

Validation : les documents sont accessibles sur GitHub et le notebook s’exécute.

## 2. Auditer les rendements

- [ ] Télécharger la série officielle 2010–2025.
- [ ] Confirmer la catégorie blé tendre, le département 31 et les unités.
- [ ] Vérifier les années manquantes, les révisions et le statut provisoire.
- [ ] Identifier la source du rendement 2026, sans l’utiliser pour choisir le modèle.
- [ ] Documenter les sources et produire le tableau propre.

Validation : 16 campagnes documentées, ou lacunes explicitement signalées.

## 3. Auditer la météo

- [ ] Inventorier les stations représentatives des zones cultivées.
- [ ] Vérifier la couverture depuis l’automne 2009.
- [ ] Vérifier les lacunes et indicateurs de qualité.
- [ ] Définir et documenter l’agrégation spatiale.

Validation : couverture suffisante pour construire les indicateurs retenus.

## 4. Explorer avec Python

- [ ] Lire les données avec pandas et comprendre les colonnes.
- [ ] Harmoniser dates et unités.
- [ ] Tracer les premières séries et repérer les anomalies.
- [ ] Documenter les corrections sans modifier les fichiers bruts.

Validation : expliquer le code et les premiers graphiques.

## 5. Construire les indicateurs

- [ ] Définir les périodes agronomiques et les seuils.
- [ ] Calculer les indicateurs connus au 1er mai.
- [ ] Préparer les variantes au 1er mars et au 1er juin.
- [ ] Vérifier l’absence de météo future et de cible 2026 dans l’apprentissage.

Validation : une ligne par campagne, colonnes et disponibilité documentées.

## 6. Développer et valider

- [ ] Calculer les références : moyenne mobile et tendance.
- [ ] Tester la régression parcimonieuse et Ridge.
- [ ] Valider en avançant dans le temps, sans partage aléatoire.
- [ ] Ajuster les transformations uniquement sur chaque jeu d’entraînement.
- [ ] Comparer MAE, RMSE et erreurs annuelles.
- [ ] Figer les choix avant le test final.

Validation : comparaison reproductible, même si aucun modèle ne dépasse la référence.

## 7. Évaluer 2026

- [ ] Enregistrer les prévisions du modèle figé.
- [ ] Comparer au rendement officiel et préciser son statut.
- [ ] Mesurer les erreurs par échéance et présenter l’incertitude.
- [ ] Distinguer séries révisées et informations réellement publiées à l’époque.

Validation : 2026 n’a influencé aucun choix de développement.

## 8. Présenter et finaliser

- [ ] Produire les graphiques et la synthèse.
- [ ] Rédiger les limites et les conclusions.
- [ ] Ajouter les dépendances et les instructions de reproduction.
- [ ] Mettre à jour le README et présenter le projet dans le portfolio.

## À chaque séance

Un objectif concret, une vérification du résultat, puis une mise à jour du journal de bord. Cocher une tâche seulement quand elle est terminée. Le calendrier sera ajusté à la qualité des données et au rythme d’apprentissage.
