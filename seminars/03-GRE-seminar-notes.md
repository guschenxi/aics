## Mitchell, et al. 2012

M. Mitchell, X. Han, J. Dodge, A. Mensch, A. Goyal, A. Berg, K. Yamaguchi, T. Berg, K. Stratos, and H. Daum ́e III. Midge: Generating image descriptions from computer vision detections. In Proceedings of the 13th Conference of the European Chapter of the Association for Computational Linguistics, pages 747–756. Association for Computational Linguistics, 2012.

### Simon's notes

* How do we describe an image? What is relevant in an image to include in a description? How much to say?
* Natural descriptions in the way humans express themselves but also truthful
* Natural Language Generation (NLG)
* Objects, actions, spatial relationships --> noun phrases, verbs, prepositional phrases
* Tasks
  * filter incorrect detections
  * order/attend the important objects
  * connect detections in a syntactically well-formed tree
  * add additional linguistic descriptions that go beyond the detections to make a well formed-description
* Computer vision
  * use detectors for objects, attributes of objects and relations between them
* Generation
  * template based generation: simple phrase patterns, e.g. The <OBJ1> is to the <left|right> of the <OBJ2>
  * syntactic trees make generation much more unpredictable (they are more general)
  * find similar images and simply copy their captions (may not be true of the current image); tells us something about the similarity of images in the dataset
  * this approach: use corpus statistics to estimate likelihood of words around objects (certain degree of hallucination) and use syntactic trees, also distinguish grammatical role, e.g. SUBJ and OBJ
* Learning
  * Flickr images and PASCAL images
  * parse the text
  * extract the probabilities of articles and modifiers given a head noun (and also verbs)
  * WordNet to detect mentions of physical objects: 92% mention only 3
  * 58% are sentences, 28% are NPs only, the rest are incomplete
* Generation
  * Types of phrases: a boy on the table, a boy cleans the table, a boy sits on the table; now generate trees for these patterns
  * start growing trees by creating nouns for objects that are detected
  * train the system on Flickr but test on PASCAL - why? When the detections are bad the system hallucinates (can be positive or negative)
  * GRE stages: (i) content determination, (ii) micro-planning; (iii) surface realisation
  * Knowledge base: word co-occurrence statistics, ordering of nouns in a sentence, re-writing CV detections to words, some rules (plurals, spatial relations, fixing detections)
* Content determination
  * group the nouns in groups of 3
  * order the 3 objects and determine SUBJ, OBJ
  * estimate probability to order the nouns based on their hypernyms using Wordnet; animate > inanimate
  * group adjectives by conditioning them on nouns into attribute classes: colour, material, surface, quality; by conditioning them on nouns (cf. functional-geometric); choose the most likely word for each attribute by conditioning it nouns (in case some property is described with more than one words?)
  * group objects of the same kind into a plural group; do not use modifiers, spatially relate them by the first member (simplification)
  * expand head nouns into local trees, the order of nouns (determine previously) will affect to what kind of NPs they can expand to (SUBJ, OBJ)
  * p(JJ|NN) and p(Det|JJ,NN) to determine the Det JJ NN combinations; mass, count nouns with and without determiner
  * for the VPs and PPs we collect subtrees where the probability of their sub-elements conditioned on the noun exceeds some threshold: p(VP{VBX verb}|NP{NN noun}=SUBJ) > α; the description of relation is therefore fully conditioned on the language model
* Micro-planning
  * take the intersection of the trees to form VP and PP phrases; if two NNs cannot be combined use a tree to coordinate them with AND - all trees are either S or NP (they call this step micro-planning)
* Surface realisation
  * train an n-gram language model and score all strings produced by the tree
  * take the most likely closed-class words for each node (works better)
  * order modifiers based on another language model: blue clear sky --> clear blue sky
* Evaluation
  * Amazon Mechanical Turk (AMT)
  * grammaticality, describes main spects of an image, correctness, order, human-likeness
  * the benefit of this system is that it is integrating statistical co-occurrence probabilities from corpus (i.e. language model) which filters out unlikely attribute descriptions; also ordering the objects
* Shortcoming
  * incorrect visual detections (filter out unlikely objects)
  * parsing errors on this domain affects probabilities


### Discussions

#### Groups, 2021

