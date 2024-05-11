---
id: 202405100936
doctype: study-note
book_id: KleinberTardos
tags:
  - computer-science/complexity-theory
  - computer-science/algorithm-analysis
name: Introdução aos Algoritmos de Divisão e Conquista
description: Definição de algoritmo de divisão e conquista. Aplicações comuns.
aliases:
  - Divide and Conquer Algorithms
  - Divide and Conquer
  - Divisão e Conquista
---
# `= this.name`
`= this.description`

---
## $\S 1$ Definição
> [!tip] Algoritmos de Divisão e Conquista: descrição informal
> O conceito de *divisão e conquista* referem-se a uma classe de técnicas algorítmicas nas quais **dividimos a entrada do problema em diversas partes**, e resolvemos cada parte problema de forma **recursiva**. Depois, **reunimos as soluções dos sub-problemas** para construir a **solução total**

- As técnicas de divisão e conquista são poderosas e, em muitos casos, são métodos simples. 
- A **análise do tempo de execução** de um algoritmo desta natureza envolve, geralmente, a **solução de uma relação de recorrência** que será o limite dos tempos de execução das sub-soluções. 
- O método de divisão e conquista é frequentemente utilizado juntamente com outros métodos de resolução de problemas, como [[Introdução aos Algoritmos de Programação Dinâmica|em programação dinâmica]] e [[Introdução aos Algoritmos Aleatórios|em algoritmos aleatórios]].

> [!tip] Divisão e Conquista: redução da complexidade em algoritmos polinomiais
> One thing to note about many settings in which divide and conquer is applied, including these, is that the natural brute-force algorithm may already be polynomial time, and the divide and conquer strategy is serving to reduce the running time to a lower polynomial. This is in contrast to most of the problems in the previous chapters, for example, where brute force was exponential and the goal in designing a more sophisticated algorithm was to achieve any kind of polynomial running time.
> [[Algorithm Design (Jon Kleinber, Éva Tardos)]], p. 210

---
## $\S 2$ Aplicações
1. Computação de uma **função distância** em conjuntos de objetos;
2. Encontrar o **par de pontos mais próximos entre si** em um plano;
3. **Multiplicação de inteiros**;
4. *Smoothing a noise signal*;
5. [[Algoritmos de Divisão e Conquista - MergeSort]]


---


