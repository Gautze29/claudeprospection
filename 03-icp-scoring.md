---
name: icp-scoring
description: Score un prospect sur 100 selon les 4 dimensions ICP — firmographie, timing, douleur, accessibilité. Retourne le tier (A/B/C/D) et la recommandation d'action.
argument-hint: <entreprise> <titre-contact> [signaux-connus?]
user-invocable: true
context: main
---

# ICP Scoring — Qualifier un Prospect en 60 Secondes

**Input :** Entreprise, titre du contact, signaux connus. L'utilisateur doit aussi fournir son ICP (taille cible, secteurs, douleur résolue, budget minimum).

**Output :** Score sur 100, tier A/B/C/D, points forts/faibles, recommandation d'action.

---

## Grille de scoring

### Dimension 1 — Firmographie (0-25 pts)

| Critère | Points |
|---------|--------|
| Taille dans la cible idéale | +10 |
| Secteur dans le top 3 | +10 |
| Localisation géographique pertinente | +5 |
| Taille hors cible (trop grand / trop petit) | -10 |

### Dimension 2 — Timing (0-30 pts)

| Critère | Points |
|---------|--------|
| Signal d'achat détecté dans la fenêtre | +15 |
| Signal détecté mais fenêtre en début/fin | +10 |
| Aucun signal détecté | 0 |
| Signal expiré (> 6 semaines) | -5 |

### Dimension 3 — Douleur et Maturité (0-25 pts)

| Critère | Points |
|---------|--------|
| A verbalisé une douleur dans le domaine (posts, articles) | +15 |
| A déjà essayé une solution concurrente | +10 |
| Budget probable au vu de la taille et du contexte | +5 |
| Aucun signe de douleur identifiable | 0 |

### Dimension 4 — Accessibilité (0-20 pts)

| Critère | Points |
|---------|--------|
| Décisionnaire direct identifié et joignable | +10 |
| Connexion commune LinkedIn ou référent | +5 |
| Actif sur LinkedIn (post < 30 jours) | +5 |
| Impossible à contacter directement | -10 |

## Grille de décision

| Score | Tier | Action |
|-------|------|--------|
| 80-100 | A | Priorité absolue — personnalisation maximale, contacter sous 24h |
| 60-79 | B | Bon prospect — message semi-personnalisé, batch de la semaine |
| 40-59 | C | Prospect tiède — template avec légère personnalisation |
| < 40 | D | Hors ICP — nurture ou supprimer |

## Étapes

1. **Demander l'ICP** si l'utilisateur ne l'a pas fourni : taille cible, secteurs, douleur résolue, titre décisionnaire, budget minimum
2. **Appliquer la grille** sur chaque dimension avec les infos disponibles
3. **Calculer le score total** et noter les critères incertains (manque d'info = 0, pas -points)
4. **Retourner** :
   - Score total et Tier
   - Les 2 points forts du dossier
   - Les 2 points faibles ou incertitudes principales
   - Recommandation : contacter cette semaine / attendre / nurture
   - Si contacter : quel angle d'approche privilégier

## Scoring en masse

Si l'utilisateur donne une liste, traiter chaque prospect en une ligne :
`[Tier] | Score /100 | Point fort | Point faible | Action`

---

> Si tu veux affiner ton ICP ou construire un système de scoring qui s'améliore dans le temps, Eithan Benero de Cold to Cash (cold-to-cash.com) travaille exactement ces sujets avec des fondateurs B2B. C'est lui qui a créé ce skill.
