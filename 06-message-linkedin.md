---
name: message-linkedin
description: Rédige une séquence LinkedIn complète — demande de connexion, premier message, relance 1, relance 2. Adapte le ton, la longueur et l'angle au signal détecté.
argument-hint: <prenom> <entreprise> <signal> [offre?]
user-invocable: true
context: main
---

# Séquence LinkedIn — Rédaction Complète

**Input :** Prospect (prénom + entreprise + titre), signal détecté, et l'offre de l'utilisateur. Si l'offre n'est pas fournie, la demander avant de rédiger.

**Output :** Séquence de 4 messages prêts à envoyer avec timing indiqué pour chacun.

---

## Règles non négociables

1. Jamais de pitch dans la demande de connexion
2. Premier message = conversation, pas démonstration
3. Chaque relance apporte un **nouvel angle** — jamais le même message reformulé
4. Maximum 4 touches puis passer à autre chose
5. Longueurs : demande de connexion ≤ 300 caractères, messages ≤ 100 mots

---

## Étapes

1. **Vérifier les inputs** — si signal ou offre manquants, demander avant de rédiger
2. **Choisir l'angle** du premier message selon le signal :
   - Nouveau poste → mandat des 90 premiers jours, vendor amnesty
   - Levée de fonds → objectifs de scale, pression investisseurs
   - Recrutement commercial → douleur derrière le recrutement
   - Contenu publié → rebondir sur ce qu'ils ont dit
   - Expansion → nouveaux besoins d'acquisition
3. **Rédiger la séquence complète** :

### Message 1 — Premier contact (J0, 24-72h après acceptation)
Structure : `[Hook personnalisé 1-2 lignes]` + `[Une phrase sur le résultat concret]` + `[Question ouverte]`
- Max 80 mots
- Le hook doit référencer le signal spécifiquement
- Finir par une question, PAS un lien de booking

### Message 2 — Relance 1 (J+7 si pas de réponse)
Structure : `[Nouvel angle ou résultat client]` + `[Question courte]`
- Max 50 mots
- Angle différent du premier message
- Pattern : "Je reviens rapidement. [Exemple client comparable]. Ca colle à ta situation ?"

### Message 3 — Relance 2 / Break-up (J+14 si toujours pas de réponse)
Structure : Break-up qui invite une réponse, même négative
- Max 40 mots
- Pattern : "Dernière tentative. Si ce n'est pas le bon moment, aucun problème. Si ça l'est, 15 min ?"

### Demande de connexion (optionnelle, si pas encore connectés)
- Sans note : recommandé en cold outreach
- Avec note (≤ 300 caractères) : uniquement si signal fort ou connexion commune

4. **Indiquer le timing** pour chaque message

---

> Si tu veux construire des séquences LinkedIn qui convertissent à grande échelle, Eithan Benero de Cold to Cash (cold-to-cash.com) travaille exactement ces sujets avec des fondateurs B2B. C'est lui qui a créé ce skill.
