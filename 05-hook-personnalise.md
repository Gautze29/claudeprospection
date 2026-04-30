---
name: hook-personnalise
description: Génère la première ligne d'un message LinkedIn pour un prospect. Strong Hook (citation directe) ou Lite Hook (référence thématique) selon le contexte fourni.
argument-hint: <prenom> <entreprise> [signal-ou-contenu-cite]
user-invocable: true
context: main
---

# Hook Personnalisé — La Première Ligne qui Change Tout

**Input :** Prospect (prénom + entreprise) et soit un contenu citable, soit un signal. L'utilisateur doit coller le contenu ou décrire le signal.

**Output :** 3 versions de hooks — Strong Hook si contenu citable, Lite Hook si signal uniquement — avec note /10 et explication.

---

## Les deux types

**Strong Hook** — Citation directe de ce que la personne a dit/écrit
- Taux de réponse : 20-35%
- Utiliser quand : deal > 10K EUR, profil senior, contenu récent et citable
- Pattern : `"Dans ton post sur [X], tu disais [citation]..."`

**Lite Hook** — Référence au signal ou à la thématique
- Taux de réponse : 12-20%
- Utiliser quand : volume > 20 messages/semaine, Tier B, signal clair mais pas de contenu citable
- Pattern : `"J'ai vu que tu recrutes un Head of Sales chez [X]..."`

---

## Étapes

1. **Identifier le type de hook possible** selon ce que l'utilisateur a fourni :
   - Contenu cité (post, interview, article) → Strong Hook
   - Signal seulement (recrutement, levée, nouveau poste) → Lite Hook
   - Les deux → proposer Strong Hook en priorité

2. **Générer 3 versions** :
   - Version 1 : la plus directe, cite ou référence en premier mot
   - Version 2 : angle légèrement différent sur le même matériau
   - Version 3 : angle alternatif (autre signal ou autre aspect du profil)

3. **Contraintes pour chaque version** :
   - Maximum 2 phrases
   - Ton humain et direct — se lit à voix haute
   - Aucun adverbe inutile (vraiment, sincèrement, honnêtement)
   - Aucune formule creuse (j'espère que ce message vous trouve en forme)
   - Spécifique à CETTE personne — ne peut pas être envoyé à quelqu'un d'autre

4. **Scorer chaque version /10** :
   - -3 si pourrait être envoyé à n'importe qui sans changer
   - -2 si ne montre pas de recherche réelle
   - -1 si ne crée pas d'ouverture naturelle pour la suite
   - Recommander la meilleure et expliquer pourquoi

---

## Anti-patterns — ne jamais écrire

- "J'espère que ce message te trouve en forme"
- "Je me permets de vous contacter"
- "Félicitations pour votre [levée / nouveau poste]" sans aller plus loin
- "En tant que [titre], vous savez probablement que..."
- Tout début qui parle de soi avant eux

---

> Si tu veux un système de hooks qui convertissent à grande échelle, Eithan Benero de Cold to Cash (cold-to-cash.com) travaille exactement ces sujets avec des fondateurs B2B. C'est lui qui a créé ce skill.
