---
layout: home
title:  "Meeting overview"
---
# Description of the Meeting

Algebraic effects and handlers are a uniform abstraction for expressing computational effects. The abstraction enables modular development of programs involving sophisticated control-flow patterns, while (optionally) guaranteeing the absence of certain undesired behavior. Effect handlers have been implemented in diverse programming languages, ranging from functional languages such as Haskell and OCaml, to imperative languages 1such as C and JavaScript. In particular, the next release of OCaml will be the first production-level language with built-in support for effect handlers. There are also industrial applications of effect handlers. As a representative example, the Pyro programming language of Uber has a library of effect handlers, which allows the user to easily implement inference algorithms for probabilistic programming.

In response to the growing use of effect handlers, researchers have been actively studying the theory and implementation of effect handlers. Of particular interest are the reasoning, performance, and typing of effect handlers, which are the main topics of [Shonan Meeting 146](https://shonan.nii.ac.jp/seminars/146/) on "Programming and Reasoning with Algebraic Effects and Effect Handlers" held in 2019.

At the same time, researchers have also been working on the practice of effect handlers. In particular, the goal of a prior [Dagstuhl Seminar 18172](https://www.dagstuhl.de/seminars/seminar-calendar/seminar-details/18172) “Algebraic Effect Handlers Go Mainstream” was to bring effect handlers to existing languages.

We believe that it is a good time to revisit the above theoretical challenges, but from a different perspective. Specifically, in addition to sharing new results about effect handlers, we transfer the knowledge from the effect handlers research back to designing languages with specific built-in effects, such as exceptions and concurrency. In particular, we plan to investigate how recent advances in the field of algebraic effects and handlers can improve the reasoning, performance, and typing of languages, even if they do not include effect handlers themselves.

**Reasoning** Handlers and equations both serve as a means to specify the behavior of algebraic effects. The former are well-suited for everyday programming, while the latter are useful for formal reasoning. Researchers have been attempting to give an equational account of effect handlers, but little progress has been made on integrating equations into existing languages with effect handlers. In this meeting, we explore practical approaches to equational reasoning of effect handlers that can be used for optimization purposes. In particular, we improve on the recent approaches that use types and fusion (Lukšič and Pretnar [2020], Yang and Wu [2021]). We also plan to discuss how to adapt the approaches to general-purpose languages with exceptions and concurrency (Ahman and Pretnar [2021]). In particular, we expect that many reasoning techniques for effect handlers will scale straightforwardly to exceptions, as effect handlers are a generalization of exception handlers.

**Performance** There are several sources of inefficiency in running programs with algebraic effects and handlers, such as the runtime search for handlers and the process of capturing continuations. The past few years have seen various techniques for reducing inefficiency, but each of them has certain limitations in terms of applicability and performance. In this meeting, we aim to find general and effective techniques for efficiently executing algebraic effects and handlers. To achieve this goal, we reuse ideas from various program transformations proposed recently (Schuster et al. [2020], Xie and Leijen [2021], Karachalias et al. [2021]). We also intend to discuss how to adapt such techniques to general-purpose languages with primitive effects, such as exceptions and region-based memory management (Schuster et al. [2022]). For instance, we conjecture that the similarity between handler lifetimes (Zhang et al. [2020]) and object lifetimes would help us derive optimizations for memory management from those for effect handlers.

**Typing** Many languages of algebraic effects and handlers are equipped with an effect system, which prevents undesired behavior during execution of programs. There are a variety of effect systems in the literature; some of them focus on expressiveness, while others prioritize ease of use. In this meeting, we seek for a sweet spot among different aspects of effect systems. Specifically, we compare type systems that enforce lexical handling (Biernacki et al. [2019], Brachthäuser et al. [2020], Zhang et al. [2020]) with those that enforce dynamic handling (Bauer and Pretnar [2013]), and type systems that are explicit about effect polymorphism (Leijen [2017], Convent et al. [2020]) with those that are implicit (Brachthäuser et al. [2020], Brachthäuser et al. [2022]). Based on the insights gained from effect handler studies, we are also interested in developing and improving effect systems for parallel, concurrent, and probabilistic programming languages (Xie et al. [2022], Nguyen et al. [2022]). Specifically, we believe that the discussion of lexical vs. dynamic handling and explicit vs. implicit polymorphism would help us increase the efficiency and user experience of these languages.

Solving these problems has two potential outcomes. First, it fosters uses of effect handlers and thus increases modularity and safety of real-world programs. Second, it leads to better implementation of effectful languages in general. We believe that having face-to-face discussions among effect handler experts is crucial to advance in this research area.

From the above problems, we draw the following specific topics for discussion at the meeting.

-    Effect handlers and delimited control operators (shift/reset, control/prompt, fcontrol/run)
-    Effect handlers and morphisms (mutumorphisms, futumorphisms, histomorphisms)
-    Effect handlers and parallelism
-    Effect handlers and quantitative types (linear types, affine types)
-    Lexical handlers vs. dynamic handlers
-    User experience of effect systems and effect polymorphism

To foster interaction among the participants, we plan to structure the meeting in the following way. On Day 1, we allocate a few poster sessions so that the participants can see who is working on which problem. The poster sessions will help us to synchronize on the current state and open questions. Together with the participants, we then choose the most interesting problems as topics for dedicated breakout sessions. During Days 2–4, we alternate presentations of participants and the chosen breakouts. Presentations include talks, demos, tutorials, etc., and may be of various length. On Day 5, we invite the participants of each breakout to summarize the discussion and present future directions.

## References

Danel Ahman and Matija Pretnar. Asynchronous effects. Proceedings of the ACM on Programming Languages, 5(POPL), jan 2021. doi: 10.1145/3434305.

Andrej Bauer and Matija Pretnar. An effect system for algebraic effects and handlers. In Reiko Heckel and Stefan Milius, editors, Algebra and Coalgebra in Computer Science, pages 1–16, Berlin, Heidelberg, 2013. Springer Berlin Heidelberg. ISBN 978-3-642-40206-7.

Dariusz Biernacki, Maciej Piróg, Piotr Polesiuk, and Filip Sieczkowski. Binders by day, labels by night: Effect instances via lexically scoped handlers. Proc. ACM Program. Lang., 4(POPL), dec 2019. doi: 10.1145/3371116.

Jonathan Immanuel Brachthäuser, Philipp Schuster, and Klaus Ostermann. Effects as capabilities: Effect handlers and lightweight effect polymorphism. Proceedings of the ACM on Programming Languages, 4(OOPSLA), November 2020. doi: 10.1145/3428194.

Jonathan Immanuel Brachthäuser, Philipp Schuster, Edward Lee, and Boruch-Gruszecki Aleksander. Effects, capabilities, and boxes: From scope-based reasoning to type-based reasoning and back. Proceedings of the ACM on Programming Languages, 6(OOPSLA), April 2022. doi: 0.1145/3527320.

Lukas Convent, Sam Lindley, Conor McBride, and Craig McLaughlin. Doo bee doo bee doo. Journal of Functional Programming, 30:e9, 2020. doi: 10.1017/S0956796820000039.

Georgios Karachalias, Filip Koprivec, Matija Pretnar, and Tom Schrijvers. Efficient compilation of algebraic effect handlers. Proceedings of the ACM on Programming Languages, 5(OOPSLA), October 2021. doi: 10.1145/3485479.

Daan Leijen. Type directed compilation of row-typed algebraic effects. In Proceedings of the 44th ACM SIGPLAN Symposium on Principles of Programming Languages, POPL 2017, page 486–499, New York, NY, USA, 2017. Association for Computing Machinery. ISBN 9781450346603. doi: 10.1145/3009837.3009872.

Žiga Lukšič and Matija Pretnar. Local algebraic effect theories. Journal of Functional Programming, 30:e13, 2020. doi: 10.1017/S0956796819000212.

Minh Nguyen, Roly Perera, Meng Wang, and Nicolas Wu. Modular probabilistic models via algebraic effects. arXiv preprint arXiv: 2203.04608, 2022.

Philipp Schuster, Jonathan Immanuel Brachthäuser, and Klaus Ostermann. Compiling effect handlers in capability-passing style. Proceedings of the ACM on Programming Languages, 4(ICFP), August 2020. doi: 10.1145/3408975.

Philipp Schuster, Jonathan Immanuel Brachthäuser, and Klaus Ostermann. Region-based resource management and lexical exception handlers in continuation-passing style. In European Symposium on Programming (ESOP 2022), 2022. To appear.

Ningning Xie and Daan Leijen. Generalized evidence passing for effect handlers: Efficient compilation of effect handlers to C. Proceedings of the ACM on Programming Languages, 5(ICFP), August 2021. doi: 10.1145/3473576.

Ningning Xie, Daniel Johnson, Dougal Maclaurin, and Adam Paszke. Parallel algebraic effect handlers. In ACM SIGPLAN Workshop on Partial Evaluation and Program Manipulation (PEPM 2022), 2022.

Zhixuan Yang and Nicolas Wu. Reasoning about effect interaction by fusion. Proceedings of the ACM on Programming Languages, 5(ICFP), August 2021. doi: 10.1145/3473578.

Yizhou Zhang, Guido Salvaneschi, and Andrew C. Myers. Handling bidirectional control flow. Proceedings of the ACM on Programming Languages, 4(OOPSLA), nov 2020. doi: 10.1145/3428207.

