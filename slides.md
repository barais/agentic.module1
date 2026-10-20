---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Module 1 - Grands Modèles de Langage (Le Socle)
info: |
  ## Cours Agentic AI 
# apply UnoCSS classes to the current slide
class: text-center
# https://sli.dev/features/drawing
pdf: true
export: true
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable Comark Syntax: https://comark.dev/syntax/markdown
comark: true
download: true
# duration of the presentation
duration: 10min
---

# Module 1 : Grands Modèles de Langage (LLM)
## Le socle de compréhension avant l'ère agentique

<div class="pt-12">
  <span class="px-3 py-1 rounded bg-emerald-600/60 text-sm font-mono">Socle technique & conceptuel</span>
  <p class="mt-4 text-gray-300 text-sm">D'après les retours d'expérience et travaux académiques (Univ. Rennes / Inria DiverSE)</p>
</div>

---
layout: default
---

# 1. Le principe fondamental : la boîte noire

<div class="text-xl text-emerald-600 font-semibold mb-6">
  « Un LLM n'est ni un oracle, ni une base de données de faits : c'est un prédicteur statistique. »
</div>

<div class="grid grid-cols-3 gap-4 my-6 items-center text-center">
  <div class="p-4 rounded-xl border border-gray-300 bg-gray-50 dark:bg-gray-800">
    <div class="font-bold text-lg">Texte en entrée (Prompt)</div>
    <div class="text-xs text-gray-500 mt-2 font-mono">"Le chat mange la..."</div>
  </div>
  <div class="p-4 rounded-xl border-2 border-emerald-500 bg-emerald-50 dark:bg-emerald-950 font-mono text-sm">
    <div class="font-bold">Boîte noire (LLM)</div>
    <div class="text-xs text-gray-500 mt-1">100B+ paramètres</div>
    <div class="text-xs text-emerald-600 mt-1">P(token | contexte)</div>
  </div>
  <div class="p-4 rounded-xl border border-gray-300 bg-gray-50 dark:bg-gray-800">
    <div class="font-bold text-lg">Prochain token</div>
    <div class="text-xs text-emerald-500 mt-2 font-mono font-bold">"souris" (87%)</div>
  </div>
</div>

<v-clicks>

- **Génération auto-régressive :** il injecte le token prédit à la fin de la phrase et recommence, mot après mot.
- **Illusion de pensée :** La cohérence apparente découle d'un calcul de vraisemblance sur des téraoctets de données textuelles humaines.
- **Règle d'or :** Demander un fait brut à un modèle pur sans outil externe est une erreur de casting conceptuelle.

</v-clicks>

---
layout: two-cols-header
---

# 2. Qu'est-ce qu'il sait faire ?

Un couteau suisse protéiforme pour le traitement textuel :

::left::
<v-clicks>

- ✍️ **Génération & Reformulation**
  - Rédaction, adaptation de style, synthèse de documents longs
- 🔄 **Traduction universelle**
  - Entre langues naturelles (FR ↔ EN)
  - Vers des formats structurés (Texte ↔ JSON, SQL, RegExp)
- 💻 **Programmation assistée**
  - Écriture de boilerplate, détection de bugs, conversion de langages (Python ↔ OCaml)

</v-clicks>

::right::
<div class="ml-6 p-4 rounded-lg bg-gray-100 dark:bg-gray-800 border-l-4 border-amber-500">
  <div class="font-bold text-amber-600">Le piège de la posture</div>
  <p class="text-sm mt-2">
    <i>« Bottes de 7 lieues si on comprend ce qu'on fait, déconnecteur de cerveau sinon. »</i>
  </p>
  <p class="text-xs text-gray-500 mt-2">
    Le LLM produit du code ou des textes plausibles, jamais garantis formellement corrects sans validation humaine ou outillée.
  </p>
</div>

---
layout: default
---

# 3. Sous le capot (1/2) : Des mots aux Tokens

Un modèle ne lit pas des lettres, il manipule des identifiants discrets dans un espace vectoriel.

<div class="grid grid-cols-2 gap-6 mt-6">
<div>

