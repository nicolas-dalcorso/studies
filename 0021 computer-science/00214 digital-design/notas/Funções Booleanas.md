---
id: 202404251732
name: Funções Booleanas
aliases:
  - Boolean Functions
description: Definição de função booleana.
doctype: study-note
---
# `= this.name`
`= this.description`

## $\S 1$ Definições
> [!info] Definição: função booleana
> Seja $\{True, False\}$ o conjunto de valores booleanos. Então, uma função booleana $f$ terá a assinatura
> $$f: \{True, False\}^k \to \{True, False\}$$
> É comum também assumir o conjunto de valores possíveis como $\{0,1\}$:
> $$f:\{0,1\}^k \to \{0,1\}$$

> [!info] Definição: função booleana vetorial
> Uma função booleana $f$ é dita vetorial se, e somente se, 
> $$f: \{0,1\}^k \to \{0,1\}^m$$ 

### $\S 1.1$ Relações
#### Número de funções booleanas
Existem $2^{2^{k}}$ funções booleanas com $k$ argumentos. De forma análoga, existem $2^{2^{k}}$ [[Tabela-Verdade|tabelas-verdade]] com $2^k$ entradas.

#### Representações de funções booleanas
As funções booleanas podem ser representadas através de
1. [[Tabela-Verdade|Tabelas-Verdade]]: listagem de todos os possíveis valores para os argumentos e para as saídas.
	1. [[Diagrama de Marquand]] para a construção de [[Mapa de Karnaugh|Mapas de Karnaugh]].
	2. [[Diagramas de Decisão Binária]]: uma árvore binária é utilizada para representar a tabela-verdade;
	3. [[DIagrama de Venn]]
2. Representação proposicional: toda função booleana pode ser transformada em uma proposição de lógica de primeira ordem.
	1. Existem diversas formas possíveis, destacando-se nesta nota as *formas canônicas normais*

#### Propriedades de Funções Booleanas
Abaixo está uma lista de propriedades possíveis em funções booleanas.


| Propriedade Funcional | Descrição                                                                                                                                                                                   |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[Função Constante]]  | Função booleana que é sempre verdadeira ou sempre falsa, independente dos argumentos que recebe.                                                                                            |
| [[Função Monotônica]] | Para quaisquer combinações de dois valores, a mudança de um argumento de falso para verdadeiro somente pode causar a saída mudar de falso para verdadeiro (e não de verdadeiro para falso). |
| [[Função Linear]]     | Se alterarmos o valor de qualquer argumento da função, sempre ocorrerá que: OU a saída permanecerá a mesma, OU a saída sempre se alterará.                                                  |
| [[Função Simétrica]]  | A saída independente da *ordem* dos argumentos.                                                                                                                                             |
| [[Função Balanceada]] | Uma função booleana é dita balanceada se, e somente se, possui a mesma quantidade de $0$ e de $1$ em sua tabela-verdade.                                                                    |

---

## $\S 2$ *Links* e referências
- [[Álgebra Booleana]]
- [[Mapa de Karnaugh]]
