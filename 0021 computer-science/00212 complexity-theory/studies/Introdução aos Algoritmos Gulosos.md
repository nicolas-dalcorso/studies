---
id: 202405100912
name: Introdução aos Algoritmos Gulosos
tags:
  - computer-science/complexity-theory
  - computer-science/algorithm-analysis
description: Definição de algoritmo guloso. Técnicas para provar algoritmos gulosos. Aplicações comuns aos algoritmos gulosos.
aliases:
  - Introduction to Greedy Algorithms
  - Greedy Algorithms
  - Algoritmos Gulosos
doctype: study-note
---
# `= this.name`
`= this.description`

---
## $\S 1$ Definições
> It is hard, if not impossible, to define precisely what is meant by a *greedy algorithm*. **An algorithm is greedy if it builds up a solution in small steps, choosing a decision at each step myopically to optimize some underlying criterion**. One can often design many different greedy algorithms for the same problem, each one locally, incrementally optimizing some different measure on its way to a solution.
> [[Algorithm Design (Jon Kleinber, Éva Tardos)]], p. 115

-  Um **algoritmo guloso** é um algoritmo que, a cada iteração **escolhe** a próxima **decisão** (isto é, *decide a cada passo*), qual será a estratégia ótima **no momento**, de acordo com algum **critério**.
	1. É possível desenvolver mais de um algoritmo guloso para o mesmo problema, cada um localmente, de modo a incrementalmente otimizar alguma medida, isto é, de acordo com algum critério, até chegar à solução.
	2. Quando um algoritmo é bem sucedido em resolver um problema não-trivial, descobrimos algo em relação ao problema em si: trata-se de um problema que possui **regras locais** para a construção de soluções ótimas. Alguns problemas, entretanto, não terão uma solução ótima utilizando algoritmos gulosos mas terão soluções *próximas* ao ótimo (heurísticas).
	3. É possível escrever algoritmos gulosos para quase qualquer problema, mas encontrar cenários nos quais estes algoritmos funcionam bem é um desafio interessante.


## $\S 2$ Provar a eficiência de um algoritmo guloso
- Para provar a eficiência de um algoritmo guloso, temos duas estratégias:
	1. Provar que, a cada passo, o algoritmo guloso está **a frente de qualquer outro algoritmo a cada passo**; ou
	2. Encontra-se uma solução para o problema e, gradualmente, transformamos esta solução na solução possível de ser construída por um algoritmo guloso, sem perda de qualidade.
	3. Em ambas as estratégias, precisamos provar que o método do algoritmo guloso encontrará uma solução que é tão boa quanto qualquer outra solução ao problema.

## $\S 3$ Aplicações comuns para algoritmos gulosos
- Algumas das **aplicações mais conhecidas** para algoritmos gulosos são
	1. Encontrar o **menor caminho em um grafo**;
	2. **Minimum Spanning Tree Problem**;
	3. Construção de **códigos de Huffman** para compressão de dados;
	4. Relação entre *spanning trees* e *minimum clustering*; e
	5. **Minium-Cost Arborescence Problem**


