## Harnad

S. Harnad. [The symbol grounding problem.](https://doi.org/10.1016/0167-2789(90)90087-6) Physica D, 42(1–3):335–346, June 1990.

(Roy 1990) introduces the notion of grounded natural language from a theoretical perspective. What are the main points he presents and how do they relate to the distributional and distributed representations of language we use in language technology?


### Simon's notes

 - the context of the paper: symbolic AI, symbolic NLP; behaviourism in psychology, early applications of neural networks
 - sees language as a symbolic system: NL syntax follows distributional or symbolic rules; certainly symbol combinations on the surface but the process could be distributional
 - complementarity of the symbol system and connectionist system
 - top-down and bottom-up systems: work in complementarity as grounded symbols are manipulated (cf. learning to compose); compatible with behaviourism
 - iconic representations discriminate (one pattern from another); categorical identify (i.e. a horse) symbolic representations require structure / compositionality (zebra = horse & stripes)


### Discussion

## 2022 groups





#### 2021 groups

 - G4-FDP Model: human or computational? Related?
 - Grounding: bottom-up and top-down: in order to connect the meaning to words you need to consider both levels
 - Is natural language symbol manipulation or not?
 - G1 Compositionality of grounding: the granularity of grounding; do we need to experience all parts of the grounded concept?
 - Are all words grounded (to the same degree)? Determiners, nouns, adjectives, relations? How do we ground actions: objects first? Easy to ground colours and shapes - what about abstract concepts?
 - Distributed or distributional representations
 - Grounding for visually impaired people? Other features: shape, texture?
 - G6: Iconic and categorical representations: difference?
 - SHRDLU, Shakey and Flakey: T. Winograd. Understanding Natural Language. Edinburgh University Press, 1976.



#### 2019 Miriam

  - Behaviourism and cognitivism
  - Computation as symbol manipulation, rules
    * Symbolic vs distributional
  - Symbols connected with the world
  - Chinese room, working with a dictionary
  - Symbol vs entity it represents, sensory-motor system
  - How to pass a Turing test? How to verify and experience an object?
  - Grounded and non-graded representations
    * model based vs distributional semantics
  - Meaning is achieved through grounding
  - Iconic and categorical representations
    * Iconic, discriminative
    * Categorical, identifiable
    * Levels of grounded representations?
  - Sensors, motors, the capacity to interact with the world
  - Detect, categorise, identify and act upon the entities that the symbol refers to
  - Feature dectors: inborn or learned
  - Learning based on trial and error guided from feedback (correct vs incorrect categorisation)
  - Are all words grounded in perception and action?
  - Formal test: can we interpret the representations
  - Behavioural test: is the behaviour okay? Discriminate, identify, manipulate...
  - Where is the meaning? Agent-relevant or out there?
  - Connectionism as a solution
  - Are all concepts experienceable and groundable?
  - Grounding in perception and grounding in a language model



#### ?

  - Symblic vs connectionist
  - Cognitivism vs behaviorism: impossible to form theopries about whatagent has in mind; cognitivism underlines behaviour
  - Symbolic systems: arbitrary symbols, rules, incremental structure
    * Compositeness (meaning of the whole is the meaning of its parts) and Systematicity (derive semantic meaning from separate parts)
    * Not all symbolic systems have the property of compositeness and systematicity
  - Connectionist systems:
    * Symbolic way of modelling the language and the brain
    


#### Ida

  - Grounded
  - Symbols: a triangle; symbol is a representation of the object, not the object itself
  - Cognition as symbol manipulation: Symbols: tokens, agreed rules, composed symbols/composite symbol-token strings; semantics: describing state of affairs
  - Cognition as connectivism: not a symbol system;
  - Harnad: we need a hybrid model:
    * discrimination: iconic representations
    * identification: categorical representations
    * symbols connected to non-symbolic representations
  - Why is a connectionist model a good candidate?

   - Why iconic representations?
   - Why neural networks as mediators of non-categorial representations and categorial representations?
   - Compositionality of grounding?



#### David

Behaviourism

Connectivism

What is a symbol system: this view is very familiar to NLP community

Neural networks: 26 years ago, deep learning has now returned

Symbols and nets: symbols better for language tasks and nets are better for the sensory motor tasks

The Chinese room experiment thought experiment:
  - Round 1: you learn Chinese from the outputs of the system where you know another language
  - Round 2: you learn Chinese from the outputs of the system where you don't know another language, i.e. symbols are ungrounded, not connected to the world

Represnetations:

  - Iconic representations: directly connected to the world; sensory readings, features
  - Categorical representations: cognitive abstractions but of course based on grounded representations; there is an interplay between the two in terms of how much they contribute, e.g. discussion on the nature of objects
  - Symbolic representations
  - Taxonomic representations

Symbolic model is ungrounded
Connectionist model is grounded but not compositional
   - Horses, stripes = zebras ???
   


#### Wafia

The paper might be a bit old, but it is still very relevant as it is still a central research quetsion in linguistics, computational linguistics, philosophy and AI.

The Chinese Room Experiment, Searl

Symbolism and connectivism: similar divide in computational linguistics

Symbol system: cf. Computational Semantics course

Connectionist system: artificial neural networks from ML, Shruti, Networks and Types project

Neural Networks are slow?

Are neural networks symbolic? According to Harnad thay fail the composition criteria.

Chinese room: difficult (trying to learn Chinese on the basic of bilingual dictionary) and impossible version (learning Chiense as a native speaker, from data?)

Top down (symbolic) and bottom up (connectioninst)

Levels of representations:

  - Iconic representations - why do we need these?
  - Categorical representations: elementary symbols - what are elementary symbols?
  - Higher-order symbolic representations
  
  This will become very relevant for the TTR lectures next week.
  
Symbols are not grounded only on arbitrary shapes but their grounding is based on non-arbitrary shapes of the iconic representations. What does this mean?

"The symbol menaing are not parasitic on the meanings in the head of the interpreter but intrinsic to the dedicated symbol system itself."





## Roy

D. Roy. [Learning visually-grounded words and syntax for a scene description task.](https://doi.org/10.1016/S0885-2308(02)00024-4) Computer speech and language, 16(3):353–385, 2002.

Roy (2002) describes a computational implementation of how scene descriptions are connected to the visual representations of abstract scenes. It describes the grounding in a Bayesian probabilistic approach which provides an intuitive description of how representations at different levels of language are grounded. How is grounding implemented in practice? What techniques from natural language processing that you know from before are applied and how they are extended?


### Simon'd notes

* DESCRIBER, grounding: visual scenes \~\~> transcribed descriptions
* data \~\~> learning \~\~> NLU \~\~> NLG \~\~> descriptions
* Computer generated rectangle scenes
* NLG: generate a description to identifies the target objects and excludes all its distractors
* Multi-layered grounding: words - word classes - syntactic patterns
* Separate simple from complex descriptions (multiple objects): syntax learned in stages
* semantically and syntactically words belong to the same classes
  * words of the same class do not co-occur syntactically: co-occurrence is distortion
  * words of the same class have similar grounded features: mju and sigma for how features associates over words
  * estimate the same but for scenes and words that do not occur in the utterance; background model, i.e. presence of feature unconditioned on a word
  * KL divergence between the two
  * Semantic association vector: for each word create a feature vector of KL distances; calculate distortion between the semantic association vectors (take one as negative) just as in the syntactic comparison above
  * Combine syntactic and semantic distortion into a single weighted metric
  * Calculate KL divergence on multi-variate distribution, for several features
  * Features are associated from words to classes of these words
  * For each word estimate a Gaussian distribution over the features identified for its class (this is our classification model, previously we were looking at how to associate features)
* train a statistical model of class sequences
* summary on p.18
* generation
  * syntactic constraints (word order), semantic constraints (features are grounded) and contextual constraints (must be distinguishing)
  * For each bi-gram sequence of classes, for each class choose the most likely word given the target object: the, the rectangle, the green rectangle, the large green rectangle, the large light green rectangle...
  * Syntactic and semantic constraints: estimate the fit of each description to the target object: the likelihood of a sequence of words to refer to the features of the object
  * Contextual constraints and ambiguity of a description; fit of a description to an object against the best fitting competing object\
    ψ(Q)=fit(x_target,Q)−max∀x=/=target fit(x,Q)
  * Combine the scores from syntactic and contextual constraints with a weighted sum
* Grounding spatial clauses / descriptions



### Discussion


#### 2021 groups

* The pipeline of the system; generating the text; where does grounding happens; during learning or generation over a new scene?
* Learning language in real context with intentions



#### Linnea

  - Describer, images of rectangles automatically generated
  - Learning grounding and syntax (simple vs complex utterances)
  - Feature selection, pre-defined features
  - Learning word-classes
  - Dsitributional clustering; words in similar classes will be used in similar contexts and exlcusive of each other
  - A model a combination of visual and distirbutional cues
  - Categories on p.366
  - Categories defined by features, sequences of categories, most likely classes of sequences



#### ?

  - Describer: artificially create the dataset
  - supervising the process of learning buy splitting the task into modules
  - introducing certain features at certain modules only, e.g. spatial features of Regier



#### Sylvie

  - 



#### Yuri

  - Learn grounded meanings of words
  - Learn structure

  - Phrases that best describe the target objects: 8 features (colours and spatial features (things that might be releavant for identifying objects)
  - Speech transcription (but in the earlier paper this was done automatically)

Learning classes
  - Similar words would cluster in the same context; cluster the words accoring to the context; could try vector space models
  - Feature association clusters; what features are predictive for a particular class of words: words will have similar clusters
  - Linear combination of the previous two metrics (syntax, approach 1 and semantics approach 2)
  - Feature selection: what features are relevant for classes; some words do not have relevant features, e.g. -est, the

Class-based bi-gram model models syntax

What utterance is the least ambiguous given an object?

Complex utterances
(...) near the (...): use simple parsing in the complex utterances

Generating relative spatial clauses: i.e. typical spatial descriptions

Evaluation:
  - Given a description, choose an image
  - 200 machine generated and human generated descriptions

Discussion:
  - Small size of the task: only 1 human, more people should be included
  - 89.8% human accuracy: this is taken as a top baseline
  - the question of vagueness of expressions; humans may find them more acceptable than they would be given the classifier accuracy
  - a lot of supervision in the learning: simple vs complex categories, attentional vector sum model
  - replicate the model with image classification, larger corpus



#### Ana

A simple task? An incredibly difficult task! Wants to be unsupervised.

Simple vs. complex utterances? Are we not there distinguishing between reprrsentational layers and therefore making the task supervised, i.e. the outputs from the first layer asre taken as inputs on the second layer.

The learning contains visual features which introduces a supervision element to the learning.

Feature selection? Data driven or interesting linguistic generalisation?

Complicated maths: Bayesian reasoning

Spatial relations: attentional vector sum model is used directly (AVS) rather than implementing learning on the same features as learning objects

Possible project to repeat (on a smaller scale).
