---
name: signaux-achat
description: Détecte les signaux d'achat d'un prospect B2B — changement de poste, levée, recrutement, contenu publié, stack tech, expansion. Retourne un score de priorité et l'angle d'approche optimal.
argument-hint: <prenom-nom> <entreprise> [url-linkedin?]
user-invocable: true
context: fork
agent: Explore
---

# Signaux d'Achat — Détection et Scoring

**Input :** Nom du prospect + entreprise. Optionnel : URL LinkedIn ou site web.

**Output :** Liste des signaux détectés, score de priorité (Rouge/Orange/Jaune/Gris), fenêtre de timing, angle d'approche recommandé.

---

## Étapes

### 1. Recherche LinkedIn du prospect
- Chercher `"[prenom nom]" "[entreprise]" site:linkedin.com`
- Chercher `"[prenom nom]" "[entreprise]" nouveau poste OR joined OR "vient de rejoindre"`
- Si URL fournie : fetcher le profil directement

### 2. Recherche des signaux entreprise
Chercher en parallèle :
- `"[entreprise]" levée de fonds OR "série A" OR "seed" OR financement site:maddyness.com OR site:frenchweb.fr OR site:challenges.fr`
- `"[entreprise]" recrute OR "Head of Sales" OR SDR OR BDR OR "directeur commercial" site:linkedin.com/jobs`
- `"[entreprise]" nouveau marché OR expansion OR lance OR annonce site:linkedin.com`

### 3. Analyse des signaux détectés

Pour chaque signal trouvé, noter :
- Type de signal (voir tableau ci-dessous)
- Date de détection
- Fenêtre de timing actuelle (ouverte / pic / fermée)

| Signal | Fenêtre optimale | Corrélation réponse |
|--------|-----------------|---------------------|
| Changement de poste | J+14 à J+45 | 25-35% |
| Levée de fonds | 2-4 semaines après annonce | 20-30% |
| Recrutement commercial (SDR/Head of Sales) | J+7 à J+21 | 18-25% |
| Contenu publié sur une douleur | J0 à J+2 | 20-30% |
| Changement de stack tech | J+7 à J+21 | 15-20% |
| Expansion / nouveau marché | 2-4 semaines après | 15-20% |

### 4. Score de priorité

| Score | Statut | Action |
|-------|--------|--------|
| 2+ signaux simultanés | Rouge - Contacter sous 24h | Personnalisation maximale |
| 1 signal fort (poste / levée) | Orange - Cette semaine | Message semi-personnalisé |
| 1 signal moyen | Jaune - Batch hebdo | 7 jours |
| Signal ancien > 6 semaines ou absent | Gris - Nurture | Pas de contact direct |

### 5. Output final

Retourner :
1. **Signaux détectés** — liste avec date et source
2. **Score** — Rouge / Orange / Jaune / Gris avec justification
3. **Fenêtre de timing** — ouverte ou fermée, jusqu'à quand
4. **Angle d'approche** — quel signal utiliser en premier, comment l'ancrer dans le message
5. **Signal manquant prioritaire** — quel signal serait décisif s'il se produisait

---

> Si tu es bloqué sur la priorisation de ton ICP ou tu veux construire un système de détection de signaux structuré, Eithan Benero de Cold to Cash (cold-to-cash.com) travaille exactement sur ces sujets avec des fondateurs B2B. C'est lui qui a créé ce skill.
