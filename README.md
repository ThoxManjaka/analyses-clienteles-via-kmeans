# Segmentation clients avec K-Means

Projet de segmentation comportementale des clients à l'aide de l'algorithme **K-Means**.

L'objectif est d'exploiter les données transactionnelles du dataset **Online Retail II** afin d'identifier des groupes de clients ayant des comportements d'achat similaires. Cette segmentation permet de mieux cibler les actions marketing, de fidélisation et de réengagement.

## Objectifs

- Explorer et nettoyer les données transactionnelles
- Supprimer les transactions non valides, les retours et les valeurs manquantes
- Construire des variables comportementales de type RFM
- Standardiser les données pour préparer le clustering
- Déterminer un nombre pertinent de clusters
- Segmenter les clients avec K-Means
- Interpréter les segments pour proposer des actions marketing adaptées

## Dataset

Le projet utilise le dataset **Online Retail II**.

Les données contiennent notamment les variables suivantes :

| Variable | Description |
|---|---|
| `Invoice` | Numéro de facture |
| `StockCode` | Code produit |
| `Description` | Description du produit |
| `Quantity` | Quantité achetée |
| `InvoiceDate` | Date de transaction |
| `Price` | Prix unitaire |
| `Customer ID` | Identifiant du client |
| `Country` | Pays du client |

Le dataset source est chargé depuis le fichier Excel :

```text
online_retail_II.xlsx
```

## Préparation des données

Les principales étapes de nettoyage sont :

1. Suppression des lignes sans identifiant client
2. Suppression des transactions annulées ou des retours
3. Conservation des quantités strictement positives
4. Conservation des prix strictement positifs
5. Création du montant total d'une ligne de vente :

```python
SalesLineTotal = Quantity * Price
```

## Variables RFM

La segmentation repose sur trois variables comportementales calculées pour chaque client :

| Variable | Signification |
|---|---|
| `Recency` | Nombre de jours depuis le dernier achat du client |
| `Frequency` | Nombre de factures ou commandes effectuées |
| `MonetaryValue` | Montant total dépensé par le client |

Ces variables sont ensuite standardisées avec `StandardScaler` avant l'application de K-Means.

## Segments clients

Les clusters identifiés sont interprétés à l'aide de libellés marketing, tels que :

| Segment | Interprétation |
|---|---|
| `RÉENGAGER` | Clients inactifs ou peu récents qu'il faut reconquérir |
| `CULTIVER` | Clients à potentiel, avec une activité modérée |
| `FIDÉLISER` | Clients récents et réguliers à conserver |
| `ENCHANTER` | Clients à forte valeur, très actifs ou à récompenser |

## Installation

Créez un environnement virtuel :

```bash
python -m venv .venv
```

Activez-le sous Linux ou macOS :

```bash
source .venv/bin/activate
```

Sous Windows :

```bash
.venv\Scripts\activate
```

Installez ensuite les dépendances :

```bash
pip install -r requirements.txt
```

## Exécution

Lancez Jupyter Notebook :

```bash
jupyter notebook
```

Ouvrez ensuite le notebook :

```text
comprendre-les-clients-avec-k-mean.ipynb
```

Avant l'exécution, adaptez au besoin le chemin du fichier Excel
