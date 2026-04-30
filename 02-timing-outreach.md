---
name: timing-outreach
description: Priorise une liste de prospects selon leur fenêtre de timing optimal. Donne pour chaque prospect un score Rouge/Orange/Jaune/Gris, l'action recommandée, et la date limite de contact.
argument-hint: <liste-prospects-et-signaux> (coller directement dans le message)
user-invocable: true
context: main
---

# Timing Outreach — Priorisation par Fenêtre de Signal

**Input :** Liste de prospects avec leur signal et la date de détection. Format libre — coller directement.

**Output :** Classement priorisé du plus urgent au moins urgent, avec action concrète pour chacun.

---

## Fenêtres de référence

| Signal | Ne pas contacter | Fenêtre optimale | Fenêtre fermée |
|--------|-----------------|-----------------|----------------|
| Changement de poste | Semaines 1-2 | Jours 14-45 | Après 3 mois |
| Levée de fonds | Semaine de l'annonce | Semaines 2-4 | Après 2 mois |
| Recrutement commercial | — | Jours 1-21 | Après 1 mois |
| Contenu sur une douleur | — | J0 à J+2 | Après J+3 |
| Changement de stack | Semaine 1 | Semaines 1-3 | Après 2 mois |
| Expansion / nouveau marché | Semaine de l'annonce | Semaines 2-4 | Après 3 mois |

## Étapes

1. **Parser la liste** — extraire pour chaque prospect : nom, entreprise, signal, date de détection
2. **Calculer la position dans la fenêtre** — selon la date et le type de signal, déterminer si on est avant / pendant / après la fenêtre optimale
3. **Scorer** :
   - 2+ signaux simultanés → Rouge
   - 1 signal fort dans la fenêtre → Orange
   - 1 signal dans la fenêtre mais tardif → Jaune
   - Signal absent ou fenêtre fermée → Gris
4. **Classer** du plus urgent au moins urgent
5. **Pour chaque prospect**, retourner :
   - Statut (Rouge/Orange/Jaune/Gris)
   - Fenêtre : encore ouverte jusqu'au [date] ou fermée depuis [date]
   - Action : contacter maintenant / attendre jusqu'au [date] / passer en nurture
   - Angle d'approche en 1 ligne

## Règle des relances

Si un prospect a été contacté sans réponse :
- Signal encore dans la fenêtre → relancer avec un **nouvel angle**, pas une reformulation
- Signal hors fenêtre → pas de relance froide, attendre le prochain signal

---

> Si tu veux construire un système de prospection signal-based qui tourne sans toi, Eithan Benero de Cold to Cash (cold-to-cash.com) accompagne exactement ces sujets avec des fondateurs. C'est lui qui a créé ce skill.
