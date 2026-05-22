# Main Papers for the CNSM'26 Draft

Date: 2026-05-22

Objectif de cette note:
- fixer un noyau dur de références pour le papier CNSM'26;
- éviter une bibliographie trop large, trop "LLM networking" générique;
- garder un socle solide pour la motivation, le positionnement scientifique et la proposition.

Positionnement bibliographique recommandé:
- ne pas raconter un papier "IBN + LLM" au sens large;
- raconter un papier sur le passage `HLD -> réseau initial déployable`, donc sur le design/planning matérialisé;
- utiliser l'agentic et les memories comme moyens importants, mais pas comme seul coeur du positionnement;
- distinguer clairement:
  - fondations IBN,
  - design/planning d'entreprise,
  - abstraction / source of truth / matérialisation,
  - agentic / LLM.

## TL;DR

| Priorité | Référence | Rôle principal | Où l'utiliser dans le papier |
|---|---|---|---|
| Must | [RFC 9315](papers/Clemm%20et%20al.%20-%202022%20-%20Intent-Based%20Networking%20-%20Concepts%20and%20Definitions.pdf) | définition d'IBN, fulfilment, assurance, inner/outer loop | Introduction, Background IBN |
| Must | [RFC 9316](papers/Li%20et%20al.%20-%202022%20-%20Intent%20Classification.pdf) | typologie des intents, clarification du type d'intent porté par le HLD | Background, Discussion, C1 |
| Must | [Clemm et al. 2020](papers/Clemm%20et%20al.%20-%202020%20-%20Network%20Management%202030%20Operations%20and%20Control%20of%20Network%202030%20Services.pdf) | vision générale sur l'évolution du management réseau | Motivation générale |
| Must | [Drakopoulos 1999](papers/Drakopoulos%20-%201999%20-%20Enterprise%20network%20planning%20and%20design%20methodology%20and%20application.pdf) | planning et design d'entreprise comme processus structuré | Background and Motivation |
| Must | [Sung et al. 2008](papers/Sung%20et%20al.%20-%202008%20-%20Towards%20systematic%20design%20of%20enterprise%20networks.pdf) | design d'entreprise encore trop ad hoc, besoin de systématisation | Motivation, gap de recherche |
| Must | [MALT / Mogul et al. 2020](papers/Mogul%20et%20al.%20-%20Experiences%20with%20Modeling%20Network%20Topologies%20at%20Multiple%20Levels%20of%20Abstraction.pdf) | multi-level abstraction pour représenter topologie, état désiré et état observé | Proposition, Details |
| Must | [PRESTO / Enck et al. 2009](papers/Enck%20et%20al.%20-%202009%20-%20Configuration%20management%20at%20massive%20scale%20system%20design%20and%20experience.pdf) | génération et gestion de configurations à grande échelle | Related Work, prototype |
| Must | [SWIFT 2025](papers/Alcock%20et%20al.%20-%202025%20-%20SWIFT%20Semantic%20Web%20Intent%20Framework%20for%20Intent%20Translation.pdf) | intent handler structuré, ontologie, reasoning | Proposition, Related Work |
| Must | [NetConfEval 2024](papers/Wang%20et%20al.%20-%202024%20-%20NetConfEval%20Can%20LLMs%20Facilitate%20Network%20Configuration.pdf) | état réel des LLMs pour la configuration réseau, benchmark sérieux | C2, Discussion, Eval |
| Must | [Confucius 2025](papers/Wang%20et%20al.%20-%202025%20-%20Intent-Driven%20Network%20Management%20with%20Multi-Agent%20LLMs%20The%20Confucius%20Framework.pdf) | multi-agent, outils, procédures, mémoire, validation en production | C2 agentique, Discussion |
| Must | [Matryoshka, NSDI 2026](https://www.usenix.org/conference/nsdi26/presentation/cai) | matérialisation automatique d'un design haut niveau en configurations concrètes | Related Work direct |
| Must | [Clarify, HotNets 2025](https://conferences.sigcomm.org/hotnets/2025/papers/hotnets25-final189.pdf) | le vrai problème n'est pas seulement l'hallucination, mais aussi l'ambiguïté de l'intent | Motivation du choix HLD structuré |

## Message principal de cette sélection

Le socle biblio du papier doit soutenir quatre idées:

1. Le problème n'est pas seulement l'exploitation d'un réseau existant, mais aussi la phase `T0`, quand on part d'un design.
2. Le HLD peut être lu comme une forme d'intent, mais il faut être rigoureux sur son type et son niveau d'abstraction.
3. Le vrai verrou scientifique est le passage du design à une représentation normalisée puis à des artefacts déployables.
4. L'agentic / LLM est utile, mais seulement s'il est encadré par structure, procédures, mémoire, outillage et validation.

## Références coeur par catégorie

### 1. Fondations IBN

#### [RFC 9315](papers/Clemm%20et%20al.%20-%202022%20-%20Intent-Based%20Networking%20-%20Concepts%20and%20Definitions.pdf)

À garder absolument.

Pourquoi:
- c'est la base terminologique;
- clarifie `intent`, `policy`, `fulfillment`, `assurance`;
- donne la structure de la boucle fermée et la distinction inner/outer loop.

Usage recommandé:
- Introduction: rappeler le cadrage classique d'IBN;
- Background: montrer ce que le papier reprend;
- Discussion: expliquer que le papier déplace l'application d'IBN plus tôt dans le cycle de vie.

#### [RFC 9316](papers/Li%20et%20al.%20-%202022%20-%20Intent%20Classification.pdf)

Très importante.

Pourquoi:
- évite de rester flou sur "quel type d'intent" représente un HLD;
- utile pour articuler `business intent`, `service intent`, `resource intent`;
- aide à justifier qu'un HLD n'est pas juste une config incomplète, mais un artefact d'intention à un niveau donné.

Usage recommandé:
- Background and Motivation;
- Discussion sur le concept de `design-time intent` ou `Intent Zero`;
- articulation de la contribution `C1`.

### 2. Motivation générale et design/planning

#### [Clemm et al. 2020](papers/Clemm%20et%20al.%20-%202020%20-%20Network%20Management%202030%20Operations%20and%20Control%20of%20Network%202030%20Services.pdf)

Pourquoi:
- bon papier de vision;
- crédibilise le besoin de réseaux plus automatisés, adaptatifs, analytiques.

À utiliser pour:
- l'ouverture de l'introduction;
- la motivation générale côté management réseau.

#### [Drakopoulos 1999](papers/Drakopoulos%20-%201999%20-%20Enterprise%20network%20planning%20and%20design%20methodology%20and%20application.pdf)

Pourquoi:
- montre que le design/planning d'entreprise est un processus structuré depuis longtemps;
- insiste sur le lien business requirements -> architecture -> planning -> dimensioning;
- renforce l'idée que votre problème n'est pas une simple variante moderne de génération de config.

À utiliser pour:
- la section lifecycle / HLD;
- la distinction design vs implementation.

#### [Sung et al. 2008](papers/Sung%20et%20al.%20-%202008%20-%20Towards%20systematic%20design%20of%20enterprise%20networks.pdf)

Probablement le meilleur papier du corpus pour appuyer votre gap.

Pourquoi:
- affirme explicitement que le design des réseaux d'entreprise est encore ad hoc;
- propose une approche systématique sous contraintes de performance, sécurité et résilience;
- très aligné avec votre cible SME / enterprise.

À utiliser pour:
- la motivation scientifique;
- le gap de recherche côté enterprise network design;
- l'idée qu'il faut passer du raisonnement manuel à une chaîne plus systématique.

### 3. Abstraction, représentation, matérialisation

#### [MALT / Mogul et al. 2020](papers/Mogul%20et%20al.%20-%20Experiences%20with%20Modeling%20Network%20Topologies%20at%20Multiple%20Levels%20of%20Abstraction.pdf)

Pourquoi:
- justifie le besoin de plusieurs niveaux d'abstraction;
- permet de penser le lien entre design, desired state, deployed state et as-built;
- utile même si le contexte initial est datacenter.

À utiliser pour:
- la proposition générale;
- la justification d'une représentation intermédiaire ou d'une source of truth.

#### [PRESTO / Enck et al. 2009](papers/Enck%20et%20al.%20-%202009%20-%20Configuration%20management%20at%20massive%20scale%20system%20design%20and%20experience.pdf)

Pourquoi:
- bon papier classique sur la génération et la maintenance de configurations à grande échelle;
- montre que la matérialisation en config est un vrai problème en soi;
- sert de point de comparaison: PRESTO part d'un niveau plus bas que votre HLD.

À utiliser pour:
- Related Work sur config generation;
- section prototype / implementation choices.

#### [SWIFT 2025](papers/Alcock%20et%20al.%20-%202025%20-%20SWIFT%20Semantic%20Web%20Intent%20Framework%20for%20Intent%20Translation.pdf)

Pourquoi:
- cadre très utile pour l'intent handler;
- ontologie + raisonnement + translation d'intent;
- plus structurant qu'un papier purement "LLM traduit du texte".

À utiliser pour:
- Related Work IBN/intention translation;
- discussion sur la structuration sémantique de l'entrée et de la transformation.

#### [Matryoshka, NSDI 2026](https://www.usenix.org/conference/nsdi26/presentation/cai)

Référence externe à ajouter absolument au `.bib`.

Pourquoi:
- très proche de votre angle, mais dans le contexte datacenter;
- conversion de designs / intents de haut niveau vers des configurations concrètes de switches;
- probablement la référence moderne la plus directement comparable.

À utiliser pour:
- Related Work direct;
- Discussion des différences avec votre papier:
  - datacenter vs enterprise;
  - design HLD humain vs design plus formalisé;
  - bootstrap initial d'un réseau SME.

### 4. Agentic / LLM

#### [NetConfEval 2024](papers/Wang%20et%20al.%20-%202024%20-%20NetConfEval%20Can%20LLMs%20Facilitate%20Network%20Configuration.pdf)

Référence coeur.

Pourquoi:
- benchmark sérieux;
- montre où les LLMs aident réellement et où ils restent fragiles;
- évite un discours trop spéculatif sur "les LLMs savent faire la config".

À utiliser pour:
- votre contribution `C2`;
- Discussion sur les limites et les garde-fous;
- éventuelle partie Eval sur types de modèles.

#### [Confucius 2025](papers/Wang%20et%20al.%20-%202025%20-%20Intent-Driven%20Network%20Management%20with%20Multi-Agent%20LLMs%20The%20Confucius%20Framework.pdf)

Très importante pour la future écriture de `C2`.

Pourquoi:
- meilleure référence agentique du lot;
- multi-agent, outils, procédures structurées, short-term / long-term memory, validation;
- basée sur une vraie expérience de production.

À utiliser pour:
- proposition agentique high-level;
- justification du besoin de mémoire, procédures et outillage;
- discussion sur le fait qu'un LLM seul ne suffit pas.

#### [Clarify, HotNets 2025](https://conferences.sigcomm.org/hotnets/2025/papers/hotnets25-final189.pdf)

Référence externe très utile.

Pourquoi:
- message central: le vrai problème est souvent l'ambiguïté de l'intent, pas seulement l'hallucination;
- renforce votre choix d'une entrée HLD structurée au lieu d'un simple prompt.

À utiliser pour:
- la motivation du format d'entrée;
- la discussion sur les limites des approches purement conversationnelles.

## Références de réserve

À garder sous la main, mais pas dans le noyau dur initial.

### Réserve utile

- [Falkner et Apostolopoulos 2022](papers/Falkner%20et%20Apostolopoulos%20-%202022%20-%20Intent-based%20networking%20for%20the%20enterprise%20a%20modern%20network%20architecture.pdf)  
  Utile pour le contexte enterprise IBN, mais plutôt papier d'orientation.

- [El Rajab et al. 2024](papers/El%20Rajab%20et%20al.%20-%202024%20-%20Zero-touch%20networks%20Towards%20next-generation%20network%20automation.pdf)  
  Bon survey ZSM / zero-touch; à citer si vous voulez élargir le contexte.

- [Bovenzi et al. 2025](papers/Bovenzi%20et%20al.%20-%202025%20-%20Mapping%20the%20Landscape%20of%20Generative%20AI%20in%20Network%20Monitoring%20and%20Management.pdf)  
  Très bon survey GenAI pour network management; utile si la partie agentic prend de la place.

- [Canavese et al. 2025](papers/Canavese%20et%20al.%20-%202025%20-%20Game%20of%20Zones%20An%20Automated%20Intent-Based%20Network%20Micro-segmentation%20Methodology.pdf)  
  Bon exemple d'application IBN à un problème spécifique.

- [Dzeparoska et Leon-Garcia 2025](papers/Dzeparoska%20et%20Leon-Garcia%20-%202025%20-%20KPI%20Assurance%20and%20LLMs%20for%20Intent-Based%20Management.pdf)  
  Plutôt utile pour assurance que pour votre coeur design-to-deployment.

### Réserve plus périphérique

- [Brodimas et al. 2025](papers/Brodimas%20et%20al.%20-%202025%20-%20Intent-Based%20Infrastructure%20and%20Service%20Orchestration%20Using%20Agentic-AI.pdf)
- [Guo et al. 2025](papers/Guo%20et%20al.%20-%202025%20-%20Intent-Based%20Autonomous%20Network%20Framework%20Guided%20by%20Large%20Language%20Model.pdf)
- [Angi et al. 2025 / LLNet](papers/Angi%20et%20al.%20-%202025%20-%20LLNet%20An%20Intent-Driven%20Approach%20to%20Instructing%20Softwarized%20Network%20Devices%20Using%20a%20Small%20Language%20M.pdf)
- [Van Tu et al. 2024 / NFV-Intent](papers/Van%20Tu%20et%20al.%20-%202024%20-%20Towards%20Intent-based%20Configuration%20for%20Network%20Function%20Virtualization%20using%20In-context%20Learning%20in.pdf)
- [Wei et al. 2025 / INTA](papers/Wei%20et%20al.%20-%202025%20-%20INTA%20Intent-Based%20Translation%20for%20Network%20Configuration%20with%20LLM%20Agents.pdf)

Ces papiers sont intéressants, mais ils sont:
- soit trop centrés telco / NFV / orchestration de services;
- soit trop focalisés sur la traduction de configuration;
- soit moins structurants pour votre angle HLD -> réseau initial.

## Scan externe rapide 2024-2026

Objectif de ce scan:
- identifier quelques papiers non présents localement qui renforcent vraiment le papier;
- éviter d'ajouter trop de bruit.

### Très pertinents

- [Matryoshka, NSDI 2026](https://www.usenix.org/conference/nsdi26/presentation/cai)  
  Le plus important à ajouter hors corpus local.

- [Clarify, HotNets 2025](https://conferences.sigcomm.org/hotnets/2025/papers/hotnets25-final189.pdf)  
  Très utile pour le problème d'ambiguïté de l'intent.

- [Lightweight Automated Reasoning for Network Architectures, HotNets 2024](https://conferences.sigcomm.org/hotnets/2024/papers/hotnets24-74.pdf)  
  Très bon appui pour l'idée que le design réseau devient trop complexe pour rester un exercice manuel.

### Intéressants mais secondaires

- [NetLLM, SIGCOMM 2024 program](https://conferences.sigcomm.org/sigcomm/2024/program/)  
  Intéressant pour le panorama LLM + networking, mais moins directement lié à votre angle HLD/design.

- [S2Sim, NSDI 2026](https://www.usenix.org/conference/nsdi26/presentation/yang)  
  Très bien pour repair / assurance / future work, moins central pour ce papier.

## Recommandation pratique pour la première écriture

Pour une première version du papier, je recommande:

### Bloc minimal indispensable

1. RFC 9315
2. RFC 9316
3. Clemm 2020
4. Drakopoulos 1999
5. Sung et al. 2008
6. MALT
7. PRESTO
8. SWIFT
9. NetConfEval
10. Confucius
11. Matryoshka
12. Clarify

### Si la pression de place devient forte

Les deux premières références à sortir du noyau dur seraient:
- Clemm 2020
- PRESTO

Pas parce qu'elles sont faibles, mais parce qu'elles sont moins directement décisives que:
- les deux RFC,
- Sung,
- MALT,
- NetConfEval,
- Confucius,
- Matryoshka.

## Ce que cette sélection permet de raconter

Cette bibliographie permet de raconter un papier cohérent:

- `RFC 9315 + RFC 9316`:
  l'intent est bien défini et classifiable;
- `Drakopoulos + Sung + HotNets 2024`:
  le design/planning réseau est un vrai problème scientifique, ancien et toujours insuffisamment outillé;
- `MALT + PRESTO + SWIFT + Matryoshka`:
  la transformation d'un niveau abstrait vers des artefacts déployables nécessite structure, représentation et matérialisation;
- `NetConfEval + Confucius + Clarify`:
  l'agentic et les LLMs sont utiles, mais seulement avec procédures, mémoire, récupération de contexte et réduction d'ambiguïté.

## Conclusion opérationnelle

Le coeur du papier ne doit pas être:
- "on a un système multi-agent";
- ni "on utilise des LLMs pour faire du réseau".

Le coeur du papier doit être:
- "le HLD est un artefact d'intention exploitable à T0";
- "le gap scientifique est le passage design -> matérialisation initiale du réseau";
- "l'agentic est le moyen moderne pour opérer cette transformation, pas l'unique message".

