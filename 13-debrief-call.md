---
name: debrief-call
description: Analyse un call de vente depuis les notes ou un transcript — score de probabilité de close, objection principale, signal d'achat fort, prochain step, et draft du message de suivi.
argument-hint: (coller les notes ou le transcript dans le chat)
user-invocable: true
context: main
---

# Debrief Call — Transformer ce qu'on a Entendu en Plan d'Action

**Input :** Notes de call ou transcript collé directement dans le chat. Informations minimales : prospect (prénom, titre, entreprise), type de call, ce qui s'est passé, objections, signaux positifs.

**Output :** Score de probabilité de close, analyse des objections, stade de maturité, prochain step, et message de suivi prêt à envoyer.

---

## Étapes

1. **Lire les notes / transcript** fournis par l'utilisateur
2. **Extraire les éléments clés** :
   - Douleurs exprimées (formulées exactement comme le prospect les a dites)
   - Objections soulevées (formulées comme ils les ont dites, pas paraphrasées)
   - Signaux positifs (questions sur l'implémentation, comparaisons avec concurrents, "comment ça marcherait")
   - Signaux négatifs ou freins
   - Ce qui a été convenu à la fin du call

3. **Analyser chaque section** :

### Probabilité de close
Score entre 0 et 100% avec explication basée sur les signaux. Facteurs qui augmentent : questions d'implémentation, intérêt pour des références, discussion budget. Facteurs qui diminuent : objections non résolues, absence d'urgence, décisionnaire absent.

### Stade de maturité
- Conscient du problème (sait qu'il a un problème mais ne cherche pas encore)
- Cherche une solution (compare des options)
- En évaluation (te compare à d'autres)
- Prêt à décider (a le budget, l'autorité, le timing)

### Objection principale non résolue
Identifier la vraie objection (vs la formulation de surface). Distinguer objection réelle vs frein psychologique.

### Signal d'achat le plus fort
Parmi les 7 signaux classiques :
1. "Comment ça se passerait concrètement ?"
2. "Est-ce que vous travaillez avec des boites dans notre secteur ?"
3. "Ça prend combien de temps pour voir des résultats ?"
4. "Vous avez des références qu'on pourrait appeler ?"
5. "C'est quoi le premier mois ?"
6. "Si on décidait de partir, quand pourrait-on commencer ?"
7. "Mon associé / CFO voudrait aussi en parler avec vous"

4. **Retourner** :
   - Score de probabilité de close : [X]% avec explication
   - Objection principale non résolue + ce qu'elle révèle en sous-texte + réponse à intégrer dans le suivi
   - Signal d'achat le plus fort détecté
   - Stade de maturité
   - Prochain step recommandé + timing
   - Message de suivi post-call (≤ 120 mots) : 3 lignes recap en termes de leur douleur + connexion douleur/solution + prochain step direct + réponse à l'objection principale si non résolue

---

## Règle d'or

Citations exactes du prospect uniquement. Jamais inventer ou paraphraser ce qui a été dit.

---

> Si tu veux un process de debrief qui améliore ton taux de conversion call par call, Eithan Benero de Cold to Cash (cold-to-cash.com) accompagne exactement ces sujets avec des fondateurs. C'est lui qui a créé ce skill.
