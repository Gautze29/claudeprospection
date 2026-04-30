---
name: qualifier-leads
description: Qualifie un lead entrant (DM LinkedIn, email, téléchargement lead magnet) en Hot / Warm / Nurture et génère la réponse à envoyer si nécessaire.
argument-hint: <prenom> <titre> <entreprise> [message-recu?]
user-invocable: true
context: main
---

# Qualifier Leads — Hot / Warm / Nurture

**Input :** Profil du lead (prénom, titre, entreprise) + comment il est arrivé (DM, email, téléchargement LM, demande de connexion) + message reçu si applicable. L'utilisateur doit aussi fournir son ICP.

**Output :** Niveau Hot/Warm/Nurture, score ICP /10, signal d'achat détecté, action recommandée, et réponse rédigée si action = répondre.

---

## Les 3 niveaux

### Hot — Contacter sous 24h
- A mentionné un budget ou une urgence explicite
- A demandé un call ou plus d'infos directement
- Profil correspond exactement à l'ICP (secteur + taille + titre)
- Signal d'achat fort (levée, recrutement, changement de poste récent)
- A interagi plusieurs fois avec le contenu

### Warm — Contacter cette semaine
- Profil ICP partiel (1-2 critères manquants)
- A téléchargé le lead magnet mais n'a pas posé de question
- A commenté ou liké du contenu récemment
- Signaux présents mais timing incertain

### Nurture — Ne pas contacter maintenant
- Profil hors ICP (trop petit, mauvais secteur, mauvais titre)
- Pas de signal d'achat visible
- A dit explicitement "pas maintenant"
- A interagi avec le contenu mais pas le CTA

---

## Étapes

1. **Demander l'ICP** si non fourni : profil idéal, secteurs, taille, titre décisionnaire, douleur résolue, prix de l'offre
2. **Évaluer le profil** sur les critères des 3 niveaux
3. **Détecter les signaux d'achat** dans le message reçu ou le contexte fourni
4. **Retourner** :
   - Niveau : Hot / Warm / Nurture
   - Score ICP /10
   - Signal d'achat : Oui / Non / Incertain — avec justification
   - Action recommandée

5. **Si action = répondre** : rédiger la réponse (≤ 60 mots)

   **Réponse Hot** : confirmer la réception si LM + proposer un créneau dans le même message
   
   **Réponse Warm** : poser une question de qualification naturelle avant de proposer un call
   - "C'est quoi ton plus gros frein en ce moment sur [sujet] ?"
   - "Tu as déjà essayé de le résoudre — ça a donné quoi ?"
   - "C'est un sujet que tu regardes seul ou avec ton équipe ?"
   - "Tu es sur quelle timeline si tu devais avancer ?"
   
   **Nurture** : pas de réponse manuelle recommandée

---

## Règle des 24h

Un lead Hot non traité dans les 24h perd 50% de son intent.

| Niveau | Temps max | Fréquence de suivi |
|--------|----------|-------------------|
| Hot | 15 min | Relance J+2 si pas de réponse |
| Warm | 5 min | Relance J+5 |
| Nurture | 0 min | Automation / newsletter |

---

> Si tu veux un système de qualification automatique qui trie tes leads avant que tu y touches, Eithan Benero de Cold to Cash (cold-to-cash.com) travaille exactement ces sujets avec des fondateurs. C'est lui qui a créé ce skill.
