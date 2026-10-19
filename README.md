# Modélisation de données environnementales en XML

Projet universitaire de **Données semi-structurées et XML** (Licence 3 Informatique, Université de Tours).

Il modélise en XML des données de suivi de la biodiversité : des **espèces animales et végétales**, leurs **lieux d'observation**, les **années de recensement** et le **nombre d'individus** observés. Deux structures XML différentes sont étudiées, chacune validée par un **DTD** et par un **schéma XML (XSD)**.

## Contenu du dépôt

```
├── Data.txt
├── structure1/
│   ├── donnees.xml        # Document XML (structure 1)
│   ├── miniprojet.dtd     # Validation par DTD
├── structure2/
│   ├── donnees.xml        # Document XML (structure 2)
│   └── ...xsd             # Validation XML Schema
└── README.md
```

## Modèle de données

Le document est organisé par espèce, puis par lieu, puis par observation :

```
mini_projet
└── especes
    └── espece (id)
        ├── type            (plante | animal)
        ├── nom
        ├── description
        └── les_lieux
            └── lieu (id)
                ├── nom
                ├── pays
                └── observations
                    └── observation
                        ├── annee
                        └── nb_individu
```

### Espèces étudiées

| Type    | Espèce                          | Lieux d'observation                    |
|---------|---------------------------------|----------------------------------------|
| Plante  | Paphiopedilum villosum          | Chiang Mai, Doi Inthanon (Thaïlande)   |
| Plante  | Staurogyne bicolor              | Mont Koupé, Monts Bakossi (Cameroun)   |
| Animal  | Éléphant d'Afrique              | Niokolo-Koba (Sénégal), Zakouma (Tchad)|
| Animal  | Gorille des plaines de l'Ouest  | Odzala-Kokoua (Congo), Loango (Gabon)  |

Chaque lieu comporte quatre observations annuelles (2021–2024 pour les plantes, 2022–2025 pour les animaux).

## Validation

### Avec le schéma XSD

Le schéma est écrit en style **Declaration Global** : tous les éléments sont déclarés globalement et assemblés avec `ref`, et les types complexes sont nommés. Les identifiants `id` des espèces et des lieux sont de type `xs:ID`.

```bash
xmllint --noout --schema miniprojet2.xsd miniprojet2.xml
```

### Avec le DTD

```bash
xmllint --noout --dtdvalid miniprojet1.dtd miniprojet1.xml
```

Une sortie `miniprojet{1 | 2}.xml validates` confirme que le document est valide.

## Outils

- XML, DTD, XML Schema (XSD)
- [xmllint] pour la validation

## Auteur

Younes AMRI, L3 Informatique, Université de Tours (site de Blois)
