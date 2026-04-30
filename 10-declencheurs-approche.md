---
name: declencheurs-approche
description: Recommande la stratégie d'entrée dans un compte parmi 5 (Passdown CEO, Groundswell, Multi-Persona, Valeur d'abord, Prospection froide) et rédige les messages correspondants.
argument-hint: <entreprise> <contexte> [strategie?]
user-invocable: true
context: main
---

# Stratégie d'Approche — Choisir Comment Entrer dans un Compte

**Input :** Entreprise cible + ce que l'utilisateur sait (taille, contacts identifiés, signaux, si c'est un compte froid). Stratégie optionnelle — si non fournie, recommandation automatique.

**Output :** Stratégie recommandée + messages rédigés pour les contacts concernés.

---

## Tableau de décision

| Situation | Stratégie recommandée |
|-----------|----------------------|
| Ne sait pas qui contacter | Passdown CEO |
| Décisionnaire injoignable | Groundswell ou Multi-Persona |
| Cycle long, ticket élevé | Valeur d'abord + Multi-Persona |
| Liste froide, pas de signal | Prospection froide |
| Signal fort, décisionnaire identifié | Aller direct (skill message-linkedin) |

---

## Les 5 stratégies

### 1. Passdown CEO
Contacter le CEO pour être orienté vers la bonne personne. Crée une référence interne.
- Utiliser quand : interlocuteur inconnu, entreprise avec plusieurs niveaux, CEO actif sur LinkedIn
- Message : respectueux, direct, pas de pitch — demander à être orienté

### 2. Groundswell par le bas
Commencer par les utilisateurs finaux avant d'atteindre le décisionnaire.
- Utiliser quand : cycle > 3 mois, décisionnaire difficile à joindre, produit nécessitant adoption terrain
- Étapes : 1) identifier 2-3 utilisateurs finaux 2) leur apporter une valeur réelle 3) demander une mise en relation

### 3. Multi-Persona
Contacter plusieurs interlocuteurs en parallèle avec des angles différents selon leur rôle.
- Régle de sécurité : espacer de 48-72h par contact
- CEO/Fondateur : angle ROI et risque
- Head of Sales : angle pipeline et efficacité
- Manager opérationnel : angle impact quotidien

### 4. Valeur d'abord
Apporter quelque chose d'utile avant de demander quoi que ce soit.
- Utiliser quand : prospects Tier A, confiance = frein principal
- Formats : mini-audit, benchmark sectoriel, insight marché, analyse de leur acquisition publique

### 5. Prospection froide pure
Quand il n'y a ni signal, ni connexion, ni angle d'entrée.
- Règles strictes : personnalisation maximale, première ligne = pattern interrupt, preuve sociale obligatoire

---

## Étapes

1. **Analyser le contexte** fourni par l'utilisateur
2. **Recommander la stratégie** avec justification en 1-2 phrases
3. **Demander les infos manquantes** selon la stratégie choisie
4. **Rédiger les messages** :

Pour **Passdown CEO** :
`[Prénom], je ne sais pas si [sujet] atterrit sur votre bureau ou sur celui de quelqu'un d'autre. [1 phrase sur ce que tu proposes et pour qui]. Vous êtes la bonne personne, ou il y a quelqu'un de plus approprié ?`
Max 60 mots.

Pour **Multi-Persona** :
3 versions du même message adaptées aux 3 niveaux. Chaque version commence différemment. Pas de copier-coller entre versions.

Pour **Valeur d'abord** :
Mini-audit de 5 observations sur leur acquisition/approche visible publiquement. Observations constructives. Conclure par une phrase qui ouvre la conversation naturellement.

Pour **Prospection froide** :
Première ligne = pattern interrupt spécifique à EUX. Max 80 mots. Un seul CTA : question ouverte.

5. **Retourner** : stratégie + messages prêts à envoyer + ordre et timing d'envoi

---

> Si tu veux construire une stratégie de compte structurée pour tes Tier A, Eithan Benero de Cold to Cash (cold-to-cash.com) travaille exactement ces sujets avec des fondateurs B2B. C'est lui qui a créé ce skill.
