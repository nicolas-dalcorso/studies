---
id: 202405081611
book_id: ImplPatt
name: Valores em Engenharia de Software
description: Descrição dos valores em Engenharia de Software segundo Kent Beck (Implementation Patterns)
tags:
  - computer-science/software-engineering
  - computer-science/software-patterns
doctype: study-note
---
# `= this.name`
`= this.description`

---
## $\S 1$ Valores
### Comunicação
- Dizemos que um código **comunica-se bem** se um leitor pode entendê-lo, modificá-lo ou utilizá-lo. Programação não deve ser voltada somente para o computador.
	- *Coisas boas acontecem* quando consideramos outras pessoas durante o processo de comunicação: o **código** torna-se **mais claro** e **mais fácil de ser lido**, há um **aumento no custo-benefício**, o **pensamento do programador torna-se mais claro** e o **estresse é menor**
- Lembre-se do [[Literate Programming (Donald Knuth)]]: **um programa deve ser lido como se fosse um livro**. Isto é, **deve ter enredo, ritmo *and delightful little turns of phrase***.

> [!info] Comunicação: o caso do `ScrollController`
> When Ward Cunningham and I first read about literate programs, we decided to try it. We sat down with one of the cleanest pieces of code in the Smalltalk image, the ScrollController, and tried to make it into a story. Hours later we had completely rewritten the code on our way to a reasonable paper. Every time a bit of logic was a little hard to explain, it was easier to rewrite the code than explain why the code was hard to understand. The demands of communication changed our perspective on coding.
> [[Implementation Patterns (Kent Beck)]], p. 11

- Uma vez que a maior parte do custo em desenvolvimento de software está na **fase pós-implementação**, torna-se necessário que o desenvolvedor **leia muito mais do que escreva código**; logo, se quisermos desenvolver **software barato**, devemos fazer **software legível**.

> [!tip] Comunicação: perspectiva
> Focusing on communication improves thinking by being more realistic. Part of the improvement comes from engaging more of my brain. When I think, “How would someone else see this?” different neurons are firing than when I’m just focused on myself and my computer. I take a step back from my isolated perspective and see my problem and solution anew. Another part of the improvement comes from the reduced stress of knowing that I am taking care of business, doing the right thing. Finally, as a socially oriented species, explicitly accounting for social issues is more realistic than working at pretending they don’t exist.
> [[Implementation Patterns (Kent Beck)]], p. 11

---

### Simplicidade
- Lembrar do [[The Visual Display of Quantitative Information (Edward Tufte)]]: dado um gráfico, a remoção de todas as marcas que não adicionam informação relevante, resulta em um novo gráfico muito mais fácil de entender que o original
- **Eliminar complexidade em excesso** permite àqueles que estão lendo, usando ou modificando programas a entendê-los mais rapidamente.
	- Alguma complexidade é inerente à resolução do problema, enquanto outras complexidades são marcas que demonstram má resolução do problema. É o excesso de informação que decrementa o valor de um software, e o torna mais difícil de modificar no futuro.
- Novamente, **um programa é muito mais vezes modificado do que implementado**, e o **excesso de complexidade torna muito mais difícil modificar um programa** ou **estender suas funcionalidades**

> Computing advances in waves of complexity and simplification. Mainframe architectures became more and more baroque until mini-computers came along. The mini-computer didn’t solve all the problems of a mainframe, but it turned out that for many applications those problems weren’t all that important. Programming languages, too, go through waves where they get more complex and then simpler. C begets C++, which begets Java, which is now becoming itself more complicated.
> Pursuing simplicity enables innovation. **JUnit** was much simpler than the testing tools it largely replaced. JUnit spawned a variety of look-alikes, add-ons, and new programming/testing techniques. The latest release,**JUnit 4**, has lost that “bare metal” feel, although I made or concurred with each of the complexifying decisions. Someday someone will come up with a much simpler way for programmers to write tests than JUnit. The new idea will enable a further wave of innovation.
> [[Implementation Patterns (Kent Beck)]], pp. 11-12

- Enquanto desenvolvedores, devemos **aplicar simplicidade em todos os níveis**
	- Formatar código de forma que nenhuma deleção de código possa ocorrer sem perda de informação
	- *Design with no extraneous elements*
	- Investigar os requisitos de forma a encontrar aqueles que são realmente essenciais
- **Comunicação** e **simplicidade** funcionam de mãos dadas: quanto menos complexidade, mas fácil é de se entender um sistema; quanto maior o foco em comunicação, mais fácil é ver quais aspectos da complexidade podem ser descartados.
	- Ocasionalmente, **simplificação torna um programa mais difícil de se entender**; nestes casos, devemos **escolher comunicação em primeiro lugar e redução da complexidade em segundo**; estes casos são, entretanto, raros

---


### Flexibilidade

> [!warning] Mal-uso da flexibilidade
> Dentre os três valores, a flexibilidade é o mais comumente mal utilizado para justificar programação ineficiente e técnicas de projeto pobres.
> >  To retrieve a constant, I’ve seen pro- grams look up an environment variable containing the name of a directory con- taining a file in which is found the constant value. Why all the complexity? Flexibility. Programs should be flexible, but only in ways they change. If the constant never changes, all that complexity is cost without benefit.
> >  [[Implementation Patterns (Kent Beck)]], p. 12

- Todo programa deve ser **fácil de modificar**: o custo real de um programa provavelmente só poderá ser medido após sua implementação, então devemos ser pacientes na adoção de complexidade desnecessária.

> [!info] Flexibilidade: uma dica
> Choose patterns that encourage flexibility and bring immediate benefits. For patterns with immediate costs and only deferred benefits, often patience is the best strategy. Put them back in the bag until they are needed. Then you can apply them in precisely the way they are needed.
> [[Implementation Patterns (Kent Beck)]], p. 12

> [!info] Flexibilidade e complexidade
> Flexibility can come at the cost of increased complexity. For instance, user- configurable options provide flexibility but add the complexity of a configuration file and the need to take the options into account when programming. Simplicity can encourage flexibility. In the above example, if you can find a way to eliminate the configurable options without losing value, you will have a program that is easier to change later.
> [[Implementation Patterns (Kent Beck)]], p. 13


> [!tip] Flexibilidade e comunicabilidade
> Enhancing the communicability of software also adds to flexibility. The more people who can quickly read, understand, and modify the code, the more options your organization has for future change
> [[Implementation Patterns (Kent Beck)]], p. 13

---
