---
id: 202404231700
name: resumo do capítulo sobre tipos abstratos de dados do [[Code Complete]]
aliases:
  - Abstract Data Types
  - Tipos Abstratos de Dados (Code Complete)
tags:
  - computer-science/software-engineering
---

# Tipos Abstratos de Dados
- **Definição**: coleção em uma só estrutura de *dados* e de *operações* a serem aplicadas sobre estes dados. As operações permitem que o restante do sistema interaja (leia, escreva etc) com os dados do tipo.
- (*Modelagem de objetos do mundo real*) Permitem modelar conceitos e objetos do mundo real, ou do domínio do problema a ser resolvido, enquanto abstrações no código.
- (*Detalhes de implementação são privados*) Os desenvolvedores que utilizaram tipos abstratos de dados implementados por terceiros **não precisam** compreender a implementação. Se os métodos e os dados forem implementados utilizando boas práticas e o código for devidamente comentado, bastará saber os nomes dos dados e dos métodos para estender as funcionalidades do sistema.
- (*Tipos de dados abstratos são entidades modulares*) As alterações em um tipo não devem alterar aspectos de outros tipos; ou, no pior dos casos, esta alteração deverá ser mínima. Da mesma maneira, a alteração de algum método do tipo de dados abstrato não deverá afetar o funcionamento do sistema como um todo.
- (*Auto-documentação*) Tipos de dados bem implementados, coesos e coerentes exigiram pouca ou nenhuma documentação explícita, se forem implementados de forma legível e clara.

Diferentes linguagens de programação oferecem diferentes estratégias para implementar tipos de dados abstratos. Enquanto linguagens como `C` permitem que um tipo de dados abstrato seja implementado em um arquivo, e que somente alguns métodos sejam exportados (mantendo, desta forma, algumas funções privadas), outras linguagens não implementam estas funcionalidades.

Exemplo: tipo de dados abstrato para representar um arquivo.

```
FileDataType::
data String filepath;

---

function init();
function set_filepath(filepath);
function get_filepath();

function open();
function close();
function read();
function write();

function get_creation_date();
function get_last_acessed_date();
```

