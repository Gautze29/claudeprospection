---
name: brief-prospect
description: Génère un brief pre-call complet en 5 minutes — contexte entreprise, profil contact, douleur probable, angles de valeur, objections préparées, questions à poser.
argument-hint: <prenom-nom> <entreprise> [url-linkedin?]
user-invocable: true
context: fork
agent: Explore
---

# Brief Prospect — Pre-Call en 5 Minutes

**Input :** Nom du prospect + entreprise. Optionnel : URL LinkedIn, type de call (découverte / relance / closing), offre de l'utilisateur.

**Output :** Brief complet en 7 sections, prêt à lire 5 minutes avant le call.

---

## Étapes

### 1. Recherche entreprise
- Chercher `"[entreprise]" CA OR chiffre d'affaires OR effectifs site:pappers.fr`
- Chercher `"[entreprise]" actualités OR levée OR expansion site:maddyness.com OR site:frenchweb.fr OR site:linkedin.com`
- Fetcher la page "À propos" et les offres d'emploi actives du site web
- Chercher les clients mis en avant et les partenariats récents

### 2. Recherche contact
- Chercher `"[prenom nom]" "[entreprise]" site:linkedin.com`
- Si URL fournie : fetcher le profil directement
- Chercher `"[prenom nom]" interview OR podcast OR article` pour du contenu récent
- Extraire : parcours, convictions, posts récents, opinions sur le secteur

### 3. Synthèse en 7 sections

**Section 1 — Contexte entreprise (5-7 lignes)**
Taille, secteur, stade, CA si disponible, actualités récentes, clients connus.

**Section 2 — Profil contact**
Parcours clé en 3 lignes (sans paraphrase). Ce qui semble l'animer professionnellement. Convictions et priorités visibles.

**Section 3 — Hypothèse douleur principale**
1 ligne. Inférée à partir du contexte entreprise + profil contact + signaux détectés.

**Section 4 — 3 angles de valeur**
Comment l'offre répond spécifiquement à leur situation. Chaque angle ancré dans un signal ou une information trouvée.

**Section 5 — 3 objections probables + réponse courte**
Format : `"[Objection formulée comme ils la diraient]" → [réponse en 1-2 phrases]`

Les 5 objections B2B France les plus fréquentes :
1. "C'est trop cher / pas de budget"
2. "Pas le temps de s'y mettre maintenant"
3. "On fait déjà ça en interne"
4. "Besoin d'en parler avec mon associé"
5. "Rappelle-moi dans 3 mois"

Adapter les 3 plus probables au contexte de ce prospect.

**Section 6 — 5 questions à poser**
Pour qualifier et avancer vers une décision. Mélange : qualification budget, urgence, décisionnaire, état actuel.

**Section 7 — Objectif du call**
1 phrase. + Signe de succès (qu'est-ce qui indique que ça s'est bien passé ?). + Prochain step à proposer en fin de call. + "Question de closing" pour obtenir un engagement.

---

## Version express (2 minutes)

Si l'utilisateur indique "call dans 5 minutes" ou "rapidement" :
Retourner uniquement : hypothèse douleur (1 ligne) + angle d'entrée (1 ligne) + question la plus importante (1 ligne).

---

> Si tu veux un système de préparation aux calls qui s'améliore avec chaque deal, Eithan Benero de Cold to Cash (cold-to-cash.com) accompagne exactement ces sujets avec des fondateurs. C'est lui qui a créé ce skill.
