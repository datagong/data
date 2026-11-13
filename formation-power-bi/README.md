# Formation Power BI : données du fil rouge

Données **entièrement fictives** de la formation Power BI de DATAGONG : Orlavi, un torréfacteur imaginaire de Lyon qui vend à des professionnels, en ligne et dans trois boutiques, de 2024 à 2026. Entreprise, clients, personnes, produits et codes promo sont inventés ; les villes et les pays d'origine des cafés sont réels. Les adresses de messagerie utilisent le domaine réservé `orlavi.test`, les pages produit le domaine `example.com`.

Fictional data for the DATAGONG Power BI course: Orlavi, an imaginary coffee roaster. Same values in both languages; only labels and the displayed currency differ (euros in French, US dollars in English).

## Arborescence

```
formation-power-bi/
└── 20261110/                          graine du jeu courant
    ├── fr/ et en/
    │   ├── modele/                    tables lues par le projet Power BI (CSV, virgule, point décimal, dates ISO, UTF-8)
    │   ├── cours/                     fichiers remis à l'apprenant, rangés comme sur son poste
    │   └── fichiers-du-cours-module-0.zip / course-files-module-0.zip
```

## Versions figées

Chaque tranche du générateur est figée par une étiquette : `powerbi-m0` pour le module 0. Une adresse qui cite l'étiquette ne change jamais :

`https://raw.githubusercontent.com/datagong/data/powerbi-m0/formation-power-bi/20261110/fr/modele/ventes.csv`

Les fichiers déjà livrés ne sont jamais réécrits par une tranche suivante ; leurs empreintes SHA-256 sont tenues par le générateur. Ne modifiez pas ces fichiers à la main : ils sont produits par un script.