* G1: generation of prepositions, relations between bounding boxes;
* the role of the language model (hallucination, objects are grounded but actions are not), the role of attention, what the image is about
* G4: grounding of actions in video form
* the types of visual features used
* evaluation: what is a good score?
* the object description is rigid; object detection gives us a lot of results
* differences between GRE task and image captioning: the role of intent; improving datasets by having side-by-side images and the descriptions are discriminative; VQA; CLEVR dataset
* more than a single sentence: paragraph generation


#### ? 

  - Attributes even of the same linguistic categiory do not fit: several subcategories
  - Knowledge about the objects: what kind of attributes they license
  - Information comes in different order in a sentence: animate before inaanimate
  - Do not describe more than 3 objects in a sentence
  - The likelihood of full sentences vs NPs





## Lu et al, 2015

J. Lu, C. Xiong, D. Parikh, and R. Socher. Knowing when to look: Adaptive attention via a visual sentinel for image captioning. arXiv:1612.01887 [cs.CV], 6 June 2017.


### Simon's notes

* Not all words depend on the vision to the same degree
* Adaptive attention with visual sentinel: when to rely on visual signals and when to analyse on the language model;
* attention tells us where to look and when
* encoder-decoder architecture for image captioning: predict the likelihood of the next word conditioned on the previous words and the image from the hidden state of the LSTM and the and the context vector: log p(yt|y1,...,yt1,I) = f(ht,ct)
* context vector is either (i) features from the image V or (ii) features of the image and the decoder h_t (attention)
* basic attention
  * V and h_t are fed to a fully connected layer followed by softmax yo give us \\alpha: the attention weights over V
  * the weights are summed over the regions to give us c_t
  * c\**\*i \*is combined with ht to predict y*\*{t+1}, the next word
  * h_t *or* h_{t-1}: attention for the current word or from the previous word? motivation: complete information state for this word
* adaptive attention
  * visual sentinel as a fall-back from attending image (sentinel = guard)
  * visual sentinel s_t *is determined from xt, ht and m*_t: information about adaptive attention is in the memory cell
  * adaptive attention is then ct^ = \\beta*t* s_*t + (1 -* \\beta*t)c*_t; beta is therefore weighing between the contribution of the sentinel (not just language information!) and the visual information
  * calculate \\beta: concatenate the visual attention vector (the previous \\alpha) with the output of the layer that combines h_*t and* s_t; the last element of this vector is then \\beta, see Figure 3; softmax ensures that all values sum up to 1
  * from the ct^and h_t predict the probability of the next word (softmax)
* implementation
  * extract ResNET features; add a linear layer to resize them to d
  * the input vector x_t is a concatenation of the word embedding vector and image feature vector
  * s*t and h*t are projected to the same dimension d with a single layer; so that they can be concatendated to the visual features for ct^
  * beam search for generation, size 3
* Results
  * Flickr30k, COCO
  * Evaluation scores, BLEU, METEOR, CIDEr, Rouge-L, SPICE
  * Figure 4 shows very nice visualisations of attention
  * Figure 5 shows visualisations of the sentinel gate; the system is attending objects but not attending relations; a functional word such as *a* might be attended at the beginning of the sentence because the model needs to look to get context but not later; progression of attention
  * Figure 6 ranks works how likely they are to be visually grounded; there are language models effects to the degree of grounding Figure 7: (i) because of a frequency of a word used in general (e.g. different forms of verbs); (ii) because of other competing descriptions (phone, cell)
  * overlap the attended regions with the ground-truth bounding boxes, 0.362 for spatial/simple attention, and 0.373 for adaptive attention

Other relevant papers

