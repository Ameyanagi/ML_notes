  Probabilistic programming is a mechanism for compactly and compositionally representing a large set of richly expressive generative models as well as performing general-purpose automatic algorithms to do inference over variables in such models.  
  Higher-order probabilistic programming languages open up possibility of doing inference over generative models themselves. The goal is to find an efficient robust way to automatically produce and tune models based on training data and knowledge.


  * [introduction](#introduction)
  * [overview](#overview)
  * [applications in industry](#applications-in-industry)
  * [applications in cognitive science](#applications-in-cognitive-science)
  * [higher-order probabilistic programming](#higher-order-probabilistic-programming)
  * [projects](#projects)
  * [interesting quotes](#interesting-quotes)
  * [interesting papers](#interesting-papers)
    - [inference](#interesting-papers---inference)
    - [applications](#interesting-papers---applications)


selected papers and books - https://dropbox.com/sh/2m10m5bsctmd4zr/AADSvK7nWzyB7jViNXBuXghca

bayesian inference and learning - https://dropbox.com/s/7vlg0vhb51rd6c1/Bayesian%20Inference%20and%20Learning.txt




### introduction

  "A probabilistic programming language provides syntax to instantiate random variables, as well as syntax to impose conditions on these random variables. The goal of inference in a probabilistic program is to characterize the distribution on its random variables, subject to the imposed conditions. When conditions define hard constraints (such as a=10, or a>5, for some variable a), execution of a probabilistic program can be interpreted as rejection sampling. Expectation values can, in principle, be calculated by repeatedly running the program and excluding executions that violate one or more conditions. In practice, the language design often implicitly or explicitly guarantees that conditions can be satisfied with a computable non-zero probability in any execution. Probabilistic programs in such languages can be seen as importance samplers; repeated execution yields samples from a prior, which are assigned an importance weight according to the probability that its conditions are satisfied. From a modeling point of view, a probabilistic program P defines a probability distribution. In a language that provides if-statements, recursion, higher-order functions, and primitive operations such as matrix inversion, this distribution can have an almost arbitrary structure. This means that from an inference point of view, a program P is a sequence of opaque deterministic operations that is interrupted by (1) sample statements, which require generation of a value for a random variable and (2) conditioning statements, which change the importance weight of the execution history."

  "Probabilistic programming systems represent generative models as programs in a language that has specialized syntax for definition and conditioning of random variables. A backend provides one or more general-purpose inference methods for any program in this language, resulting in an abstraction boundary between model and inference algorithm design. Models specified as programs are often concise, modular, and easy to modify or extend. This allows definition of structured priors that are specifically tailored to an application domain in a manner that is efficient in terms of the dimensionality of its latent variables, albeit at the expense of performing inference with generic methods that may not take advantage of model-specific optimizations."

  "Probabilistic models provide a framework for describing abstract prior knowledge and using it to reason under uncertainty. Probabilistic programs are a powerful tool for probabilistic modeling. A probabilistic programming language is a deterministic programming language augmented with random sampling and Bayesian conditioning operators. Performing inference on these programs then involves reasoning about the space of executions which satisfy some constraints, such as observed values. A universal probabilistic programming language, one built on a Turing-complete language, can represent any computable probability distribution, including open-world models, Bayesian non-parameterics, and stochastic recursion."

  "In the context of Turing-complete, higher-order probabilistic programming languages, a probabilistic program is simultaneously a generative model and a procedure for sampling from the same. All probabilistic programming procedures are program text that describe how to generate a sample value conditioned on the value of arguments. A probabilistic programming procedure is a constructivist description of a conditional distribution."

  "From an AI perspective, probabilistic programs are an extremely general representation of knowledge, and one that identifies uncertainty with stochastic computation. In probabilistic programming language the meaning of the program is the distribution it samples from."

  "It's a way of doing machine learning without writing algorithms. You write a simulator of the world, which is a probabilistic program, and environment takes that program and runs it backwards. It's less coding, which allows rapid prototyping, makes it much faster to develop machine learning systems, is easier to debug - there are tons of advantages.”




### overview

  http://plus.google.com/+BeauCronin/posts/KpeRdJKR6Z1  
  http://intelligence.org/2014/09/04/daniel-roy/  
  http://pl-enthusiast.net/2014/09/08/probabilistic-programming/  

  [Programs and Probability](http://americanscientist.org/libraries/documents/20158411291411312-2015-09Hayes.pdf)

  http://habrahabr.ru/post/242993/  (in russian)  
  http://youtube.com/watch?v=ZHERrzVDTiU  (in russian)  

  http://moalquraishi.wordpress.com/2015/03/29/the-state-of-probabilistic-programming/  
  http://twiecki.github.io/blog/2016/06/01/bayesian-deep-learning/  
  http://dustintran.com/blog/a-quick-update-edward-and-some-motivations  

  overview by Mansinghka -
	https://youtube.com/watch?v=-8QMqSWU76Q

  tutorials by Wood -  
	http://research.microsoft.com/apps/video/dl.aspx?id=259568  
	http://youtube.com/watch?v=6Lqt07enBGs + http://youtube.com/watch?v=DY5yuBNEuQs  

  "Probabilistic Programming and Bayesian Methods for Hackers" by Davidson-Pilon -
	http://camdavidsonpilon.github.io/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers/

  "The Design and Implementation of Probabilistic Programming Languages" by Goodman and Stuhlmuller -
	http://dippl.org

  Neural Abstract Machines & Program Induction workshop @ NIPS 2016 - https://uclmr.github.io/nampi/




### applications in industry

  Microsoft Office 365 (using Infer.NET) - https://cambridgenetwork.co.uk/news/email-clutter-machine-learning-probabilistic-programming/

  Microsoft Excel plugin (using Infer.NET) - http://research.microsoft.com/en-us/projects/tabular/

  graphics in reverse - http://newsoffice.mit.edu/2015/better-probabilistic-programming-0413

  http://blogs.microsoft.com/next/2015/07/10/the-next-evolution-of-machine-learning-machine-teaching/




### applications in cognitive science

  "Cognitive Foundations for Common-sense Knowledge Representation and Reasoning" by Tenenbaum -
	https://youtube.com/watch?v=oSAG57plHnI

  "Building Machines That Learn like Humans" by Tenenbaum -
	https://youtube.com/watch?v=quPN7Hpk014

  "The Origins of Common Sense: Modeling human intelligence with Probabilistic Programs and Program Induction" by Tenenbaum -
	http://research.microsoft.com/apps/video/default.aspx?id=229021&l=i

  "How to Grow a Mind: Statistics, Structure, and Abstraction" by Tenenbaum, Kemp, Griffiths, Goodman -  
	http://videolectures.net/aaai2012_tenenbaum_grow_mind/  
	http://videolectures.net/nips2010_tenenbaum_hgm/  
	http://web.mit.edu/cocosci/Papers/tkgg-science11-reprint.pdf  


  "Concepts in a Probabilistic Language of Thought" by Goodman, Tenenbaum, Gerstenberg -
	https://web.stanford.edu/~ngoodman/papers/ConceptsChapter-final.pdf

>	"Knowledge organizes our understanding of the world, determining what we expect given what we have already seen. Our predictive representations have two key properties: they are productive, and they are graded. Productive generalization is possible because our knowledge decomposes into concepts - elements of knowledge that are combined and recombined to describe particular situations. Gradedness is the observable effect of accounting for uncertainty - our knowledge encodes degrees of belief that lead to graded probabilistic predictions. To put this a different way, concepts form a combinatorial system that enables description of many different situations; each such situation specifies a distribution over what we expect to see in the world, given what we have seen. We may think of this system as a probabilistic language of thought in which representations are built from language-like composition of concepts and the content of those representations is a probability distribution on world states."

>	"Probabilistic language of thought hypothesis (informal version): Concepts have a language-like compositionality and encode probabilistic knowledge. These features allow them to be extended productively to new situations and support flexible reasoning and learning by probabilistic inference."

  "Probabilistic Programs: A New Language for AI" by Goodman -
	http://youtube.com/watch?v=fclvsoaUI-U

>	"How can logical and probabilistic approaches to understanding intelligence be reconciled? I will argue that probabilistic programming is the best way to merge logic and probability, providing a new set of tools for thinking about representation and inference in systems with human-like intelligence. I will illustrate these ideas by introducing the probabilistic programming language Church (a stochastic LISP), describing two universal inference algorithms (i.e. algorithms that can perform probabilistic inference for any Church program), and giving a series of examples. These examples, drawn from cognitive science and AI, will include multi-agent reasoning and concept learning."


  "Probabilistic Models of Cognition" by Goodman, Tenenbaum -
	https://probmods.org

  "Modeling Cognition with Probabilistic Programs: Representations and Algorithms" by Stuhlmueller (PhD thesis) -
	https://stuhlmueller.org/papers/stuhlmueller-phdthesis.pdf

  "Towards more human-like concept learning in machines: compositionality, causality, and learning-to-learn" by Lake (PhD thesis) -
	http://cims.nyu.edu/~brenden/LakePhDThesis.pdf

  "How Does the Brain Do Plausible Reasoning" by E.T. Jaynes -
	http://bayes.wustl.edu/etj/articles/brain.pdf


####   Sanders, Hangya, Kepecs - ["Signatures of a Statistical Computation in the Human Sense of Confidence"](https://goo.gl/OQ7pEk)
>	"Human confidence judgments are thought to originate from metacognitive processes that provide a subjective assessment about one’s beliefs. Alternatively, confidence is framed in mathematics as an objective statistical quantity: the probability that a chosen hypothesis is correct. Despite similar terminology, it remains unclear whether the subjective feeling of confidence is related to the objective, statistical computation of confidence. To address this, we collected confidence reports from humans performing perceptual and knowledge-based psychometric decision tasks. We observed two counterintuitive patterns relating confidence to choice and evidence: apparent overconfidence in choices based on uninformative evidence, and decreasing confidence with increasing evidence strength for erroneous choices. We show that these patterns lawfully arise from statistical confidence, and therefore occur even for perfectly calibrated confidence measures. Furthermore, statistical confidence quantitatively accounted for human confidence in our tasks without necessitating heuristic operations. Accordingly, we suggest that the human feeling of confidence originates from a mental computation of statistical confidence."

  - http://www.eurekalert.org/pub_releases/2016-05/cp-obu042816.php




### higher-order probabilistic programming

"One of the key characteristics of higher-order probabilistic programming languages equiped with eval is that program text both can be generated and evaluated. In higher-order languages (Lisp, Scheme, Church, Anglican and Venture) functions are first class objects - evaluating program text that defines a valid procedure returns a procedure that can be applied to arguments. The means that, among other things, program text can be programmatically generated by a program and then evaluated. In a probabilistic programming context this means that we can do inference about the program text that gave rise to an observed output or output relationship. In short, we can get computers to program themselves."

"Performing Inference in the Spapce of Expressioans via Probabilistic Programming" by Wood - http://www.robots.ox.ac.uk/~fwood/anglican/teaching/mlss2014/arithmetic_expression/questions.pdf

>	"In the following we set up what is essentially a regression problem and ask the computer to find a solution in the space of arithmetic expressions that could give rise to the observed relationship. Note very carefully that this approach stands in sharp contrast to picking a function family and looking for a parameterization of a member of this family that is optimal with respect to some cost function and observed input output values. The following program generates simple arithmetic expression code using a probabilistic context-fee grammar generative model (productions) and then evaluates those expressions on known input values and compares the output to known outputs. It then predicts both the procedure text and the value of the procedure applied to a new argument."

"Learning Probabilistic Programs" by Perov and Wood - http://arxiv.org/abs/1407.2646




### projects

  http://probabilistic-programming.org


  * Forest - "a repository for generative models"  
	http://forestdb.org  

  * Probability Zoo - "a community repository for pre-trained probabilistic models"  
	http://edwardlib.org/zoo  

  * Edward  
	http://github.com/blei-lab/edward  
	http://dustintran.com/blog/a-quick-update-edward-and-some-motivations/  
	http://github.com/blei-lab/edward/wiki  
	http://dustintran.com/talks/Tran_Edward.pdf  
	"Deep Probabilistic Programming" - https://arxiv.org/abs/1701.03757  

  * Stan  
	http://dustintran.com/talks/post_advi.pdf  
	https://youtube.com/watch?v=6NXRCtWQNMg  
	https://vimeo.com/132156595  

  * PyMC3  
	http://pymc-devs.github.io/pymc3/  

  * Infer.NET  
	http://research.microsoft.com/infernet  

  * WebPPL  
	http://webppl.org  

  * Church  
	http://cocolab.stanford.edu/publications.html  

  * BLOG  
	http://bayesianlogic.github.io  

  * Venture  
	http://probcomp.csail.mit.edu/bayesdb/  
	https://youtube.com/watch?v=-8QMqSWU76Q  
	https://youtube.com/watch?v=7_m7JCLKmTY  

  * FACTORIE  
	http://factorie.cs.umass.edu  
	http://youtube.com/watch?v=MEhN9K36BfQ  
	http://youtube.com/watch?v=DkRLTToCw-0  




### interesting quotes

  Andreas Stuhlmueller:
  > "Probabilistic programs express generative models, i.e., formal descriptions of processes that generate data. To the extent that we can mirror mechanisms “out there in the world” in a formal language, we can pose queries within this language and expect the answer to line up with what happens in the real world. For example, if we can accurately describe how genes give rise to proteins, this helps us in predicting which genetic changes lead to desirable results and which lead to harm.
  Traditionally, Bayesian networks have been used to formalize and reason about such processes. While extremely useful, this formalism is limited in its expressive power compared to programming languages in general. Probabilistic programming languages like Church provide a substrate for computational modeling that brings together Bayesian statistics and Turing-complete programming languages.
  What is the structure of thought? The language of thought hypothesis proposes that thoughts are expressions in a mental language, and that thinking consists of syntactic manipulation of these expressions. The probabilistic language of thought hypothesis suggests that these representations have probabilistic meaning. If we treat concepts as stochastic programs and thinking as approximate Bayesian inference, can we predict human behavior in experimental settings better than using other approaches, e.g., prototype theory? If we learn more about the primitives and composition mechanisms used in the brain to represent abstract concepts, can this inform how we construct tools for reasoning?"

  Joshua Tenenbaum:
  > "If our goal is to build knowledge representations sufficient for human-level AI, it is natural to draw inspiration from the content and form of knowledge representations in human minds. Cognitive science has made significant relevant progress in the last several decades, and I will talk about several lessons AI researchers might take from it. First, rather than beginning by trying to extract common-sense knowledge from language, we should begin (as humans do) by capturing in computational terms the core of common sense that exists in prelinguistic infants, roughly 12 months and younger. This is knowledge about physical objects, intentional agents, and their causal interactions -- an intuitive physics with concepts analogous to force, mass and the dynamics of motion, and an intuitive psychology with concepts analogous to beliefs, desires and intentions, or probabilistic expectations, utilities and plans -- which is grounded in perception but has at its heart powerful abstractions that can extend far beyond our direct perceptual experience. Second, we should explore approaches for linguistic meaning, language understanding and language-based common-sense reasoning that build naturally on top of this common-sense core. Both of these considerations strongly favor an approach to knowledge representation based on probabilistic programs, a framework that combines the assets of traditional probabilistic (though not neural) and symbolic approaches."

  Pedro Domingos:
  > "Probabilistic graphical models provide a formal lingua franca for modeling and a common target for efficient inference algorithms. However, many of the most innovative and useful probabilistic models published by the AI, machine learning, and statistics community far outstrip the representational capacity of graphical models and associated inference techniques. Models are communicated using a mix of natural language, pseudo code, and mathematical formulae and solved using special purpose, one-off inference methods. Rather than precise specifications suitable for automatic inference, graphical models typically serve as coarse, high-level descriptions, eliding critical aspects such as fine-grained independence, abstraction and recursion.
  Probabilistic programming languages aim to close this representational gap, unifying general purpose programming with probabilistic modeling; literally, users specify a probabilistic model in its entirety (e.g., by writing code that generates a sample from the joint distribution) and inference follows automatically given the specification. These languages provide the full power of modern programming languages for describing complex distributions, and can enable reuse of libraries of models, support interactive modeling and formal verification, and provide a much-needed abstraction barrier to foster generic, efficient inference in universal model classes."

  Daniel Roy:
  > "The class of samplable distributions is, in a sense, the richest class you might hope to deal with. The question we asked was: is there an algorithm that, given a samplable distribution on two variables X and Y, represented by a program that samples values for both variables, can compute the conditional distribution of, say, Y given X=x, for almost all values for X? When X takes values in a finite, discrete set, e.g., when X is binary valued, there is a general algorithm, although it is inefficient. But when X is continuous, e.g., when it can take on every value in the unit interval [0,1], then problems can arise. In particular, there exists a distribution on a pair of numbers in [0,1] from which one can generate perfect samples, but for which it is impossible to compute conditional probabilities for one of the variables given the other. As one might expect, the proof reduces the halting problem to that of conditioning a specially crafted distribution. This pathological distribution rules out the possibility of a general algorithm for conditioning (equivalently, for probabilistic inference). The paper ends by giving some further conditions that, when present, allow one to devise general inference algorithms. Those familiar with computing conditional distributions for finite-dimensional statistical models will not be surprised that conditions necessary for Bayes’ theorem are one example."




selected papers - https://dropbox.com/sh/2m10m5bsctmd4zr/AADSvK7nWzyB7jViNXBuXghca


recent interesting papers - https://github.com/brylevkirill/notes/blob/master/recent%20papers.txt




### interesting papers


#### Gordon, Henzinger, Nori, Rajamani - ["Probabilistic Programming"](http://research.microsoft.com/pubs/208585/fose-icse2014.pdf)
>	"Probabilistic programs are usual functional or imperative programs with two added constructs: (1) the ability to draw values at random from distributions, and (2) the ability to condition values of variables in a program via observations. Models from diverse application areas such as computer vision, coding theory, cryptographic protocols, biology and reliability analysis can be written as probabilistic programs. Probabilistic inference is the problem of computing an explicit representation of the probability distribution implicitly specified by a probabilistic program. Depending on the application, the desired output from inference may vary - we may want to estimate the expected value of some function f with respect to the distribution, or the mode of the distribution, or simply a set of samples drawn from the distribution. In this paper, we describe connections this research area called “Probabilistic Programming” has with programming languages and software engineering, and this includes language design, and the static and dynamic analysis of programs. We survey current state  of the art and speculate on promising directions for future research."


#### De Raedt, Kimmig - ["Probabilistic (Logic) Programming Concepts"](https://lirias.kuleuven.be/bitstream/123456789/490338/1/deraedt_kimmig_mlj15.pdf)
>	"A multitude of different probabilistic programming languages exists today, all extending a traditional programming language with primitives to support modeling of complex, structured probability distributions. Each of these languages employs its own probabilistic primitives, and comes with a particular syntax, semantics and inference procedure. This makes it hard to understand the underlying programming concepts and appreciate the differences between the different languages. To obtain a better understanding of probabilistic programming, we identify a number of core programming concepts underlying the primitives used by various probabilistic languages, discuss the execution mechanisms that they require and use these to position and survey state-of-the-art probabilistic languages and their implementation. While doing so, we focus on probabilistic extensions of logic programming languages such as Prolog, which have been considered for over 20 years."

>	"First, there is an ongoing quest for efficient inference approaches for languages that support a broad range of programming concepts. Promising directions include lifted inference, which aims at exploiting symmetries and abstraction over individuals to speed up inference, knowledge compilation, which has contributed many data structures for compactly representing and efficiently querying various types of knowledge, and approximate methods such as MCMC, which is used in many probabilistic programming languages, but still requires proposal functions to be custom made for the program at hand. There also is a need for a clear understanding of the relative computational complexity of the various probabilistic languages and concepts that exist to date. Another question that has only seen partial answers so far is how to efficiently deal with evidence and constraints in different inference techniques. Adapting and extending program transformation and analysis techniques to the probabilistic setting promises opportunities to recognize and exploit program parts that are amenable to more efficient inference. Concepts such as time and dynamics require inference approaches that on the one hand exploit repeated structure, but on the other hand can also deal with changing structure over time. Last but not least, it still is a challenge to learn probabilistic programs, although a wide variety of learning techniques for probabilistic programming has already been developed. Many key challenges for both parameter and structure learning remain, many of which are related to efficient inference, as learning requires inference."

  - https://lirias.kuleuven.be/bitstream/123456789/504183/1/pp-tutorial-ijcai15.pdf




### interesting papers - inference


#### Tran, Hoffman, Saurous, Brevdo, Murphy, Blei - ["Deep Probabilistic Programming"](https://arxiv.org/abs/1701.03757)
>	"We propose Edward, a Turing-complete probabilistic programming language. Edward builds on two compositional representations - random variables and inference. By treating inference as a first class citizen, on a par with modeling, we show that probabilistic programming can be as flexible and computationally efficient as traditional deep learning. For flexibility, Edward makes it easy to fit the same model using a variety of composable inference methods, ranging from point estimation, to variational inference, to MCMC. In addition, Edward can reuse the modeling representation as part of inference, facilitating the design of rich variational models and generative adversarial networks. For efficiency, Edward is integrated into TensorFlow, providing significant speedups over existing probabilistic systems. For example, on a benchmark logistic regression task, Edward is at least 35x faster than Stan and PyMC3."


#### Kucukelbir, Ranganath, Gelman, Blei - ["Automatic Variational Inference in Stan"](http://arxiv.org/abs/1506.03431)
>	"Variational inference is a scalable technique for approximate Bayesian inference. Deriving variational inference algorithms requires tedious model-specific calculations; this makes it difficult to automate. We propose an automatic variational inference algorithm, automatic differentiation variational inference. The user only provides a Bayesian model and a dataset; nothing else. We make no conjugacy assumptions and support a broad class of models. The algorithm automatically determines an appropriate variational family and optimizes the variational objective. We implement ADVI in Stan (code available now), a probabilistic programming framework. We compare ADVI to MCMC sampling across hierarchical generalized linear models, nonconjugate matrix factorization, and a mixture model. We train the mixture model on a quarter million images. With ADVI we can use variational inference on any model we write in Stan."

>	"We develop automatic differentiation variational inference in Stan. ASVI leverages automatic transformations, an implicit non-Gaussian variational approximation, and automatic differentiation. This is a valuable tool. We can explore many models, and analyze large datasets with ease."

  - http://research.microsoft.com/apps/video/default.aspx?id=259601 (Kucukelbir, 18:30)


#### Ritchie, Horsfall, Goodman - ["Deep Armotized Inference for Probabilistic Programs"](https://arxiv.org/abs/1610.05735)
>	"Probabilistic programming languages are a powerful modeling tool, able to represent any computable probability distribution. Unfortunately, probabilistic program inference is often intractable, and existing PPLs mostly rely on expensive, approximate sampling-based methods. To alleviate this problem, one could try to learn from past inferences, so that future inferences run faster. This strategy is known as amortized inference; it has recently been applied to Bayesian networks and deep generative models. This paper proposes a system for amortized inference in PPLs. In our system, amortization comes in the form of a parameterized guide program. Guide programs have similar structure to the original program, but can have richer data flow, including neural network components. These networks can be optimized so that the guide approximately samples from the posterior distribution defined by the original program. We present a flexible interface for defining guide programs and a stochastic gradient-based scheme for optimizing guide parameters, as well as some preliminary results on automatically deriving guide programs. We explore in detail the common machine learning pattern in which a ‘local’ model is specified by ‘global’ random values and used to generate independent observed data points; this gives rise to amortized local inference supporting global model learning."

>	"In this paper, we presented a system for amortized inference in probabilistic programs. Amortization is achieved through parameterized guide programs which mirror the structure of the original program but can be trained to approximately sample from the posterior. We introduced an interface for specifying guide programs which is flexible enough to reproduce state-of-the-art variational inference methods. We also demonstrated how this interface supports model learning in addition to amortized inference. We developed and proved the correctness of an optimization method for training guide programs, and we evaluated its ability to optimize guides for Bayesian networks, topic models, and deep generative models."


#### Wingate, Goodman, Stuhlmuller, Siskind - ["Nonstandard Interpretations of Probabilistic Programs for Efficient Inference"](https://web.stanford.edu/~ngoodman/papers/WGSS-NIPS11.pdf)
>	"Probabilistic programming languages allow modelers to specify a stochastic process using syntax that resembles modern programming languages. Because the program is in machine-readable format, a variety of techniques from compiler design and program analysis can be used to examine the structure of the distribution represented by the probabilistic program. We show how nonstandard interpretations of probabilistic programs can be used to craft efficient inference algorithms: information about the structure of a distribution (such as gradients or dependencies) is generated as a monad-like side computation while executing the program. These interpretations can be easily coded using special-purpose objects and operator overloading. We implement two examples of nonstandard interpretations in two different languages, and use them as building blocks to construct inference algorithms: automatic differentiation, which enables gradient based methods, and provenance tracking, which enables efficient construction of global proposals."

>	"We have shown how nonstandard interpretations of probabilistic programs can be used to extract structural information about a distribution, and how this information can be used as part of a variety of inference algorithms. The information can take the form of gradients, Hessians, fine-grained dependencies, or bounds. Empirically, we have implemented two such interpretations and demonstrated how this information can be used to find regions of high likelihood quickly, and how it can be used to generate samples with improved statistical properties versus random-walk style MCMC. There are other types of interpretations which could provide additional information. For example, interval arithmetic could be used to provide bounds or as part of adaptive importance sampling. Each of these interpretations can be used alone or in concert with each other; one of the advantages of the probabilistic programming framework is the clean separation of models and inference algorithms, making it easy to explore combinations of inference algorithms for complex models. More generally, this work begins to illuminate the close connections between probabilistic inference and programming language theory. It is likely that other techniques from compiler design and program analysis could be fruitfully applied to inference problems in probabilistic programs."

>	"With an outline of probabilistic programming in hand, we now turn to nonstandard interpretations. The idea of nonstandard interpretations originated in model theory and mathematical logic, where it was proposed that a set of axioms could be interpreted by different models. For example, differential geometry can be considered a nonstandard interpretation of classical arithmetic. In programming, a nonstandard interpretation replaces the domain of the variables in the program with a new domain, and redefines the semantics of the operators in the program to be consistent with the new domain. This allows reuse of program syntax while implementing new functionality. For example, the expression “a ∗ b” can be interpreted equally well if a and b are either scalars or matrices, but the “∗” operator takes on different meanings. Practically, many useful nonstandard interpretations can be implemented with operator overloading: variables are redefined to be objects with operators that implement special functionality, such as tracing, reference counting, or profiling."




### interesting papers - applications


#### Lake, Salakhutdinov, Tenenbaum - ["Human-level Concept Learning Through Probabilistic Program Induction"](http://web.mit.edu/cocosci/Papers/Science-2015-Lake-1332-8.pdf)
>	"People learning new concepts can often generalize successfully from just a single example, yet machine learning algorithms typically require tens or hundreds of examples to perform with similar accuracy. People can also use learned concepts in richer ways than conventional algorithms - for action, imagination, and explanation. We present a computational model that captures these human learning abilities for a large class of simple visual concepts: handwritten characters from the world’s alphabets. The model represents concepts as simple programs that best explain observed examples under a Bayesian criterion. On a challenging one-shot classification task, the model achieves human-level performance while outperforming recent deep learning approaches. We also present several “visual Turing tests” probing the model’s creative generalization abilities, which in many cases are indistinguishable from human behavior."

>	"Vision program outperformed humans in identifying handwritten characters, given single training example"

>	"This work brings together three key ideas -- compositionality, causality, and learning-to-learn --- challenging (in a good way) the traditional deep learning approach"

  - http://youtube.com/watch?v=kzl8Bn4VtR8 (Lake)
  - http://youtu.be/quPN7Hpk014?t=21m5s (Tenenbaum)
  - http://techtalks.tv/talks/one-shot-learning-of-simple-fractal-concepts/63049/ (Lake)
  - https://github.com/brendenlake/BPL


#### Kulkarni, Kohli, Tenenbaum, Mansinghka - ["Picture: A Probabilistic Programming Language for Scene Perception"](http://mrkulk.github.io/www_cvpr15/)
>	"Recent progress on probabilistic modeling and statistical learning, coupled with the availability of large training datasets, has led to remarkable progress in computer vision. Generative probabilistic models, or “analysis-by-synthesis” approaches, can capture rich scene structure but have been less widely applied than their discriminative counterparts, as they often require considerable problem-specific engineering in modeling and inference, and inference is typically seen as requiring slow, hypothesize-and-test Monte Carlo methods. Here we present Picture, a probabilistic programming language for scene understanding that allows researchers to ex- press complex generative vision models, while automatically solving them using fast general-purpose inference machinery. Picture provides a stochastic scene language that can express generative models for arbitrary 2D/3D scenes, as well as a hierarchy of representation layers for comparing scene hypotheses with observed images by matching not simply pixels, but also more abstract features (e.g., contours, deep neural network activations). Inference can flexibly integrate advanced Monte Carlo strategies with fast bottom-up datadriven methods. Thus both representations and inference strategies can build directly on progress in discriminatively trained systems to make generative vision more robust and efficient. We use Picture to write programs for generative 3D face analysis, 3D human pose estimation, and 3D object reconstruction – each in under 50 lines of code, and each competitive with specially engineered baselines."

  - https://youtube.com/watch?v=quPN7Hpk014 (Tenenbaum)
  - https://youtu.be/-8QMqSWU76Q?t=44m8s (Mansinghka)


#### Ouyang, Tessler, Ly, Goodman - ["Practical Optimal Experiment Design with Probabilistic Programs"](https://arxiv.org/abs/1608.05046)
>	"Scientists often run experiments to distinguish competing theories. This requires patience, rigor, and ingenuity - there is often a large space of possible experiments one could run. But we need not comb this space by hand - if we represent our theories as formal models and explicitly declare the space of experiments, we can automate the search for good experiments, looking for those with high expected information gain. Here, we present a general and principled approach to experiment design based on probabilistic programming languages. PPLs offer a clean separation between declaring problems and solving them, which means that the scientist can automate experiment design by simply declaring her model and experiment spaces in the PPL without having to worry about the details of calculating information gain. We demonstrate our system in two case studies drawn from cognitive psychology, where we use it to design optimal experiments in the domains of sequence prediction and categorization. We find strong empirical validation that our automatically designed experiments were indeed optimal. We conclude by discussing a number of interesting questions for future research."


#### Krishnamurthy, Tafjord - ["Semantic Parsing to Probabilistic Programs for Situated Question Answering"](http://arxiv.org/abs/1606.07046)
>	"Situated question answering is the problem of answering questions about an environment such as an image. This problem requires interpreting both a question and the environment, and is challenging because the set of interpretations is large, typically superexponential in the number of environmental objects. Existing models handle this challenge by making strong -- and untrue -- independence assumptions. We present Parsing to Probabilistic Programs (P3), a novel situated question answering model that utilizes approximate inference to eliminate these independence assumptions and enable the use of global features of the question/environment interpretation. Our key insight is to treat semantic parses as probabilistic programs that execute nondeterministically and whose possible executions represent environmental uncertainty. We evaluate our approach on a new, publicly-released data set of 5000 science diagram questions, finding that our approach outperforms several competitive baselines."

>	"We present Parsing to Probabilistic Programs (P3), a novel model for situated question answering that embraces approximate inference to enable the use of arbitrary features of the language and environment. P3 trains a semantic parser to predict logical forms that are probabilistic programs whose possible executions represent environmental uncertainty. We demonstrate this model on a challenging new data set of 5000 science diagram questions, finding that it outperforms several competitive baselines and that its global features improve accuracy. P3 has several advantageous properties. First, P3 can be easily applied to new problems: one simply has to write an initialization program and define the execution features. Second, the initialization program can be used to encode a wide class of assumptions about the environment. For example, the model can assume that every noun refers to a single object. The combination of semantic parsing and probabilistic programming makes P3 an expressive and flexible model with many potential applications."


#### Perov, Wood - ["Learning Probabilistic Programs"](http://arxiv.org/abs/1407.2646)
>	"We develop a technique for generalising from data in which models are samplers represented as program text. We establish encouraging empirical results that suggest that Markov chain Monte Carlo probabilistic programming inference techniques coupled with higher-order probabilistic programming languages are now sufficiently powerful to enable successful inference of this kind in nontrivial domains. We also introduce a new notion of probabilistic program compilation and show how the same machinery might be used in the future to compile probabilistic programs for efficient reusable predictive inference."

>	"Higher-order probabilistic programming languages open up the possibility of doing inference over generative model program text directly via a generative prior over program text and the higher-order functionality of eval. This paper is a first step towards the ambitious goal of inferring generative model program text directly from example data. Inference in the space of program text is hard so, as a start, we present an account of our effort to directly infer sampler program text that, when evaluated repeatedly, produces samples with similar summary statistics to observational data."

>	"There are reasons to make this specific effort itself. One is the potential automation of the development of new entries in the special collection of efficient sampling procedures that humankind has painstakingly developed over many decades for common distributions, for example the Marsaglia and Box-Mulle samplers for the normal distribution. In this paper we develop preliminary evidence that suggests that such automated discovery might indeed be possible. In particular we perform successful leave-one-out experiments in which we are able to learn a sampling procedure for one distribution, i.e. Bernoulli, given only program text for others and observed samples. We do this by imposing a hierarchical generative model of sampling procedure text, fitting it to out-of-sample, human-written sampler program text, then inferring the program text for the left-out random variate distribution type given only sample values drawn from the same."

>	"The second reason for making such an effort has to do with “compiling” probabilistic programs. What we mean by compilation of probabilistic programs is somewhat more broad than both transformational compilation which compiles a probabilistic program into an MH sampler for the same and normal compilation of a probabilistic program to machine code that encodes a parallel forward inference algorithm. What we mean by probabilistic program compilation is the automatic generation of program text that when run will generate samples distributed ideally identically to the posterior distribution of quantities of interest in the original program, conditioned on the observed data. Concisely; given samples resulting from posterior inference in a probabilistic program, our aim is to learn program text that when evaluated generate samples from the same directly. The reason for expressing and approaching compilation in this generality is that simpler approaches to generalizing probabilistic programming posterior samples via a less-expressive model families will suffer precisely due to the compromise in expressivity. Distributions over expressions are valid posterior marginals in higher-order probabilistic programming languages. Compiled probabilistic programs must be capable of generating the same. This effort is also a first step towards such a compiler."

>	"Our approach to learning probabilistic programs relates to both program induction and statistical generalization from sampled observations. The former is usually treated as search in the space of program text where the objective is to find a deterministic function that exactly matches outputs given parameters. The latter, generalizing from data, is usually referred to as either density estimation or learning. We impose a prior on the program text and use Bayesian inference machinery to infer a distribution over program text given observations. Unlike other approaches we learn stochastic programs from sampled observation data rather than deterministic programs from input/output pairs."

>	"Generalizing from data is one of the main objectives of the fields of machine learning and statistics. It is important to note that what we are doing here is a substantial departure from almost all prior art in these fields in the sense that the learned representation of the observed data is that of generative sampling program text rather than, say, a parametric or nonparametric model from which samples can be drawn using some extrinsic algorithm. In our work the model is the sampler itself and it is represented as program code. We do full Bayesian inference, not greedy search, and the model family over which we search is ultimately more expressive as it is a high order language with stochastic primitives and, as a result, is capable of representing all computable probability distributions."

>	"While it is possible to manually specify production rule probabilities for the grammar we took a hierarchical Bayesian approach instead, learning from human-written sampler source code. We compute held-out production rules prior probabilities from this corpus in cross-validation way so that when we are inferring a probabilistic program to sample from F we update our priors using counts from all other sampling code in the corpus, specifically excluding the sampler we are attempting to learn. Our production rule probability estimates are smoothed by Dirichlet priors. Note that in the following experiments the production rule priors were updated then fixed during inference. True hierarchical coupling and joint inferences approaches are straightforward from a probabilistic programming perspective but result in inference runs that tak elonger to compute."

>	"The experiments we perform illustrate all three uses cases outlined for automatically learning probabilistic programs. We begin by illustrating the expressiveness of our prior over sampler program text. We then report results from experiments in which we test our approach in all three scenarios for how we can compute the ABC penalty d. The first set of experiments tests our ability to learn probabilistic programs that produce samples from known one-dimensional probability distributions. In these experiments d either probabilistically conditions on p-values of one-sample statistical hypothesis tests or on approximate moment matching. The second set of experiments addresses the cases where only a finite number of samples from an unknown real-world source are provided. The final experiment is a preliminary study in probabilistic program compilation where it is possible to gather a continuing set of samples."

>	"Our novel approach to program synthesis via probabilistic programming raises at least as many questions as it answers. One key high level question this kind of work sharpens is, really, what is the goal of program synthesis? By framing program synthesis as a probabilistic inference problem we are implicitly naming our goal to be that of estimating a distribution over programs that obey some constraints rather than as a search for a single best program that does the same. On one hand, the notion of regularising via a generative model is natural as doing so predisposes inference towards discovery of programs that preferentially possess characteristics of interest (length, readability, etc.). On the other hand, exhaustive computational inversion of a generative model that includes evaluation of program text will clearly remain intractable for the foreseeable future. For this reason greedy and stochastic search inference strategies are basically the only options available. We employ the latter, and MCMC in particular, to explore the posterior distribution of programs whose outputs match constraints knowing full-well that its actual effect in this problem domain, and, in particular finite time, is more-or-less that of stochastic search. We could add an annealing temperature and schedule to clarify our use of MCMC as search, however, while ergodic, our system is sufficiently stiff to not require quenching (and as a result almost certainly will not achieve maxima in general). It is pleasantly surprising, however, that the Monte Carlo techniques we use were able to find exemplar programs in the posterior distribution that actually do a good job of generalising observed data in the experiments we report. It remains an open question whether or not sampling procedures are the best stochastic search technique to use for this problem in general however. Perhaps by directly framing the problem as one of search we might do better, particularly if our goal is a single best program. Techniques ranging from genetic algorithms to Monte Carlo tree search all show promise and bear consideration. One interesting way to take this work forward is to introduce techniques from the cumulative/incremental learning community, perhaps by adding time-dependent and hierarchical dimensions to the program text generative model. In the specific context of learning sampler program text, it would be convenient if, for instance when learning the program text for sampling from a parameterised normal distribution, one had access to an already learned subroutine for sampling from a standard normal. In related work from the field of inductive programming large gains in performance were observed when the learning task was structured in this way. Our example inference tasks are just the start. What inspired and continues to inspire us is our the internal experience of our own ability to reason about procedure. Given examples, humans clearly are able to generate program text for procedures that compute or otherwise match examples. Humans can physically simulate Turing machines, and, it would seem clear, are capable doing something at least as powerful when deducing the action of a particular piece of program text from the text itself. No candidate artificial intelligence solution will be complete without the inclusion of such ability. Those without will always be deficient in the sense that it is apparent that humans can internally represent and reason about procedure. Perhaps some generalised representation of procedure is the actual expressivity class of human reasoning. It certainly can’t be less."

  - http://research.microsoft.com/apps/video/default.aspx?id=209278 (Perov, 37:00)




<brylevkirill (at) gmail.com>