# Comparison of Sport Event Timelines from Social Media

Analyse automatique des événements sportifs à partir des réseaux sociaux, des médias numériques et des données officielles de match.

Projet réalisé dans le cadre du module de **Traitement Automatique du Langage Naturel (TAL)** — Master 1, Algorithmique et Systèmes Intelligents — Année universitaire 2025–2026.

## Équipe

**Encadrement**
- Pr. Marc Spaniol
- Pr. Alexandre Niveau

## Résumé du projet

Ce projet étudie dans quelle mesure les réactions publiées en ligne permettent de reconstruire, d'analyser et de comparer les moments importants d'un match de football. Il combine trois axes complémentaires :

1. **Analyse des données** — collecte et exploration de commentaires Reddit, d'articles de presse et de fichiers de match officiels, centrée sur le match **Galatasaray vs Liverpool**, puis élargie à un corpus multi-match (5 rencontres).
2. **Traitement Automatique du Langage naturel (TAL)** — nettoyage des textes, détection d'événements sportifs par règles puis par classification supervisée (TF-IDF + régression logistique), extraction de scores, construction d'une timeline sociale.
3. **Analyse de sentiment** — évolution émotionnelle des commentaires autour des événements clés du match, modélisation par régression logistique, forêt aléatoire et gradient boosting, comparaison des timelines sociale / médiatique / officielle.

## Structure du dépôt

```
.
├── data/               # Données brutes et intermédiaires (Reddit, articles, fichiers de match)
├── notebooks/          # Notebooks d'exploration et d'analyse
├── src/                # Scripts de traitement (nettoyage, TAL, sentiment, timelines)
├── figures/            # Figures générées pour le rapport
├── report/             # Rapport LaTeX complet
└── README.md
```

*(À adapter selon l'organisation réelle du dépôt.)*

## Données utilisées

**Corpus Galatasaray vs Liverpool**
- 200 publications Reddit analysées
- 46 416 commentaires parcourus
- 1 228 commentaires associés aux fenêtres temporelles du match
- 100 articles de presse
- 90 lignes de résultats issues de la chaîne TAL

**Corpus multi-match (5 rencontres)**
- Atlético Madrid vs Inter Milan
- Real Madrid vs Manchester City
- Arsenal vs PSG
- Barcelona vs Bayer Leverkusen
- Liverpool vs Galatasaray

## Méthodologie

1. Collecte des données (Reddit, médias, fichiers de match)
2. Nettoyage et normalisation des textes
3. Association des commentaires aux périodes du match (00:00 → 90:00)
4. Détection TAL des événements sportifs (règles + TF-IDF + régression logistique)
5. Analyse de sentiment et signaux temporels (modèle `cardiffnlp/twitter-roberta-base-sentiment-latest`)
6. Construction des timelines sociale et médiatique
7. Comparaison avec la timeline officielle

## Principaux résultats

- Taux de correspondance commentaires/fenêtres du match : **~2,65 %**
- Classification des titres (TF-IDF + régression logistique) : accuracy **0,889** (version 1)
- Analyse de sentiment sur les titres : 79 positifs / 11 négatifs
- Analyse de sentiment sur les commentaires : 873 négatifs (71,1 %) / 355 positifs (28,9 %)
- Détection d'événements à partir de signaux temporels (comparaison de modèles) :

| Modèle | F1-macro moyen | ROC-AUC moyen |
|---|---|---|
| Régression logistique | 0,433 | 0,750 |
| Forêt aléatoire | 0,583 | 0,650 |
| Gradient Boosting | **0,720** | **0,825** |

Le Gradient Boosting obtient les meilleurs résultats moyens pour la détection des fenêtres événementielles.

## Conclusion

Les réseaux sociaux produisent une réaction rapide, émotionnelle et fortement liée au déroulement du match, tandis que les médias fournissent une information plus structurée. Le projet met en évidence la complémentarité entre sources sociales, médiatiques et officielles pour reconstruire une chronologie sportive enrichie.

## Limites et perspectives

- Corpus de titres TAL limité et classes déséquilibrées
- Règles linguistiques sensibles aux formulations ambiguës (ex. faux positifs sur "VAR" dans "Vardy")
- Perspectives : enrichir le corpus avec davantage de matchs, améliorer la collecte Reddit, utiliser des modèles multilingues, entraîner un modèle supervisé de détection d'événements plus robuste

## Rapport complet

Le rapport détaillé (méthodologie, figures, tableaux) est disponible dans le dossier `report/` au format LaTeX/PDF.

## Dépôt GitHub

[https://github.com/britek2001/Comparaison_of_Sport_Event_Timeline.git](https://github.com/britek2001/Comparaison_of_Sport_Event_Timeline.git)

## Mots-clés

réseaux sociaux, football, chronologie sportive, TAL, analyse de sentiment, Reddit, médias, détection d'événements