A. Karpathy and L. Fei-Fei. Deep visual-semantic alignments for generating image descriptions. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pages 3128–3137, 2015. [paper](<https://www.cv-foundation.org/openaccess/content>*cvpr*2015/papers/Karpathy*Deep*Visual-Semantic*Alignments*2015*CVPR*paper.pdf)

K. Xu, J. Ba, R. Kiros, A. Courville, R. Salakhutdinov, R. Zemel, and Y. Bengio. Show, attend and tell: Neural image caption generation with visual attention. arXiv, arXiv:1502.03044 [cs.LG]:1–22, February 11 2015. [paper](https://arxiv.org/abs/1502.03044)

C. Olah. Understanding LSTMs. Technical report, Google Brain, August 27 2015. [tutorial](<http://colah.github.io/posts/2015-08-Understanding-LSTMs/>) 



### Discussions


#### Groups, 2021





## Mitchel, van Deemter and Reiter 2013

M. Mitchell, K. van Deemter, and E. Reiter. Generating expressions that refer to visible objects. In HLT-NAACL, pages 1174–1184, 2013.



### Discussions


#### Jose

2018-11-29

  - Why this paper? Traditional survey of features; what goes into GRE; pre-specified features and feature extractors
  - Algorithms, TUNA corpus
  - Properties:
    * Absolute: colour
    * Relative properties: size, height, width


#### Peter

  - Generating referring expressions: that unambiguously identify the referent
  - NP
  - Select a set of properties
  - Goal: locate the object; what a human might do in the same situation
  - Stochastic to capture human variation: previous work focuses on identifying objects uniquely; overspecification and redundancy; also sometimes underspecification; humans do not behave optimally
  - Focus on the salience from the perspective of the speaker; related to Schober and FOR assignment
  - Different kinds of salience
  - We process features in order: colour > size
  - Distinguish properties in two groups: absolute (colour) WHAT?, relative (size) WHERE?
  - The probability that an attribute will feature in the description (relastive to hearer), alpha
  - Incremental algorithm of Dale and Reiter, Graph based algorithm of Krahmer
  - REG algorithm: iterates thrtough two parallel lists of properties with penality for longer descriptions
  - Corpus is a pre-process dataset of visual features
  - alpha is the relative frequency of that attribute in the training data
  - dice score/coefficient to evaluate a description
  - http://www.abdn.ac.uk/ncs/departments/computing-science/corpus-496.php
  - The probability model is very simple; add conditional probabilities (which qould require a larger corpus)
  - Material and colour are related; how could this be modelled? Also, an object might have an unexpected colour which makes it worth mentioning
  - Should GRE be done more than on images; some features may not be captuared by images
  - Clarification in dialogue could be used to exploit second-best solutions, etc.
  - Both corpora use artificial colour where objects were generated with thsi as adistinguishing feature and hence they are creating a contextual bias
  - Ted Gibson: more colour terms with industrialisation vs. languages closer to nature
  - If a feature is unexpected of an object, it is more likely to be mentioned



#### Tessa





## Elliot and Keller, 2013

D. Elliott and F. Keller. Image description using visual dependency representations. In EMNLP, volume 13, pages 1292–1302, 2013.



### Discussions

#### Sung Min

  - Mitchell as a background: how GRE algorithm works, incrementally adding descriptions belonging to these properties
  - Elliot and Keller: dependency parse of words, dependencies of visual relations, some manually annotated by humans
  - Predefined rules for spatial relations (Q)
  - Templates to generate descriptions
  - They use paralel corpus to extract dependencies which help to identify relations between objects and helps VDRs, hence human annotation is not required
  - bounding boxes are distriyised but these may not be always useful, e.g. a group of people
  - VDRs as abstract not real spatial relations
  


#### India

  - Image descriptions
  - Bounding boxes of objects but no relations between them: person riding a bike vs. person fixing a bike
  - VDRs: visual dependency representations; relations between images
  - Visual dependency grammar: 8 relations between objects
  - create a DAg with visual relations over the image
  - language is depndensy parsed
  - visual dependency grammar is similar to dependency grammar for language; a central actor defines the root node
  - Annotate regions of the image manually with VDRs, 341 images
  - Several models:
      - Proximity: closeness of regions: inlcude in the description; a man beseide the bike; nop VDRs here; taking the central objects in the image and saying that they are close
      - Corpus: text corpus that picks out verbs that typically relate two objects; the man, the bike -> ride;
      - Structure: uses VDR; generate all relations between pairs of regions; and then generate descriptions according to the syntactic patterns; then generate descriptions that are closer in the graph: man -> bike -> road; man is on the bike not man is on the road; does not inlcude verbs
      - Parallel: also generates verbs; how are verbs predicted? they are probabilistically conditioned on objects and the VDRs
  - Parsing images with VDRs
  - Bleu measure
  - Human judgements about grammar, action and scene
  - Spatial relations relative to the image not to the scene
  - Regions are not objects
  - Visual parsing and sentence parsing are not connected
  - Annotators had to describe an image with two sentences: one with action and the other with relations



####  Sophie

