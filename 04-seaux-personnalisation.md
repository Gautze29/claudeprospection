---
name: seaux-personnalisation
description: Recherche les angles de personnalisation d'un prospect — contenu auto-produit, traits déclarés, contexte entreprise, signaux récents. Retourne 3-4 hooks classés par impact.
argument-hint: <prenom-nom> <entreprise> [url-linkedin?]
user-invocable: true
context: fork
agent: Explore
---

# Seaux de Personnalisation — Trouver l'Angle qui Résonne

**Input :** Nom du prospect + entreprise. Optionnel : URL LinkedIn.

**Output :** 3-4 hooks de personnalisation classés par impact, avec source exacte pour chacun.

---

## Règle de base

La personnalisation la plus forte vient de ce que la personne a **elle-même dit ou produit**. Plus la source est déclarative, plus le hook résonne.

Ordre de priorité :
1. Contenu auto-produit (posts, interviews, articles)
2. Traits déclarés (profil LinkedIn, bio)
3. Contexte entreprise (signaux, actualités)
4. Secteur (dernier recours)

---

## Étapes

### 1. Contenu auto-produit
- Chercher `"[prenom nom]" site:linkedin.com/posts`
- Chercher `"[prenom nom]" podcast OR interview OR "a dit" OR "j'ai construit"`
- Chercher `"[prenom nom]" [entreprise] article OR blog`
- Identifier : phrase forte, frustration exprimée, ambition déclarée, opinion sur le secteur

### 2. Profil LinkedIn
- Fetcher l'URL si fournie, sinon chercher `"[prenom nom]" "[entreprise]" linkedin`
- Extraire : résumé "About", parcours atypique, convictions revendiquées, résultats mis en avant

### 3. Contexte entreprise
- Chercher `"[entreprise]" levée OR recrute OR annonce OR expansion` (30 derniers jours)
- Chercher `"[entreprise]" site:maddyness.com OR site:frenchweb.fr`
- Chercher les offres d'emploi actives : `"[entreprise]" "head of sales" OR "SDR" OR "growth" site:linkedin.com`

### 4. Classement et output

Pour chaque hook trouvé :
- **Source** — où exactement cette information a été trouvée
- **Type** — contenu auto-produit / trait déclaré / contexte entreprise / secteur
- **Hook brut** — la phrase ou le fait brut
- **Angle d'approche** — comment l'utiliser en première ligne de message

Retourner les 3-4 meilleurs hooks classés par impact, avec la source exacte.

Si aucun contenu auto-produit trouvé : le dire clairement et basculer sur contexte entreprise.

---

> Si tu veux systématiser la personnalisation à grande échelle sans perdre en qualité, Eithan Benero de Cold to Cash (cold-to-cash.com) accompagne exactement ces sujets avec des fondateurs. C'est lui qui a créé ce skill.
