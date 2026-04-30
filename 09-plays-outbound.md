---
name: plays-outbound
description: Sélectionne et exécute un play outbound parmi 8 — Nouveau Leadership, Recrutement Signal, Post-Levée, Follower ICP, Contenu Douleur, Dégradation Concurrente, Expansion, Ancien Champion.
argument-hint: <play?> <prenom> <entreprise> [contexte-signal]
user-invocable: true
context: main
---

# Plays Outbound Signal-Based

**Input :** Prospect + signal détecté. Le play peut être spécifié ou Claude le recommande automatiquement selon le signal.

**Output :** Message rédigé pour le play choisi, prêt à envoyer.

---

## Les 8 plays

| Play | Signal | Timing |
|------|--------|--------|
| Nouveau Leadership | Nouveau CEO / Head of Sales / directeur | J+14 à J+45 |
| Recrutement Signal | Offre d'emploi commerciale publiée | J+1 à J+10 |
| Post-Levée | Annonce de levée Seed/A/B | Semaines 2-4 après |
| Follower ICP | Nouveau follower LinkedIn dans l'ICP | Sous 48h |
| Contenu Douleur | Post publié sur une douleur pertinente | Sous 48h |
| Dégradation Concurrente | Avis négatif sur G2/Trustpilot d'un concurrent | Sous 1 semaine |
| Expansion | Nouveau marché / nouveau produit annoncé | Semaines 2-4 après |
| Ancien Champion | Ex-client ou ex-contact qui change d'entreprise | J+7 à J+14 |

---

## Étapes

1. **Identifier le play** — si non spécifié, lire le signal et sélectionner automatiquement
2. **Vérifier le timing** — si hors fenêtre, alerter l'utilisateur et proposer d'attendre ou de passer en nurture
3. **Demander les infos manquantes** si nécessaire (ex. pour Post-Levée : objectifs annoncés dans la presse)
4. **Rédiger le message** selon le play :

### Nouveau Leadership
- Reconnaît le nouveau rôle sans être condescendant
- Identifie un enjeu typique des 90 premiers jours dans ce type de poste
- Finit par une question sur leur priorité actuelle
- Max 80 mots

### Recrutement Signal
- Référence le poste recruté (SDR / Head of Sales / Growth)
- Traduit le recrutement en douleur sous-jacente
- Contacte le CEO ou responsable direct (jamais le recruteur)
- Max 70 mots

### Post-Levée
- Félicite sans être plat (une phrase)
- Connecte les objectifs de scale à un défi d'acquisition concret
- Pose une question sur leur approche actuelle
- Max 80 mots

### Follower ICP
- Reconnaît qu'ils suivent sans être bizarre
- Qualifie leur intérêt en une question naturelle
- Pas de pitch
- Max 50 mots

### Contenu Douleur
- Cite ou fait référence au post de manière naturelle
- Montre que tu résous exactement cette douleur
- Propose une conversation, pas un call immédiat
- Max 60 mots

### Dégradation Concurrente
- Référence la douleur exprimée sans mentionner la source (avis G2)
- Propose une alternative concrète
- Zéro bashing du concurrent
- Max 80 mots

### Expansion
- Connecte l'expansion à une douleur typique de ce stade
- Résultat concret pour une entreprise en phase similaire
- Max 70 mots

### Ancien Champion
- Rappelle la collaboration sans être nostalgique
- Identifie une opportunité dans leur nouveau rôle
- Propose une conversation naturelle
- Max 60 mots

5. **Retourner** : play choisi + justification + message prêt à envoyer

---

> Si tu veux construire un système de plays outbound qui tourne en semi-automatique, Eithan Benero de Cold to Cash (cold-to-cash.com) accompagne exactement ces sujets avec des fondateurs. C'est lui qui a créé ce skill.
