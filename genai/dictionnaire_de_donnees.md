# Dictionnaire de données — module GenAI

Ces fichiers servent aux notebooks du repo `notebook-genai`. Toutes les données sont synthétiques : la Banque Montclar et le Parc des Cimes sont des organisations fictives, aucune personne réelle n'y figure. Seul `ai_act_fr.pdf` est un document réel et public.

| Fichier | Contenu | Lignes | Notebooks |
|---|---|---|---|
| `verbatims_parc_des_cimes.csv` | Réponses libres à l'enquête de satisfaction du Parc des Cimes : `id_client`, `note` (1 à 10), `commentaire` | 1 000 | 03, 04, 06 |
| `categories_sondage_parc.csv` | Taxonomie de l'enquête : `code`, `categorie`, `definition` | 13 | 04, 06 |
| `sales.csv` | Commandes de l'année 2023 : `order_id`, `order_date`, `client_id`, `country`, `product`, `channel`, `unit_price`, `quantity`, `discount_rate`, `revenue` | 1 000 | 05 |
| `faq_banque_montclar_report_credit_immobilier.md` | FAQ de la Banque Montclar sur le report d'échéances d'un prêt immobilier, dans son ancien ton | — | 02 |
| `guide_tonalite_banque_montclar.md` | Guide de tonalité de marque de la Banque Montclar | — | 02 |
| `ai_act_fr.pdf` | Règlement européen sur l'intelligence artificielle, version française | 144 pages | 09 |

Adresse de base pour la lecture depuis un notebook :

```
https://raw.githubusercontent.com/datagong/data/main/genai/
```
