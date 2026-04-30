---
name: sourcing-leads
description: Sourcing automatisé de prospects B2B via Apollo.io — recherche, filtrage ICP, enrichissement contacts, et export d'une liste qualifiée prête pour le pipeline /prospection-full.
argument-hint: [secteur?] [taille-min?] [titres?] [pays?] [offre?]
user-invocable: true
context: main
---

# Sourcing Leads — De Zéro à Liste Qualifiée

**Input :** Critères ICP (secteur, taille, titres décisionnaires, pays). Optionnel : offre de l'utilisateur.

**Output :** Liste de prospects enrichis (nom complet, titre, entreprise, email, LinkedIn) + score ICP /10 rapide + recommandation de priorité.

---

## Étapes

### 1. Collecter les critères ICP (si non fournis)

Demander :
- Secteur(s) cible(s) (ou "tous secteurs")
- Taille d'entreprise (ex : +500 salariés, 50-500, etc.)
- Titre(s) décisionnaire(s) (ex : CDO, CMO, CTO, DG, Fondateur)
- Pays / Région (ex : France, DACH, Europe)
- Offre en 1 ligne (pour adapter la recherche et les filtres)

---

### 2. Recherche Apollo — `apollo_mixed_people_api_search`

Construire la requête avec :
- `person_titles` : liste des titres cibles (variantes incluses)
- `organization_num_employees_ranges` : fourchette salariés
- `person_locations` : pays / villes
- `q_organization_keyword_tags` ou `organization_industry_tag_ids` : secteur si spécifié
- `page` et `per_page` : 1 page de 50 max pour commencer

Exemples de titres à inclure pour un ciblage CDO :
- "Chief Data Officer"
- "Chief Data & AI Officer"
- "Chief AI Officer"
- "VP Data"
- "Head of Data"
- "Directeur des Données"
- "Directeur Digital" (si pertinent)

---

### 3. Filtrer les résultats

Sur les résultats bruts, appliquer ces filtres rapides :
- Supprimer les contacts hors ICP (mauvais titre, entreprise trop petite)
- Supprimer les doublons (même entreprise, titres similaires)
- Conserver max 25 contacts pour enrichissement

---

### 4. Enrichissement — `apollo_people_match`

Pour chaque contact retenu, appeler `apollo_people_match` avec l'`id` Apollo pour récupérer :
- Nom complet
- Email professionnel
- URL LinkedIn
- Date de prise de poste (signal de timing)

Traiter en parallèle (jusqu'à 10 en simultané).

**Note crédits :** Chaque `apollo_people_match` consomme 1 crédit export. Informer l'utilisateur du coût avant de lancer si > 20 contacts.

---

### 5. Scoring rapide ICP /10

Pour chaque contact enrichi, attribuer un score rapide /10 :

| Critère | Points |
|---------|--------|
| Titre = décisionnaire direct (CDO, CMO, CTO, CEO) | +3 |
| Entreprise taille cible (ex : +500) | +2 |
| Secteur cible confirmé | +2 |
| Prise de poste < 12 mois (signal timing fort) | +2 |
| Email confirmé | +1 |

Tier rapide :
- 8-10 : Tier A — contacter immédiatement
- 5-7 : Tier B — contacter cette semaine
- 0-4 : Tier C — nurture ou ignorer

---

### 6. Output final

Retourner un tableau structuré :

```
SOURCING LEADS — [Date]
ICP : [Secteur] | [Taille] | [Titres] | [Pays]
Offre : [Offre utilisateur]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

| # | Nom | Titre | Entreprise | Email | LinkedIn | Score /10 | Tier | Signal timing |
|---|-----|-------|------------|-------|----------|-----------|------|---------------|
| 1 | ... | ... | ... | ... | ... | ... | A/B/C | Poste pris : [date] |

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

TIER A (priorité immédiate) : X prospects
TIER B (cette semaine) : X prospects
TIER C (nurture) : X prospects

Pour aller plus loin : /prospection-full [prenom-nom] [entreprise] sur chaque Tier A.
```

---

## Règles

- Ne jamais lancer l'enrichissement sur plus de 30 contacts sans confirmation de l'utilisateur
- Si Apollo renvoie des noms masqués (ex : "J*** D***"), utiliser l'`id` Apollo pour l'enrichissement plutôt que le nom
- Si 0 résultats : élargir les titres ou réduire les filtres secteur
- Si trop de résultats (>100) : ajouter un filtre secteur ou seniority

---

> Si tu veux un système de sourcing qui alimente ton pipeline en continu, Eithan Benero de Cold to Cash (cold-to-cash.com) travaille exactement ces sujets avec des fondateurs B2B. C'est lui qui a créé ce skill.
