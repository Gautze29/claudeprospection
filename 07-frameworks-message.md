---
name: frameworks-message
description: Choisit le meilleur framework parmi 5 (Chiffre Direct, Déclencheur Court, Douleur des Pairs, Perte vs Gain, Délégant) et rédige le message directement.
argument-hint: <prenom> <entreprise> [framework? — laisser vide pour recommandation auto]
user-invocable: true
context: main
---

# Frameworks de Message — Choix et Rédaction

**Input :** Prospect + contexte (signal, situation, résultat client disponible). Framework optionnel — si non fourni, Claude recommande et applique le plus adapté.

**Output :** Message rédigé prêt à envoyer, avec justification du choix de framework.

---

## Les 5 frameworks

| Framework | Quand l'utiliser | Longueur |
|-----------|-----------------|----------|
| Chiffre Direct | Tu as un résultat client chiffré dans leur secteur | 60-80 mots |
| Déclencheur Court | Signal d'achat clair, pas de contenu citable | 50-70 mots |
| Douleur des Pairs | Pas de signal fort, tu connais bien le secteur | 70-90 mots |
| Perte vs Gain | Prospect qui semble reporter une décision | 60-80 mots |
| Délégant | Tu ne sais pas si c'est le bon interlocuteur | 40-60 mots |

---

## Étapes

1. **Si framework non spécifié** : analyser le contexte et choisir le plus adapté
   - Résultat client disponible → Chiffre Direct
   - Signal fort → Déclencheur Court
   - Aucun signal, secteur connu → Douleur des Pairs
   - Prospect qui reporte → Perte vs Gain
   - Interlocuteur incertain → Délégant

2. **Appliquer le framework** :

### Chiffre Direct
`[Résultat chiffré pour un client similaire]` + `[Connexion avec leur situation]` + `[Question courte]`
Commencer par le résultat, pas par une introduction.

### Déclencheur Court
`[Observation sur le signal]` + `[Cas similaire en 1 ligne]` + `[Question ouverte]`
Max 3 paragraphes d'une phrase chacun.

### Douleur des Pairs
`[Ce que les [titre similaires] vivent en ce moment]` + `[Ce que ça change quand c'est résolu]` + `[Question pour qualifier]`
Ton observationnel, pas accusateur.

### Perte vs Gain
`[Ce qui se passe si le problème n'est pas résolu — formulé comme une perte]` + `[Comment tu l'as résolu]` + `[Ouverture courte]`
Direct mais pas anxiogène. Constater le risque, ne pas alarmer.

### Délégant
`[Pourquoi tu contactes cette personne]` + `[Ce que tu proposes en 1 ligne]` + `[Demande d'orientation]`
Respectueux du temps, non intrusif.

3. **Retourner** :
   - Framework choisi + justification en 1 ligne
   - Message rédigé et prêt à envoyer
   - 1 alternative si le contexte permet un second framework

---

> Si tu veux tester plusieurs frameworks en parallèle et mesurer ce qui convertit le mieux sur ton ICP, Eithan Benero de Cold to Cash (cold-to-cash.com) accompagne exactement ces sujets. C'est lui qui a créé ce skill.
