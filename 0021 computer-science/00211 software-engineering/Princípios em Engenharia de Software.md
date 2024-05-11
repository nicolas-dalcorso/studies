---
id: 202405081814
book_id: ImplPatt
name: Princípios em Engenharia de Software
description: Descrição dos princípios em Engenharia de Software segundo Kent Beck (Implementation Patterns)
tags:
  - computer-science/software-engineering
  - computer-science/software-patterns
doctype: study-note
---
# `= this.name`
`= this.description`

## $\S 1$ Motivação

> [!info] Princípios: motivação
> Examining principles is valuable for several reasons. Clear principles can lead to new patterns, just as the periodic table of the elements led to the discovery of new elements. Principles can provide an explanation for the motivation behind a pattern, one connected to general rather than specific ideas. Choices about contradictory patterns are often best discussed in terms of principles rather than the specifics of the patterns involved. Finally, understanding principles provides a guide when encountering novel situations. 
> For example, when I encounter a new programming language I use my understanding of principles to develop an effective style of programming. I don’t have to ape existing styles or, worse, cling to my style in some other programming language (you can write FORTRAN code in any language, but you shouldn’t). Understanding principles gives me a chance to learn quickly and act with integrity in novel situations. What follows is the list of principles behind the implementation patterns.
> [[Implementation Patterns (Kent Beck)]], p. 13

## $\S 2$ Princípios
### Consequências Locais
- **Estruture o código de forma que *mudanças locais tenham consequências locais***
- Se uma mudança *aqui* causa modificações *ali*, então **o preço da modificação de software cresce dramaticamente**.
- Código composto por consequências majoritariamente locais é um código que mantém o valor da comunicação de forma eficiente, pois pode ser entendido gradualmente, sem ter que ser primeiro entendido como um todo, para depois entender as partes.
- O **custo de modificação de software** é uma **motivação primária** que inspira os padrões de implementação; portanto, o princípio das consequências locais mostra-se comum em diversos padrões distintos.

### Minimização da Repetição
- O princípio da minimização da repetição anda lado a lado com o princípio das consequências locais e devem, portanto, ser pensados juntamente.
- **Formas de repetição**:
	- Blocos de códigos repetidos: duplicação desta forma não é, necessariamente, ruim, mas **aumenta o preço de modificação do software**; uma forma de reduzir este problema é quebrar os programas em pedaços pequenos (*small statements, small methods, small objects, small packages*).
		- Blocos grandes da lógica do programa tendem a duplicar partes de outros blocos grandes da lógica.
		- É justamente essa característica que permite a existência de padrões de implementação: existem diferenças entre partes do código, mas também existem muitas semelhanças.
	- Hierarquias paralelas de classes: se, ao fazer uma modificação conceitual do programa requer que façamos modificações em duas ou mais hierarquias de classes, então dizemos que as modificações tem consequências que se espalham.


### Agrupamento da Lógica e dos Dados
- **Colocar lógica e dados juntos, quando estes operam juntos** no mesmo método, se possível, ou no mesmo objeto, ou, em último caso, no mesmo pacote.
- Para realizar uma modificação, é provável que tanto a lógica quanto os dados terão que ser modificados; logo, faz sentido que estes estejam próximos no código.
- Não é sempre simples perceber que determinados dados e determinada lógica fazem sentidos e deveriam ter sido escritos juntos. Muitas vezes isto é algo que percebemos *após* escrever o código.
	- Quando isso ocorre, é necessário escolher: mover os dados para a lógica, ou a lógica para os dados em um *helper object*
	- Às vezes isso não é possível no momento, porque não conseguimos comunicar de forma razoável o que queremos.


### Simetria
- Simetrias são comuns em programas:
	- Um método `add()` é acompanhado por um método `remove()`;
	- Um grupo de métodos recebem todos os mesmos parâmetros;
	- Todos os campos de um objeto tem a mesma *lifetime*
- Identificar e expressar de forma clara as simetrias do código tornam-o mais fácil de ler. Se o leitor entender metade da simetria, é provável que ele possa deduzir a metade restante.

```C
// Exemplo de código sem simetria
void process() {
	input();
	count++;
	output();
}
```

```C
// Alguma simetria, mas os métodos não se comunicam: `input()` e `output()` são operações nomeadas por sua intenção, isto é, pelo que fazem, enquanto `incrementCount()` é nomeado de acordo com sua implementação.
void process(){
	input();
	incrementCount();
	output();
}
```

```C
// Implementação na qual a simetria de intenção é mantida. `tally` significa registrar o score ou valor atual de um variável
void process(){
	input();
	tally();
	output();
}
```

> [!tip] Simetria e Eliminação de Repetição
> Often, finding and expressing symmetry is a preliminary step to removing duplication. If a similar thought exists in several places in the code, making them symmetrical to each other is a good first step towards unifying them.
> [[Implementation Patterns (Kent Beck)]], p. 16

### Expressão Declarativa
-  tudo o que puder ser descrito de forma imperativa tal que a leitura já indique a função, deverá ser feito.


### Taxa de Modificação
- colocar lógica e dados que modificam-se com a mesma taxa juntos, e lógica e dado que modificam-se em taxas distintas, separados;

> The rate of change applies to data. All the fields in a single object should change at roughly the same rate. For example, fields that are modified only during the activation of a single method should be local variables. Two fields that change together but out of sync with their neighboring fields probably belong in a helper object. If a financial instrument can have its value and currency change together, then those two fields would probably better be expressed as a helper Money object: 

```
setAmount(int value, String currency) { 
	this.value= value; 
	this.currency= currency; 
} 
```

torna-se:
```
setAmount(int value, String currency) { 
	this.value= new Money(value, currency); 
};
```

e por fim:
```
setAmount(Money value) { 
	this.value= value; 
}
```

---



