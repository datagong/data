# Dictionnaire de données — Maison Pivoine

Maison Pivoine est une enseigne fictive de vente en ligne d'articles pour la maison. Le jeu couvre les commandes passées du 1ᵉʳ janvier 2024 au 30 juin 2026. Toutes les données sont synthétiques : aucune personne réelle n'y figure.

Chaque table existe en deux versions : `data/clean/` (données de référence) et `data/raw/` (export brut, à fiabiliser).

## Relations entre les tables

Un client (`customers`) passe zéro, une ou plusieurs commandes (`orders`). Une commande contient une ou plusieurs lignes (`order_items`). Chaque ligne porte sur un produit du catalogue (`products`).

| Table | Une ligne représente | Clé | Lignes |
|---|---|---|---|
| `customers` | un client inscrit | `customer_id` | 5 000 |
| `products` | un produit du catalogue | `product_id` | 261 |
| `orders` | une commande | `order_id` | 30 000 |
| `order_items` | un produit dans une commande | `order_id` + `line_number` | 77 780 |

## customers

| Colonne | Type | Description | Valeurs |
|---|---|---|---|
| `customer_id` | texte | Identifiant du client | `C00001` à `C05000` |
| `first_name` | texte | Prénom | |
| `last_name` | texte | Nom | |
| `email` | texte | Adresse e-mail | |
| `gender` | texte | Genre déclaré à l'inscription (champ facultatif) | `F`, `M` |
| `birth_date` | date | Date de naissance (champ facultatif) | |
| `city` | texte | Ville de livraison principale | |
| `postal_code` | texte | Code postal, sur cinq caractères | `06000`, `75011`… |
| `region` | texte | Région administrative | |
| `customer_type` | texte | Type de client | `Particulier`, `Professionnel` |
| `signup_date` | date | Date d'inscription | à partir de 2022 |
| `signup_channel` | texte | Canal d'inscription | `Site web`, `Application mobile`, `Parrainage`, `Réseaux sociaux` |
| `newsletter_optin` | booléen | Le client a accepté la newsletter | `True`, `False` |
| `updated_at` | date | Dernière mise à jour de la fiche client | |

## products

| Colonne | Type | Description | Valeurs |
|---|---|---|---|
| `product_id` | texte | Identifiant du produit | `P0001` à `P0261` |
| `product_name` | texte | Libellé | |
| `category` | texte | Catégorie | `Cuisine`, `Décoration`, `Linge de maison`, `Rangement`, `Jardin`, `Luminaires` |
| `subcategory` | texte | Sous-catégorie | 15 modalités |
| `brand` | texte | Marque | 7 modalités |
| `unit_price` | décimal | Prix de vente catalogue, en euros TTC | |
| `unit_cost` | décimal | Coût d'achat unitaire, en euros | |
| `launch_date` | date | Date de mise en vente | |

## orders

| Colonne | Type | Description | Valeurs |
|---|---|---|---|
| `order_id` | texte | Identifiant de la commande | `O000001` à `O030000` |
| `customer_id` | texte | Client qui a passé la commande | clé vers `customers` |
| `order_date` | date et heure | Moment de la commande | |
| `status` | texte | État de la commande | `Livrée`, `Retournée`, `Annulée`, `En cours` |
| `channel` | texte | Canal de commande | `Site web`, `Application mobile` |
| `payment_method` | texte | Moyen de paiement | `Carte bancaire`, `PayPal`, `Virement`, `Carte cadeau` |
| `shipping_mode` | texte | Mode de livraison | `Standard`, `Point relais`, `Express` |
| `shipping_fee` | décimal | Frais de livraison facturés, en euros. Standard 4,90 ; Point relais 3,50 ; Express 9,90 ; offerts dès 60 € d'achat hors Express | |
| `delivery_date` | date | Date de livraison. Vide si la commande est annulée ou en cours | |
| `satisfaction_score` | décimal | Note de l'enquête de satisfaction. Vide si le client n'a pas répondu | 1 à 5 |
| `updated_at` | date | Dernière mise à jour de la commande | |

## order_items

| Colonne | Type | Description | Valeurs |
|---|---|---|---|
| `order_id` | texte | Commande concernée | clé vers `orders` |
| `line_number` | entier | Numéro de la ligne dans la commande | 1 à 8 |
| `product_id` | texte | Produit commandé | clé vers `products` |
| `quantity` | entier | Quantité commandée | |
| `unit_price` | décimal | Prix unitaire catalogue au moment de la commande, en euros | |
| `discount_rate` | décimal | Taux de remise appliqué à la ligne | `0`, `0.1`, `0.2`, `0.3` |

Le montant d'une ligne se calcule ainsi : `quantity × unit_price × (1 − discount_rate)`.