### Tokenisation
- Découpe en sous-mots fréquents (ex. BPE / Byte-Pair Encoding)
- *« Évolution »* $\rightarrow$ `['Évol', 'ution']`
- Permet de gérer le vocabulaire inconnu, les langues rares et le code source
- **Conséquence :** Les modèles ont du mal à compter les lettres ou inverser des chaînes !

</div>
<div>

### Plongement (Embeddings)
- Chaque token devient un vecteur continu (ex. 4096 à 12288 dimensions)
- Les mots de sens proche se regroupent géométriquement
- Capture les régularités sémantiques et syntaxiques

```
"chat"    -> [ 0.12, -0.45,  0.89, ... ]
"félin"   -> [ 0.11, -0.41,  0.85, ... ]
```

</div>
</div>

---
layout: default
---

# 4. Sous le capot (2/2) : Le Transformer & l'Attention

<div class="grid grid-cols-3 gap-4 mb-6">
  <div class="p-3 bg-gray-50 dark:bg-gray-800 rounded">
    <div class="text-emerald-500 font-bold">1990 - 2010</div>
    <div class="text-sm font-semibold">Règles & RNN/LSTM</div>
    <div class="text-xs text-gray-500">Traitement séquentiel, perte de mémoire sur les textes longs.</div>
  </div>
  <div class="p-3 bg-gray-50 dark:bg-gray-800 rounded">
    <div class="text-emerald-500 font-bold">2017 (Vaswani et al.)</div>
    <div class="text-sm font-semibold">Architecture Transformer</div>
    <div class="text-xs text-gray-500">Parallélisation massive et mécanisme d'attention globale.</div>
  </div>
  <div class="p-3 bg-emerald-50 dark:bg-emerald-950 rounded border border-emerald-500">
    <div class="text-emerald-600 font-bold">2020+</div>
    <div class="text-sm font-semibold">Scaling Laws (LLM)</div>
    <div class="text-xs text-gray-500">Empilement de couches d'attention (96+ blocs, >100B params).</div>
  </div>
</div>

### L'Attention en une phrase :
Chaque token recalcule sa signification en « regardant » tous les autres tokens du contexte :
- Dans *"La banque de France"* et *"La banque de la rivière"*, le mot **banque** reçoit une projection vectorielle différente grâce aux mots voisins.

---
layout: two-cols-header
---

# 5. Du texte brut au dialogue : Le cycle d'entraînement

