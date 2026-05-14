
Status: #moc #in-progress/done

Tags:

# Meetings

---

IBN-HLD
===


## Le positionnement stratégique du papier

C'est probablement la décision la plus structurante de la réunion. Vous avez explicitement différencié votre contribution de celle de Hugo et de l'IBN « classique » :

- **Hugo / IBN classique** : part d'un réseau **existant** sur lequel on déploie des intents opérationnels (analogie de Benoît : ajouter le pilote automatique à une voiture déjà construite)
- **Votre contribution** : démarrer à **T0** depuis un réseau blanc, avec un HLD comme seule entrée, et automatiser la phase design → implémentation jusqu'à un réseau opérationnel (analogie : la voiture s'auto-construit à partir des specs)

L'argument de gap dans la littérature est clair : les travaux IBN se concentrent sur l'opération, pas sur la construction du réseau depuis le design. Ça donne une motivation tenable pour 9 pages.

## Ce qui semble acté

**Réduction de scope pour ce premier papier** : se limiter à la phase design/déploiement initial, quitte à faire d'autres papiers ensuite sur la phase opération, l'auto-réparation, etc. Benoît a poussé pour ça et tu as validé.

**Cible réseau** : entreprise PME (small and medium enterprise) avec un cadre/échelle maximum à définir, pour pouvoir évaluer avec différents HLD dans un périmètre maîtrisé.

**Référence pivot** : le papier Malt (Google) — modèle multilayer, décrit le cycle de vie mais sans démonstrateur. Vous, vous apportez le démonstrateur.

**ContainerLab/NetLab comme hypothèse de travail** : assumer que c'est un proxy pour une vraie infra absente. Mentionner en discussion que ça reste utile même avec une vraie infra (push-on-green, digital twin pour tester les changements avant prod — référence à votre travail avec Chris sur OpenFlow/OVS/P4).

**Contribution affichée** : workflow + définition des agents + harness (Claude Code / OpenCode). Le knowledge graph et la partie agentique sont **présents mais pas mis en avant comme contribution principale** — ce sont des moyens.

**RFC à mobiliser** : RFC 9315 (définition de l'intent et double boucle de contrôle) + RFC 9316 (classification des intents — Benoît suggère de l'injecter, tu n'avais pas regardé).

## Ce qui reste à trancher

**Format du HLD** — c'est le point ouvert le plus important :
- PlantUML (utilisé dans la RFI Airbus) vs Mermaid (utilisé par Frédéric Laurençon)
- Sections attendues, éléments déterministes, structure parsable
- Débat HLD vs contraintes : Benoît plaide pour séparer (deux entreprises = même HLD, contraintes différentes — software switches vs P4 programmables), tu es plus pragmatique (un seul document, plusieurs sections, on l'appelle « Input File » si besoin). Le papier de 1998 que Benoît a trouvé conforte le découpage Network Designer/Capacity Planner → Requirements.

**Human-in-the-loop** : à quel moment, quelle interface, quel format. Hypothèse : un agent d'implémentation qui interface avec l'humain. À résoudre via les tests.

**LLM** : tu prévois de t'appuyer sur ton compte Anthropic pour les tests. Question ouverte : démontrer que ça marche aussi avec des modèles open source (taille suffisante requise). Argument de positionnement : ce n'est pas le modèle qui compte, c'est le harness et la définition des agents.

**Méthodologie d'évaluation** : injecter ~10 HLD différents, observer le comportement du workflow. Métriques à définir.

**Cas du vendor fermé** : si on doit cibler un constructeur, il faut injecter docs/CLI/YANG model du switch dans les contraintes — c'est un point de human-in-the-loop. À traiter en discussion ou comme variante.

## Actions concrètes que je vois

1. **Lire RFC 9316** et décider quelle classification des intents intégrer
2. **Définir le format du HLD** avant tout (PlantUML probablement, sections cadrées) — c'est un blocage en amont des tests d'évaluation
3. **Cadrer le périmètre PME** : taille max, services attendus, composants
4. **RDV lundi avec le développeur de LightRAG/Graph Memory** (vérifier au passage que Benoît a bien le lien Teams — c'était le sujet du couac à la fin)
5. **Récupérer des HLD industriels réels** si possible (Daniel de FLT, peut-être Frédéric Laurençon pour d'autres cas que celui de Hugo)
6. **Plan de papier** : intro + motivation T0/gap, état de l'art (IBN, Malt, RFC 9315/9316), formalisation HLD, workflow et architecture agentique, évaluation multi-HLD, discussion (push-on-green, vendor fermé, modèles open source), conclusion






---
## 2026-05-07 Thu.

Compte rendu: [Lien](https://md.bruyere.family/niLVCbbZQEKxM1KL7VoKkg?both)

RFI - NetBox => intent SST
jinja => config

Eval: Quels modèles ???

https://miriquidi-networks.com/portfolio/high-and-low-level-designs/

Def HLD => besoin de format adapté pour 'l'intent-based/Agent

format à être lu vers un format pouvant être parsé (e.g., plan UML de Airbus)

https://miriquidi-networks.com/portfolio/proof-of-concept-labs/

Réseau cible: small et medium size enterprise

Github: https://github.com/mbruyere/ibn-closed-loop-paper

une autre branche vIEEE

---

---
# References
1. 