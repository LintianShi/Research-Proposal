# Symbolic Execution and Program Testing

## Background & Motivation

1. The large-scale production of reliable programs is one of the fundamental requirements today. (in this paper is 1970s)
   * a program with mistakes is a threat in many ways
     * some examples: 火箭发射失败, 停电, 化疗事故

2. We have to validate or verify the correctness of a program

   * Program Testing: 
     
* “Program testing can be used to show the presence of bugs, but never to show their absence!” **Edsger W. Dijkstra**
  
* Formal proof: 
  
  * Short of tools. There is no proof assistant in 1970s.  Coq is first released in 1989. TLA+ was introduced in 1999.
  
  * Human makes mistakes. 
  
    一个P2P协议chord的例子. 原始证明: *Chord: A scalable peer-to-peer lookup service for internet applications*. 发现了原始证明里的错误: *Lightweight verification of network protocols: The case of chord*
  
    The confidence in this method depends on the care and accuracy employed in both the creation of the specification and in the construction of the proof step
  
  * Totally "physical work".
  
* Model checking(not mentioned in paper): 
  
  * not mature at that time
  
     * Same as formal proof. depends on the care and accuracy employed in the creation of the specification

## Brief Introduction to Symbolic Execution

1. This paper describes a practical approach between these two extremes. It is an enhanced testing technique
   * Instead of executing a program on a set of sample inputs, a program is "symbolically" executed for a set of classes of inputs
     * each symbolic execution result may be equivalent to a large number of normal test cases
     * These results can be checked against the programmer's expectations for correctness either formally or informally

2. The class of inputs characterized by each symbolic execution is determined by the dependence of the program's control flow on its inputs

3. the input classes are determined only by those inputs involved in the control flow, and symbolic testing promises to provide better results more easily than normal testing for most programs

## Symbolic Execution

1. Three assumptions: 
   * Programs deal only with integers having arbitrary magnitude
   * The "execution tree"(defined later) resulting from symbolic execution of many(most) programs is infinite
   * The symbolic execution of IF statements requires theorem proving which, even for modest programming languages, is mechanically impossible.

2. One can define an alternative "symbolic execution" semantics for a programming language where the real data objects need not be used but can be represented by arbitrary symbols.