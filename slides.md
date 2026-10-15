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
# duration of the presentation
duration: 35min
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

<div class="grid grid-cols-3 gap-6 mt-6">
<div class="p-4 bg-gray-50 dark:bg-gray-800 rounded-lg">

### In-Context Learning
Le modèle adapte sa dynamique en lisant simplement des exemples dans le prompt, sans modifier ses poids internes.

</div>
<div class="p-4 bg-gray-50 dark:bg-gray-800 rounded-lg">

### Instruction Following
Capacité à décomposer des consignes complexes comportant des contraintes négatives (*« sans utiliser la lettre E »*).

</div>
<div class="p-4 bg-gray-50 dark:bg-gray-800 rounded-lg">

### Décomposition
Capacité à amorcer un pseudo-raisonnement symbolique si on le force à expliciter les étapes intermédiaires.

</div>
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
layout: default
---

# 9. La nouvelle frontière : "Reasoning Models"

<div class="text-sm text-gray-500 mb-4">Paradigme Test-Time Compute (ex. OpenAI o1/o3, DeepSeek-R1)</div>

<div class="grid grid-cols-2 gap-8 items-center">
<div>

### Modèles classiques (Style GPT-4o)
- Répond immédiatement dès le premier token généré
- Coût de calcul fixé uniquement par la longueur de la réponse finale

### Modèles à raisonnement
- Allouent du temps de calcul **avant** d'afficher la réponse
- Génèrent une chaîne de pensée interne cachée (*Hidden CoT*)
- Auto-correction, exploration d'arbres de recherche et retour en arrière

</div>

<div class="p-4 bg-emerald-50 dark:bg-emerald-950 border border-emerald-600 rounded-xl">
  <div class="font-bold text-emerald-600 text-lg">Le shift conceptuel</div>
  <p class="text-sm mt-2">
    On ne paie plus seulement pour la taille du modèle (taille des poids), mais pour le <b>temps de réflexion</b> alloué à l'inférence.
  </p>
  <div class="mt-3 text-xs font-mono text-gray-400">
    Plus de test-time compute = taux d'erreur en chute libre sur les maths & le code.
  </div>
</div>
</div>

---
layout: default
---

# 10. RAG : Brancher le modèle sur le réel

<div class="font-semibold text-emerald-600 mb-2">Retrieval-Augmented Generation (Génération Augmentée par Récupération)</div>

Le LLM apporte le **moteur linguistique**, une base documentaire apporte la **vérité terrain**.

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

# 11. Comment adapter ? L'arbre de décision

Avant de vouloir ré-entraîner un modèle, il existe une hiérarchie stricte d'effort et de coût :

<div class="grid grid-cols-3 gap-4 mt-6">
<div class="p-4 border rounded-lg bg-gray-50 dark:bg-gray-800">

### 1. Prompting & Few-Shot
**Quand ?** Tâches générales, génération standard, extraction ponctuelle.  
**Coût :** Négligeable.  
**Limites :** Dépendant de la taille du contexte.

</div>
<div class="p-4 border-2 border-emerald-500 rounded-lg bg-emerald-50 dark:bg-emerald-950">

### 2. RAG
**Quand ?** Données d'entreprise récentes, documents privés, besoin de traçabilité des sources.  
**Coût :** Modéré (infra de recherche).  
**Limites :** Qualité du chunking et de la recherche.

</div>
<div class="p-4 border rounded-lg bg-gray-50 dark:bg-gray-800">

### 3. Fine-Tuning
**Quand ?** Apprendre un **style**, une syntaxe de code propriétaire ou un jargon hermétique.  
**Attention :** Mauvaise méthode pour injecter de nouveaux faits !

</div>
</div>

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
      <li>• Données fraîches & modifiables à la seconde</li>
      <li>• <b>Traçabilité :</b> citations et sources vérifiables</li>
      <li>• Gestion fine des droits d'accès (ACL/RBAC)</li>
    </ul>
    <div class="text-red-500 font-semibold mb-1">Inconvénients :</div>
    <ul class="space-y-1">
      <li>• Pipeline lourd (chunking, vecteurs, reranking)</li>
      <li>• Échec si l'information est éparpillée sur 50 pages</li>
    </ul>
  </div>
  <div class="mt-3 pt-2 border-t border-gray-200 dark:border-gray-700 font-medium text-gray-500">
    🎯 <b>Idéal pour :</b> Base documentaire vivante, FAQ, conformité juridique.
  </div>
</div>

<!-- COLONNE 2 : LONG CONTEXT -->
<div class="p-3 border rounded-lg bg-gray-50 dark:bg-gray-800 flex flex-col justify-between">
  <div>
    <div class="font-bold text-sm text-purple-500 mb-1">2. Contexte 1M+ (Gemini 3.1 flash, Sonet, Deepseek)</div>
    <div class="text-gray-400 mb-2 italic">« Prends tout le dossier d'un coup »</div>
    <div class="text-emerald-500 font-semibold mb-1">Avantages :</div>
    <ul class="space-y-1 mb-2">
      <li>• Zéro infra complexe : un seul prompt géant</li>
      <li>• <b>Vue globale :</b> croise les chapitres/fichiers sans perte de contexte</li>
      <li>• Analyse tout un repo de code ou un livre</li>
    </ul>
    <div class="text-red-500 font-semibold mb-1">Inconvénients :</div>
    <ul class="space-y-1">
      <li>• Coût et latence (TTFT) élevés par requête</li>
      <li>• Risque d'inattention au milieu (<i>Lost in the middle</i>)</li>
      <li>• Ne remplace pas une base d'entreprise (capacité finie)</li>
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
      <li>• Maîtrise absolue du format (JSON strict, DSL)</li>
      <li>• Réduit les prompts (plus besoin de 10 exemples)</li>
      <li>• Modèle plus petit = inférence rapide & autonome</li>
    </ul>
    <div class="text-red-500 font-semibold mb-1">Inconvénients :</div>
    <ul class="space-y-1">
      <li>• <b>Mauvais pour mémoriser des faits</b> (hallucine)</li>
      <li>• Connaissances figées dans le temps</li>
      <li>• Risque d'oubli catastrophique (baisse en général)</li>
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

---
layout: default
---

# 12. Synthèse & Transition vers l'Agentique

<div class="p-4 bg-gray-100 dark:bg-gray-800 rounded-lg mb-6">
  <div class="font-bold text-lg mb-2">Ce qu'il faut retenir du socle LLM :</div>
  <ul class="text-sm space-y-1">
    <li>✓ Un LLM produit une suite de tokens vraisemblables à partir d'un contexte d'entrée.</li>
    <li>✓ Il excelle pour structurer, synthétiser et reformuler, mais il hallucine sur les faits purs.</li>
    <li>✓ Le RAG compense son absence de mémoire fraîche en lui fournissant des documents à la volée.</li>
  </ul>
</div>

### Vers le Module 2 : L'Agentique
Isolé, le LLM ne peut que parler. Pour qu'il devienne un **Agent**, il lui faut :
1. **Des outils** (exécuter du Python, interroger une API, naviguer sur le web)
2. **Une boucle de décision** (observer $\rightarrow$ raisonner $\rightarrow$ agir $\rightarrow$ corriger)
3. **Une mémoire persistante** au-delà d'un simple prompt.

---
layout: end
class: text-center
---

# Fin du Module 1
### Place aux échanges & questions !

[DiverSE Univ. Rennes](http://www.diverse-team.fr)


