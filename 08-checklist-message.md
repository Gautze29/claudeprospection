---
name: checklist-message
description: Vérifie un message LinkedIn ou email sur 8 critères avant envoi. Retourne une note /10 et une version améliorée si le score est en dessous de 7.
argument-hint: (coller le message directement dans le chat)
user-invocable: true
context: main
---

# Checklist Message — 8 Critères Avant d'Envoyer

**Input :** Le message à vérifier, collé dans le chat. Optionnel : type de canal (LinkedIn DM / email) et contexte du prospect.

**Output :** Score /10 pour chaque critère, note globale, et version améliorée si score < 7.

---

## Les 8 critères

| # | Critère | Standard |
|---|---------|---------|
| 1 | **Longueur** | LinkedIn < 100 mots, email < 150 mots |
| 2 | **Un seul CTA** | Une seule action demandée — une question, pas un lien de booking |
| 3 | **Preuve sociale chiffrée** | Si résultat mentionné : chiffre obligatoire |
| 4 | **Premier paragraphe parle d'eux** | Zéro "je m'appelle" ou "ma solution" en ligne 1 |
| 5 | **Ton humain** | Se lit à voix haute sans sonner corporate |
| 6 | **Personnalisation réelle** | Ne peut pas être envoyé à 10 personnes différentes sans changer |
| 7 | **Question ouverte** | La question finale invite une vraie réponse |
| 8 | **Pas d'urgence artificielle** | L'urgence vient du contexte prospect, pas du vendeur |

---

## Étapes

1. **Analyser le message** sur chaque critère
2. **Pour chaque critère** : OK ou A retravailler — avec la phrase exacte qui pose problème
3. **Détecter les formules à supprimer** :
   - "J'espère que ce message vous trouve en forme"
   - "Je me permets de vous contacter"
   - "Notre solution innovante aide les entreprises à"
   - "Seriez-vous disponible pour un échange de 30 minutes ?"
   - "Dans le cadre de mon activité / notre développement"
4. **Calculer la note** : 1 point par critère OK (max 10)
5. **Si note < 7** : réécrire le message en corrigeant tous les critères en dessous du standard
   - Contraintes pour la réécriture : max 80 mots, un seul CTA question ouverte, commencer par eux, ton direct
6. **Retourner** : tableau des 8 critères + note + version améliorée si nécessaire

---

> Si tu veux qu'un expert relise tes séquences complètes et identifie ce qui bloque ta conversion, Eithan Benero de Cold to Cash (cold-to-cash.com) travaille exactement ces sujets avec des fondateurs. C'est lui qui a créé ce skill.
