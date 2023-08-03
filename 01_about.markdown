---
layout: page
title: Purpose
permalink: /purpose/
---

<h1 class="page-heading">Purpose of the meeting</h1>

Algebraic effects and handlers are a uniform abstraction for expressing computational effects. The abstraction enables modular development of programs involving sophisticated control-flow patterns, while (optionally) guaranteeing the absence of certain undesired behavior. Effect handlers have been implemented in diverse programming languages, ranging from functional languages such as Haskell and OCaml, to imperative languages 1such as C and JavaScript. In particular, the next release of OCaml will be the first production-level language with built-in support for effect handlers. There are also industrial applications of effect handlers. As a representative example, the Pyro programming language of Uber has a library of effect handlers, which allows the user to easily implement inference algorithms for probabilistic programming.

In response to the growing use of effect handlers, researchers have been actively studying the theory and implementation of effect handlers. Of particular interest are the reasoning, performance, and typing of effect handlers, which are the main topics of [Shonan Meeting 146](https://shonan.nii.ac.jp/seminars/146/) on "Programming and Reasoning with Algebraic Effects and Effect Handlers" held in 2019.

At the same time, researchers have also been working on the practice of effect handlers. In particular, the goal of a prior [Dagstuhl Seminar 18172](https://www.dagstuhl.de/seminars/seminar-calendar/seminar-details/18172) “Algebraic Effect Handlers Go Mainstream” was to bring effect handlers to existing languages.

We believe that it is a good time to revisit the above theoretical challenges, but from a different perspective. Specifically, in addition to sharing new results about effect handlers, we transfer the knowledge from the effect handlers research back to designing languages with specific built-in effects, such as exceptions and concurrency. In particular, we plan to investigate how recent advances in the field of algebraic effects and handlers can improve the reasoning, performance, and typing of languages, even if they do not include effect handlers themselves.

**Reasoning:** Handlers and equations both serve as a means to specify the behavior of algebraic effects. The former are well-suited for everyday programming, while the latter are useful for formal reasoning. Researchers have been attempting to give an equational account of effect handlers, but little progress has been made on integrating equations into existing languages with effect handlers. In this meeting, we explore practical approaches to equational reasoning of effect handlers that can be used for optimization purposes. In particular, we improve on the recent approaches that use types and fusion. We also plan to discuss how to adapt the approaches to general-purpose languages with exceptions and concurrency. In particular, we expect that many reasoning techniques for effect handlers will scale straightforwardly to exceptions, as effect handlers are a generalization of exception handlers.

**Performance:** There are several sources of inefficiency in running programs with algebraic effects and handlers, such as the runtime search for handlers and the process of capturing continuations. The past few years have seen various techniques for reducing inefficiency, but each of them has certain limitations in terms of applicability and performance. In this meeting, we aim to find general and effective techniques for efficiently executing algebraic effects and handlers. To achieve this goal, we reuse ideas from various program transformations proposed recently. We also intend to discuss how to adapt such techniques to general-purpose languages with primitive effects, such as exceptions and region-based memory management. For instance, we conjecture that the similarity between handler lifetimes and object lifetimes would help us derive optimizations for memory management from those for effect handlers.

**Typing:** Many languages of algebraic effects and handlers are equipped with an effect system, which prevents undesired behavior during execution of programs. There are a variety of effect systems in the literature; some of them focus on expressiveness, while others prioritize ease of use. In this meeting, we seek for a sweet spot among different aspects of effect systems. Specifically, we compare type systems that enforce lexical handling with those that enforce dynamic handling, and type systems that are explicit about effect polymorphism with those that are implicit. Based on the insights gained from effect handler studies, we are also interested in developing and improving effect systems for parallel, concurrent, and probabilistic programming languages. Specifically, we believe that the discussion of lexical vs. dynamic handling and explicit vs. implicit polymorphism would help us increase the efficiency and user experience of these languages.

Solving these problems has two potential outcomes. First, it fosters uses of effect handlers and thus increases modularity and safety of real-world programs. Second, it leads to better implementation of effectful languages in general. We believe that having face-to-face discussions among effect handler experts is crucial to advance in this research area.

From the above problems, we draw the following specific topics for discussion at the meeting.

-    Effect handlers and delimited control operators (shift/reset, control/prompt, fcontrol/run)
-    Effect handlers and morphisms (mutumorphisms, futumorphisms, histomorphisms)
-    Effect handlers and parallelism
-    Effect handlers and quantitative types (linear types, affine types)
-    Lexical handlers vs. dynamic handlers
-    User experience of effect systems and effect polymorphism
