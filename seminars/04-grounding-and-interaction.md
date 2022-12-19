# Steels and Loetzsch

L. Steels and M. Loetzsch. [Perspective alignment in spatial language.](https://doi.org/10.48550/arXiv.cs/0605012) In K. R. Coventry, T. Tenbrink, and J. A. Bateman, editors, Spatial Language and Dialogue. Oxford University Press, 2009.

## Simon's notes


## Discussions

### Groups, 2022

  - Is it a problem that systems internalise language that is not human-like? Some fine-tuning is required with human categories. See Lazaridou et al. final experiment.
  - What happens with more participants? Convergence. Steels and Loetch pick two agents out of four that they previously trained.
  - More complicated ways to mark perspective:
    * resolve perspective from perception: compare all views and choose the one where a description makes sense
    * specify perspective overtly, "my left"
    * task might define persepctive, e.g. museum guide, instructions and direction of travel, whose point of view are we focuing on within the task
    * alignment over several utterance
  - To what degree refinforcement learning approximates natural interaction; there may be other elements involved
    * RL: statement - feedback (reward)
    * clarification
    * several statements
    * more pictures than two
    * inrementality
    * explanation about the error: Why?
  - Vocabulary size used and the success of a learning
    * agnostic learning uses only 2 symbols in the human-like expeirment with 92% of success but low purity; so it converegens onto very general classes
    * informed sender uses more symnbols
    * difference is in the architecture of visual embeddings; IS has learned how to discriminate objects rather than just identify
    * the role of syntax and the vocabulary size, cf. Kazakov asnd Kirby S. Kirby, H. Cornish, and K. Smith. [Cumulative cultural evolution in the laboratory: An experimental approach to the origins of structure in human language.](https://www.pnas.org/doi/full/10.1073/pnas.0707835105) Proceedings of the National Academy of Sciences, 105(31):10681–10686, 2008.

Interesting papers:

Adding perspective to the VQA task: code and dataset in J. H. Lee, M. Kerzel, K. Ahrens, C. Weber, and S. Wermter. [What is right for me is not yet right for you: A dataset for grounding relative directions via multi-task learning.](https://arxiv.org/abs/2205.02671) arXiv, arXiv:2205.02671 [cs.CV], 2022.

Our Cups dataset: S. Dobnik, J. D. Kelleher, and C. Howes. [Local alignment of frame of reference assignment in English and Swedish dialogue.](https://gup.ub.gu.se/publication/294795?lang=en) In J. Sˇk ̧ilters, N. S. Newcombe, and D. Uttal, editors, Spatial Cognition XII: Proceedings of the 12th International Conference, Spatial Cognition 2020, Riga, Latvia, pages 251–267, Cham, Switzerland, 2020. Springer International Publishing.



### Groups, 2021

* Programming a robot with language
* perspective shift, 90 degrees
* comparison of reinforcement learning from this paper and next; the number of examples required
* 





# Lazaridou at el.

A. Lazaridou, A. Peysakhovich, and M. Baroni. [Multi-agent cooperation and the emergence of (natural) language.](http://arxiv.org/abs/1612.07182) arXiv, arXiv:1612.07182v2 [cs.CL]:1–11, 2016.



## Simon's notes



## Discussions

### Groups, 2022

See the notes for the previous paper.



### Groups, 2021

* To what degree learning labels is natural language?
* Assigning labels is like image classification? The model ported from image classification to interactive reinforcement learning.
* Interactive? Very simple interaction: just agreeing. There are more complex forms of interaction: agreeing, correction, clarification; the model is very symmetrical; one person is describer the other is listener, but the roles could change
* <https://pytorch.org/tutorials/intermediate/reinforcement>*q*learning.html
