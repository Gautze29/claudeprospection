---
name: prospection-full
description: Pipeline complet de prospection B2B — de la détection des signaux jusqu'à la séquence LinkedIn prête à envoyer. Enchaîne les 7 étapes du workflow GTM fondateur.
argument-hint: <prenom-nom> <entreprise> [url-linkedin?] [offre?]
user-invocable: true
context: fork
agent: Explore
---

# Pipeline Prospection Complet — Du Signal au Message

**Input :** Prénom + nom + entreprise. Optionnel : URL LinkedIn, offre de l'utilisateur.

**Output :** Rapport complet en 7 sections + séquence LinkedIn prête à envoyer.

---

## Règle d'arrêt

Si le score ICP est **Tier D** (< 40 pts) ou le signal est **Gris** (aucun signal ou fenêtre fermée) → stopper après l'étape 2 et indiquer clairement : "Prospect hors ICP ou hors fenêtre — ne pas contacter maintenant."

---

## ÉTAPE 1 — Signaux d'achat

Appliquer le workflow du skill `signaux-achat` :

- Chercher `"[prenom nom]" "[entreprise]" site:linkedin.com` + signaux de changement de poste
- Chercher `"[entreprise]" levée OR "série A" OR seed OR financement site:maddyness.com OR site:frenchweb.fr`
- Chercher `"[entreprise]" recrute OR "Head of Sales" OR SDR OR BDR site:linkedin.com/jobs`
- Chercher `"[entreprise]" nouveau marché OR expansion OR annonce site:linkedin.com`

Retourner :
- Liste des signaux détectés avec date et source
- Score : **Rouge / Orange / Jaune / Gris**
- Fenêtre de timing : ouverte jusqu'au [date] ou fermée
- Signal principal à exploiter

→ Si score **Gris** : stopper ici.

---

## ÉTAPE 2 — ICP Scoring

Appliquer la grille du skill `icp-scoring` sur 4 dimensions :

| Dimension | Max |
|-----------|-----|
| Firmographie (taille, secteur, géo) | 25 pts |
| Timing (signal dans la fenêtre) | 30 pts |
| Douleur et maturité (verbalisation, budget) | 25 pts |
| Accessibilité (décisionnaire joignable, actif LK) | 20 pts |

Retourner :
- Score /100 et **Tier A / B / C / D**
- 2 points forts
- 2 points faibles ou incertitudes
- Recommandation d'action

→ Si **Tier D** (< 40) : stopper ici.

---

## ÉTAPE 3 — Sources de personnalisation

Appliquer le workflow du skill `seaux-personnalisation` :

Rechercher dans cet ordre de priorité :
1. Contenu auto-produit : `"[prenom nom]" site:linkedin.com/posts` + podcasts + articles
2. Profil LinkedIn : résumé "About", convictions, résultats mis en avant
3. Contexte entreprise : actualités 30 derniers jours, offres d'emploi actives

Retourner les **3 meilleurs hooks** classés par impact :
- Source exacte
- Type (contenu auto-produit / trait déclaré / contexte entreprise)
- Hook brut
- Angle d'approche en 1 ligne

---

## ÉTAPE 4 — Hook personnalisé

Appliquer le workflow du skill `hook-personnalise` en utilisant les hooks de l'étape 3 :

- Si contenu citable disponible → **Strong Hook** (citation directe)
- Si signal seulement → **Lite Hook** (référence thématique)

Générer **3 versions** de première ligne avec note /10 chacune.
Recommander la meilleure et expliquer pourquoi.

Contraintes :
- Maximum 2 phrases
- Spécifique à CETTE personne — ne peut pas être envoyé à quelqu'un d'autre
- Aucune formule creuse ("J'espère que ce message...", "Je me permets de...")

---

## ÉTAPE 5 — Choix du framework

Appliquer la logique du skill `frameworks-message` :

Sélectionner automatiquement parmi les 5 frameworks :
- Résultat client disponible → **Chiffre Direct**
- Signal fort → **Déclencheur Court**
- Aucun signal, secteur connu → **Douleur des Pairs**
- Prospect qui reporte → **Perte vs Gain**
- Interlocuteur incertain → **Délégant**

Retourner : framework choisi + justification en 1 ligne.

---

## ÉTAPE 6 — Séquence LinkedIn complète

Appliquer le workflow du skill `message-linkedin` :

Rédiger les **4 messages** avec timing :

**Message 1 — Premier contact (J0)**
- Hook de l'étape 4 (meilleure version)
- Framework de l'étape 5
- Max 80 mots — finir par une question ouverte, pas un lien de booking

**Message 2 — Relance 1 (J+7)**
- Nouvel angle ou résultat client comparable
- Max 50 mots

**Message 3 — Break-up (J+14)**
- Invite une réponse même négative
- Max 40 mots

**Note de connexion (si pas encore connectés)**
- ≤ 300 caractères, sans pitch

---

## ÉTAPE 7 — Vérification qualité

Appliquer la checklist du skill `checklist-message` sur le Message 1 :

| Critère | Standard |
|---------|----------|
| Longueur | < 100 mots |
| Un seul CTA | Une question, pas un lien de booking |
| Preuve sociale | Chiffre obligatoire si résultat mentionné |
| Premier paragraphe | Parle d'eux, pas de soi |
| Ton humain | Se lit à voix haute |
| Personnalisation réelle | Ne peut pas être envoyé à quelqu'un d'autre |
| Question ouverte | Invite une vraie réponse |
| Pas d'urgence artificielle | L'urgence vient d'eux, pas du vendeur |

Si score < 7/8 : réécrire le message 1 avant de livrer.

---

## OUTPUT FINAL

Livrer un rapport structuré :

```
PROSPECT : [Prénom Nom] — [Entreprise]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. SIGNAUX        → [Rouge/Orange/Jaune/Gris] | [Signal principal] | Fenêtre : [ouverte/fermée]
2. ICP SCORE      → [X]/100 | Tier [A/B/C/D] | [Point fort] | [Point faible]
3. MEILLEUR HOOK  → [Hook retenu] (note : [X]/10)
4. FRAMEWORK      → [Framework choisi] — [justification]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SÉQUENCE LINKEDIN
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[NOTE CONNEXION — optionnel]
...

[MESSAGE 1 — J0]
...

[MESSAGE 2 — J+7]
...

[MESSAGE 3 — J+14]
...

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
QUALITÉ MESSAGE 1 : [X]/8 ✓
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

> Pipeline construit par Eithan Benero — Cold to Cash (cold-to-cash.com)