::left::
### Étape 1 : Pré-entraînement
- Ingestion de téraoctets de données (Common Crawl, GitHub, livres)
- Objectif trivial : deviner le mot suivant
- Coût titanesque (millions d'euros en GPU A100/H100)
- **Résultat :** Un modèle "brut" (Base model) qui complète du texte, sans esprit de conversation.

::right::
<div class="ml-4">

### Étape 2 : Post-entraînement
- **SFT (Supervised Fine-Tuning) :** Apprentissage sur des dialogues `Question / Réponse` très qualitatifs
- **Alignement (RLHF / DPO) :** Ajustement par préférences humaines pour rendre le modèle utile, poli et refuser les demandes toxiques
- **Résultat :** L'assistant conversationnel (ChatGPT, Claude, Llama-Chat)

</div>

---
layout: default
---

# 6. Capacités émergentes : Quand l'échelle change tout

En augmentant la taille des modèles et des données, de nouveaux comportements apparaissent sans entraînement explicite :

<div class="grid grid-cols-3 gap-1 mt-1">
<div class="p-2 bg-gray-50 dark:bg-gray-800 rounded-lg">

#### In-Context Learning
<p class="text-sm">Le modèle adapte sa dynamique en lisant simplement des exemples dans le prompt, sans modifier ses poids internes.</p>
</div>
<div class="p-2 bg-gray-50 dark:bg-gray-800 rounded-lg">

#### Instruction Following
<p class="text-sm">Capacité à décomposer des consignes complexes comportant des contraintes négatives (*« sans utiliser la lettre E »*).</p>
</div>
<div class="p-2 bg-gray-50 dark:bg-gray-800 rounded-lg">

#### Décomposition
<p class="text-sm">Capacité à amorcer un pseudo-raisonnement symbolique si on le force à expliciter les étapes intermédiaires.</p>
</div>
</div>
<!-- Encart ajouté : débat sur l'émergence -->
<div class="mt-3 p-2 rounded-lg border border-indigo-500/50 bg-indigo-50/80 dark:bg-indigo-950/40">
  <div class="font-bold text-indigo-600">⚠️ « Émergence » : un terme débattu</div>
  <p class="text-sm mt-1">
    Ces comportements semblent « apparaître » au-delà d'un seuil de taille, mais l'article fondateur
    <i>« Are Emergent Abilities of Large Language Models a Mirage? »</i> (Schaeffer et al., 2023)
    montre qu'une partie de cette soudaineté pourrait être un <b>artefact de mesure</b> :
    selon la métrique ou l'échantillonnage choisis, une progression continue peut <i>paraître</i> émerger d'un coup.
  </p>
  <p class="text-sm mt-1">
    <b>Concrètement pour vous :</b> ces capacités sont <b>réelles et utilisables</b>, mais elles sont souvent
    <b>continues et prévisibles</b> plutôt que magiques. Réflexe : testez le modèle sur <b>votre</b> tâche réelle,
    ne vous fiez jamais aux seuls scores publiés.
  </p>
</div>

---
layout: default
---

# 7. Les limites fondamentales



Ne jamais oublier ce qu'est la boîte noire :

<div class="grid grid-cols-2 gap-6 mt-4">
<div>

- 🍄 **Hallucinations**
  - Formulation très affirmative d'affirmations totalement inventées (biographies, papiers académiques inexistants).
  - *Inhérent au principe statistique : vraisemblable $\neq$ vrai.*

- 📏 **Fenêtre de contexte finie**
  - Même avec des contextes à 128k/1M tokens : phénomène du *"Lost in the middle"* (l'attention baisse au centre du document).

</div>
<div>

- 🎲 **Non-déterminisme & Stabilité**
  - Deux prompts identiques peuvent donner des résultats divergents (température > 0).
  - Fragilité lors de retours itératifs de code : le modèle tend à oublier les contraintes de départ.

- 💰 **Coûts & Bilan Écologique**
  - Inférence coûteuse en énergie et mémoire GPU.

</div>

</div>

---
layout: default
---

# 7. Les limites fondamentales



Ne jamais oublier comment la boîte noire est entrainée :
<!-- Encart ajouté : Biais & Représentations -->
<div class="mt-4 p-4 rounded-lg border border-amber-500/60 bg-amber-50/80 dark:bg-amber-950/40">
  <div class="font-bold text-amber-600">⚖️ Biais & Représentations</div>
  <div class="grid grid-cols-3 gap-4 text-sm mt-2">
    <div>
      <div class="font-semibold text-amber-600">Le problème</div>
      Le modèle <b>reproduit et amplifie</b> les biais de ses données d'entraînement : stéréotypes
      de genre, d'ethnicité, de langue ou de classe sociale.
    </div>
    <div>
      <div class="font-semibold text-amber-600">Le risque côté développeur</div>
      Tri de CV, modération, scoring automatique… un biais non détecté devient une
      <b>décision outillée discriminatoire</b> et difficile à tracer.
    </div>
    <div>
      <div class="font-semibold text-amber-600">Les garde-fous</div>
      • Évaluer avant déploiement (ex. benchmarks <i>BBQ</i>, <i>Winogender</i>)<br>
      • Mesurer les disparités par sous-population<br>
      • Soigner le prompt et les sources du RAG (un RAG biaisé propage ses biais)
    </div>
  </div>
</div>

---
layout: default
---

# 8. Guider la boîte noire : Prompt Engineering

Le prompt structure l'espace latent du modèle pour maximiser la pertinence de la réponse.

```markdown
<!-- Mauvais prompt -->
Écris une fonction de tri en Python.
```

```markdown
<!-- Bon prompt (Rôle + Contexte + Contraintes + Format d'entrée/sortie) -->
Tu es un ingénieur senior Python spécialisé en algorithmique distribuée.
Écris une fonction de tri par fusion pour une liste d'entiers non triée.
Contraintes :
- Complexité temporelle attendue : O(n log n)
- N'utilise aucune bibliothèque externe
- Inclus les annotations de type (type hints) et une docstring exhaustive
Retourne uniquement le bloc de code Python.
```

💡 **Chain-of-Thought (CoT) :** Ajouter *« Réfléchissons étape par étape »* force le modèle à générer des tokens intermédiaires avant d'arrêter sa conclusion.

---
layout: two-cols-header

---

# 9. La nouvelle frontière : "Reasoning Models"

<div class="text-sm text-gray-500 mb-4">Paradigme Test-Time Compute (ex. OpenAI o1/o3, DeepSeek-R1)</div>

::left::
<div>

### Modèles classiques (style GPT-4o)
- Planifient « en interne » dans leurs poids, mais n'allouent **aucun budget de calcul dédié** avant d'entamer leur réponse
- Coût de calcul fixé uniquement par la longueur de la réponse générée

### Modèles à raisonnement (OpenAI o1/o3, DeepSeek-R1)
- Allouent du **temps de calcul supplémentaire à l'inférence** (*test-time compute*) pour « réfléchir » avant la réponse finale
- **Distinction clé entre les deux familles :**
  - **DeepSeek-R1** : la chaîne de pensée est générée sous forme de **tokens visibles** dans le contexte (entraînée par RL) — mécanisme **documenté, observable, reproductible**.
  - **OpenAI o1/o3** : le mécanisme interne **n'a jamais été publié** ; on constate seulement que le budget de calcul augmente. Parler de « *hidden CoT* » est donc une **hypothèse externe, pas un fait technique**.
  
</div>

::right::

<div class="p-4 bg-emerald-50 dark:bg-emerald-950 border border-emerald-600 rounded-xl">
  <div class="font-bold text-emerald-600 text-lg">Le shift conceptuel</div>
  <p class="text-sm mt-2">
    On ne paie plus seulement pour la taille du modèle (taille des poids), mais pour le <b>temps de réflexion</b> alloué à l'inférence.
  </p>
<div class="mt-3 text-xs font-mono text-gray-400">
    Plus de test-time compute = erreurs en forte baisse sur les maths & le code,
    mais gains marginaux ailleurs (rédaction, traduction).
  </div>
</div>

<style>
.slidev-layout.two-columns {
  grid-template-columns: 65% 35%;
}
/* style.css */
.slidev-layout.two-cols-header {
  grid-template-columns: 3fr 2fr;
}
li {
  font-size: 0.8em;
}
</style>
---
layout: default
---

# 10. RAG : Brancher le modèle sur le réel

<div class="font-semibold text-emerald-600 mb-2">Retrieval-Augmented Generation (Génération Augmentée par Récupération)</div>

Le LLM apporte le **moteur linguistique**, la base documentaire apporte **des sources contrôlées**,
pas une garantie de vérité.
```
[Question utilisateur]
         │
         ├──► 1. Recherche sémantique dans vos documents (Vector Store)
         │       └─ Extrait : "Les bourses de stage 2026 s'élèvent à 650€/mois"
         │
         ▼
[Nouveau Prompt envoyé au LLM] :
"Réponds à la question en te basant STRICTEMENT sur l'extrait ci-dessous :
 Extrait : [Les bourses de stage 2026 s'élèvent à 650€/mois]
 Question : Quel est le montant de la bourse ?"
         │
         ▼
[Réponse fiable et sourcée]
```

👉 **Différence clé :** Le RAG *injecte de l'information* au moment du prompt. Il ne modifie pas les connaissances intrinsèques du modèle.

---
layout: default
---

# 10. RAG : Brancher le modèle sur le réel


<!-- Encart ajouté : RAG ≠ garantie d'exactitude -->
<div class="mt-4 p-4 rounded-lg border border-rose-500/60 bg-rose-50/80 dark:bg-rose-950/40">
  <div class="font-bold text-rose-600">⚠️ RAG ≠ garantie d'exactitude</div>
  <div class="grid grid-cols-3 gap-4 text-sm mt-2">
    <div>
      <div class="font-semibold text-rose-600">Pourquoi ça peut encore échouer</div>
      - Récupération ratée (mauvais chunk, info éparpillée sur 50 pages)<br>
      - Le modèle <b>suit un prompt, pas une obligation</b> : il peut ignorer l'extrait ou halluciner en plus<br>
      - Information absente de la base → aucune chance de réponse correcte<br>
      - Source erronée ou biaisée → erreur propagée (<i>garbage in, garbage out</i>)
    </div>
    <div>
      <div class="font-semibold text-rose-600">Ce que RAG améliore réellement</div>
      - La <b>fraîcheur</b> des connaissances (documents à jour à la seconde)<br>
      - La <b>traçabilité</b> (citations et sources vérifiables)<br>
      - Le <b>périmètre</b> : la réponse est bornée à un corpus maîtrisé
    </div>
    <div>
      <div class="font-semibold text-rose-600">Réflexes à conserver</div>
      - Instruire le modèle : « si l'extrait ne contient pas la réponse, dis-le »<br>
      - Évaluer la qualité de la recherche à part (<i>retrieval eval</i>), pas seulement la réponse finale<br>
      - Vérifier les citations avant diffusion : <b>RAG = traçable, pas certifié</b>
    </div>
  </div>
</div>

---
layout: default
---

# 11. Comment adapter ? L'arbre de décision

Avant de vouloir ré-entraîner un modèle, il existe une hiérarchie stricte d'effort et de coût :

<div class="grid grid-cols-3 gap-2 mt-3">
<div class="p-2 border rounded-lg bg-gray-50 dark:bg-gray-800">

### 1. Prompting & Few-Shot
**Quand ?** Tâches générales, génération standard, extraction ponctuelle.  
**Coût :** Négligeable.  
**Limites :** Dépendant de la taille du contexte.

</div>
<div class="p-2 border-2 border-emerald-500 rounded-lg bg-emerald-50 dark:bg-emerald-950">

### 2. RAG
**Quand ?** Données d'entreprise récentes, documents privés, besoin de traçabilité des sources.  
**Coût :** Modéré (infra de recherche).  
**Limites :** Qualité du chunking et de la recherche.

</div>
<div class="p-2 border rounded-lg bg-gray-50 dark:bg-gray-800">

### 3. Fine-Tuning
**Quand ?** Apprendre un **style**, une syntaxe de code propriétaire ou un jargon hermétique.  
**Attention :** Mauvaise méthode pour injecter de nouveaux faits !

</div>
</div>

<!-- Encart ajouté : évaluation -->
<div class="mt-3 p-2 rounded-lg border border-sky-500/50 bg-sky-50/80 dark:bg-sky-950/40">
  <div class="font-bold text-sky-600">📊 Avant de choisir, mesurer : l'évaluation n'est pas optionnelle</div>
  <p class="text-sm mt-2">
    - Constituer un <b>jeu de test représentatif de son cas réel</b> (une vingtaine d'entrées typiques) et comparer
    modèles, prompts et variantes RAG sur ce jeu — c'est la compétence la plus rentable de ce module.<br>
    - Repères publics : <i>MMLU</i> (culture générale), <i>HumanEval / LiveCodeBench</i> (code),
    <i>GSM8K</i> (raisonnement mathématique), <i>BBQ</i> (biais).<br>
    - Règle d'or : un benchmark public sert à <b>repérer</b> des modèles, jamais à <b>choisir</b> pour son cas.    seul votre <i>golden set</i> fait foi.
  </p>
</div>

<style>
h3 {
  font-size: 1.2em;
}

p {
  font-size: 0.8em;
}
</style>

---
layout: default
---

# RAG vs Fine-Tuning vs Contexte Massif (1M+)



Trois manières très différentes d'apporter de la spécificité à un LLM :

<div class="grid grid-cols-3 gap-3 mt-4 text-xs">

<!-- COLONNE 1 : RAG -->
<div class="p-3 border rounded-lg bg-gray-50 dark:bg-gray-800 flex flex-col justify-between">
  <div>
    <div class="font-bold text-sm text-blue-500 mb-1">1. RAG (Recherche)</div>
    <div class="text-gray-400 mb-2 italic">« Va chercher la page précise »</div>
    <div class="text-emerald-500 font-semibold mb-1">Avantages :</div>
    <ul class="space-y-1 mb-2">
      <li>Données fraîches & modifiables à la seconde</li>
      <li><b>Traçabilité :</b> citations et sources vérifiables</li>
      <li>Gestion fine des droits d'accès (ACL/RBAC)</li>
    </ul>
    <div class="text-red-500 font-semibold mb-1">Inconvénients :</div>
    <ul class="space-y-1">
      <li>Pipeline lourd (chunking, vecteurs, reranking)</li>
      <li>Échec si l'information est éparpillée sur 50 pages</li>
    </ul>
  </div>
  <div class="mt-3 pt-2 border-t border-gray-200 dark:border-gray-700 font-medium text-gray-500">
    🎯 <b>Idéal pour :</b> Base documentaire vivante, FAQ, conformité juridique.
  </div>
</div>

<!-- COLONNE 2 : LONG CONTEXT -->
<div class="p-3 border rounded-lg bg-gray-50 dark:bg-gray-800 flex flex-col justify-between">
  <div>
<div class="font-bold text-sm text-purple-500 mb-1">2. Contexte long (fenêtres 1M+ tokens) 2026 — Gemini, GPT, Claude Sonnet, DeepSeek, Llama…</div>    <div class="text-gray-400 mb-2 italic">« Prends tout le dossier d'un coup »</div>
    <div class="text-emerald-500 font-semibold mb-1">Avantages :</div>
    <ul class="space-y-1 mb-2">
      <li>Zéro infra complexe : un seul prompt géant</li>
      <li><b>Vue globale :</b> croise les chapitres/fichiers sans perte de contexte</li>
      <li>Analyse tout un repo de code ou un livre</li>
    </ul>
    <div class="text-red-500 font-semibold mb-1">Inconvénients :</div>
    <ul class="space-y-1">
      <li>Coût et latence (TTFT) élevés par requête</li>
      <li>Risque d'inattention au milieu (<i>Lost in the middle</i>)</li>
      <li>Ne remplace pas une base d'entreprise (capacité finie)</li>
    </ul>
  </div>
  <div class="mt-3 pt-2 border-t border-gray-200 dark:border-gray-700 font-medium text-gray-500">
    🎯 <b>Idéal pour :</b> Audit de code, analyse comparative de bilans financiers complets.
  </div>
</div>

<!-- COLONNE 3 : FINE-TUNING -->
<div class="p-3 border rounded-lg bg-gray-50 dark:bg-gray-800 flex flex-col justify-between">
  <div>
    <div class="font-bold text-sm text-amber-500 mb-1">3. Fine-Tuning</div>
    <div class="text-gray-400 mb-2 italic">« Modifie tes réflexes et ton style »</div>
    <div class="text-emerald-500 font-semibold mb-1">Avantages :</div>
    <ul class="space-y-1 mb-2">
      <li>Maîtrise absolue du format (JSON strict, DSL)</li>
      <li>Réduit les prompts (plus besoin de 10 exemples)</li>
      <li>Modèle plus petit = inférence rapide & autonome</li>
    </ul>
    <div class="text-red-500 font-semibold mb-1">Inconvénients :</div>
    <ul class="space-y-1">
      <li><b>Mauvais pour mémoriser des faits</b> (hallucine)</li>
      <li>Connaissances figées dans le temps</li>
    </ul>
  </div>
  <div class="mt-3 pt-2 border-t border-gray-200 dark:border-gray-700 font-medium text-gray-500">
    🎯 <b>Idéal pour :</b> Langage métier hermétique, respect d'une syntaxe propriétaire.
  </div>
</div>

</div>

<!-- SYNTHÈSE / RÈGLE EMPIRIQUE -->
<div class="mt-4 p-2 bg-emerald-50 dark:bg-emerald-950 border border-emerald-500/40 rounded text-center text-xs">
  💡 <b>La règle du terrain :</b> RAG pour les <i>connaissances</i> · Contexte 1M pour le <i>raisonnement global ponctuel</i> · Fine-Tuning pour la <i>forme et le comportement</i>.
</div>

<style>
h3 {
  font-size: 1.2em;
}
li {
  font-size: 0.8em;
}
</style>



---
layout: default
---

# 🧠 Ce qu'il faut retenir de ce premier module

<div class="grid grid-cols-2 gap-4 mt-4">

<div class="p-3 rounded-lg border border-emerald-500/60 bg-emerald-50/80 dark:bg-emerald-950/40">
  <div class="font-bold text-emerald-600 mb-1">🤖 La nature du LLM</div>
  <ul class="text-sm space-y-1">
    <li>Un <b>prédicteur statistique</b>, pas un oracle ni une base de faits</li>
    <li>Il génère le <b>token suivant</b>, de façon auto-régressive, mot après mot</li>
    <li>Règle d'or : <b><i>vraisemblable ≠ vrai</i></b> → toujours vérifier</li>
  </ul>
</div>

<div class="p-3 rounded-lg border border-emerald-500/60 bg-emerald-50/80 dark:bg-emerald-950/40">
  <div class="font-bold text-emerald-600 mb-1">💪 Ce qu'il sait faire</div>
  <ul class="text-sm space-y-1">
    <li>Structurer, synthétiser, reformuler, traduire, coder</li>
    <li><b>In-context learning :</b> apprend d'exemples placés dans le prompt, sans modifier ses poids</li>
    <li><b>CoT :</b> raisonner par décomposition si on le force à expliciter ses étapes</li>
  </ul>
</div>

<div class="p-3 rounded-lg border border-rose-500/60 bg-rose-50/80 dark:bg-rose-950/40">
  <div class="font-bold text-rose-600 mb-1">⚠️ Ses limites</div>
  <ul class="text-sm space-y-1">
    <li><b>Hallucinations :</b> affirmatif mais faux — inhérent au principe statistique</li>
    <li>Fenêtre de contexte finie (<i>lost in the middle</i>)</li>
    <li>Non-déterminisme (température) & <b>biais</b> hérités des données</li>
  </ul>
</div>

<div class="p-3 rounded-lg border border-sky-500/60 bg-sky-50/80 dark:bg-sky-950/40">
  <div class="font-bold text-sky-600 mb-1">🔧 Nos leviers</div>
  <ul class="text-sm space-y-1">
    <li><b>Prompting :</b> rôle + contexte + contraintes + format (le moins cher)</li>
    <li><b>RAG :</b> injecter des sources fraîches, traçables — mais pas certifiées</li>
    <li><b>Reasoning models :</b> payer du temps de réflexion (test-time compute)</li>
    <li>Fine-tuning : pour ajuster la forme & style, pas pour apprendre des faits</li>
  </ul>
</div>

</div>

<div class="mt-1 p-1 rounded-lg bg-gray-100 dark:bg-gray-800 border-l-1 border-amber-500">
  <p class="text-sm">
    Avant de choisir un modèle, un prompt ou une architecture : <b>construire un jeu de test représentatif de votre cas réel</b>
     les benchmarks publics servent à repérer, seul votre <i>golden set</i> fait foi.
  </p>
</div>

<div class="mt-2 text-center text-xs text-gray-400">
  Socle acquis : la boîte noire, ses forces, ses limites, et nos leviers pour la guider...
</div>

<style>
h3 {
  font-size: 1.2em;
}
li {
  font-size: 0.8em;
}
p {
  font-size: 0.8em;
}
</style>

---
layout: end
class: text-center
---

# Fin du Module 1
### Place aux échanges & questions !

  <p class="text-sm mt-1">
   <b>un LLM isolé sait « parler »</b>. Il ne devient un
    <b>Agent</b> qu'avec des <b>outils</b>, une <b>boucle de décision</b> et une <b>mémoire persistante</b> → <a href="https://olivier.barais.fr/agentic.module2/">Module 2</a> !
  </p>


[DiverSE Univ. Rennes](http://www.diverse-team.fr) © 2026 


