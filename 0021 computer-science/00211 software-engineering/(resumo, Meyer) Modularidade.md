---
id: 202404082120
name: Resumo do Capítulo (3) "Modularity" do [[Object-Oriented Software Construction]] de [[Bertrand Meyer]]
aliases:
  - Object-Oriented Software Construction - Software Quality
  - Qualidade de Software (B. Meyer)
tags:
  - computer-science/software-engineering
---

# Modularidade
Um dos maiores objetivos da construção de software de qualidade é atender os [[(resumo, Meyer) software quality|fatores externos de qualidade de software]] de **extensibilidade** e **reusabilidade** para a construção de *arquiteturas flexíveis* compostas por elementos autônomos. Tais elementos autônomos (isto é, que podem ser utilizados em aplicações distintas com pouca ou nenhuma alteração, e que não dependem, ou dependem minimamente, de outros elementos) são chamados **módulos** e são o objeto do estudo da **modularidade de software**.

O *método de construção de software modular*, portanto, é aquele que visa a construção de programas que são compostos por elementos auto-contidos e organizados em arquiteturas estáveis. Dessa forma, uma aplicação modular terá uma arquitetura simples que ligará os módulos autônomos na sua implementação.

## Critérios do *design* modular
### **Decomponibilidade**
Os módulos devem ser capazes de implementar a decomposição do aplicação em partes menores e menos complexas. Isto é semelhante à estratégia de *dividir* um problema em *sub-problemas* menores e atacá-los individualmente: na construção de software modular, quebramos o problema em partes menores e construímos soluções para cada parte. A aplicação final será, portanto, uma composição de módulos, cada um resolvendo uma parte do problema.
- **Divisão de trabalho**: o sistema pode ser decomposto em sub-sistemas, nos quais o trabalho é dividido entre grupos e pessoas.
- As **dependências entre subsistemas** devem ser mínimas: uma grande dependência acarretará a necessidade de modificar outros módulos para resolver problemas em um módulo específico, além de afetar a velocidade de desenvolvimento nos times distintos que participam do projeto;
- **As dependências devem ser conhecidas**: caso contrário, a implementação de um módulo poderá funcionar, mas sua interação com outro módulo pode não ser ótima, ocasionando um produto final que simplesmente não funciona.
- O desenvolvimento de **hierarquias *top-down*** são uma solução interessante para este problema: os designers da arquitetura do sistema especificam uma descrição abstrata de cada parte do sistema e depois a refinam, decompondo cada subsistema em unidades menores, possivelmente *atômicas*, suficientemente com baixo nível de abstração (para lidar diretamente com o problema a ser solucionado na implementação).

### Componibilidade
Conforme escrevemos acima, devemos ser capazes de dividir o problema a ser resolvido em sub-problemas. Os módulos estarão associados às soluções que, quando compostas, resultarão na solução do problema total.
A decomponibilidade lida com esta quebra, enquanto a componibilidade visa extrair elementos de software do contexto no qual eles foram originalmente desenvolvidos.
Queremos que o software seja construído a partir da composição de módulos, semelhante à composição matemática de funções ou sua aplicação no paradigma da programação funcional.

**Componibilidade é independente da decomponibilidade**: o design de uma arquitetura *top-down* não necessariamente produzirá um design hábil para composição de módulos (defino à atomicidade dos módulos desenhados)

### Compreensibilidade
Os módulos devem ser *compreensíveis* e auxiliarem à compreensão geral da aplicação. O leitor humano (desenvolvedor, que trabalhará com, no mínimo, a interface do módulo) deverá ser capaz de lê-lo e entendê-lo sem ter que consultar os outros módulos do projeto (ou, no pior caso, consultando poucos outros módulos).
- Para que poucos ou nenhum outros módulos sejam consultados, busca-se diminuir **dependências sequenciais**, isto é, um módulo $A$ que depende diretamente de um módulo $B$ que, por sua vez, depende de um módulo $C$. Portanto, para usarmos o módulo $A$, será necessário conhecer e compreender tanto o módulo $B$ quanto o módulo $C$. Se o projeto fosse implementado de outra maneira, talvez fosse possível utilizar cada um dos módulos sem, no entanto, preocupar-se com os demais.
- A compreensibilidade auxiliará a implementar **módulos reutilizáveis**. Tais módulos podem ser usados em aplicações distintas com pouca ou nenhuma adaptação, o que economizará tempo e recursos para o time de desenvolvedores (ver os fatores externos de *pontualidade* e *economia*). Para tanto, é necessário que os módulos sejam plenamente documentados.

### Continuidade
Esta propriedade da modularidade está intimamente conectada ao fator externo de qualidade da **extensibilidade** de software. Queremos que cada módulo seja *atômico* de modo que uma alteração em um módulo $A$ ocasione pouca ou nenhuma alteração nos módulos $B$ ou $C$. De forma análoga, a implementação de uma nova funcionalidade poderá fazer uso de vários módulos, sem necessariamente requerer que estes sejam alterados.

### Proteção
Os módulos devem ser *protegidos* tal que se uma excepção ou um erro ocorre em um módulo, este comportamento anormal deve ser retido e tratado no módulo, sem necessariamente afetar os demais módulos; ou, no pior dos casos, o erro pode ser propagado para poucos módulos vizinhos.

## Regras para garantir a modularidade
- **Mapeamento Direto**
	- A arquitetura deve deixar o mais claro possível a relação entre o **domínio do problema** e o **domínio da solução**

> [!info] Mapeamento direto
> *The modular structure devised in the process of building a software system should remain compatible with any modular structure devised in the process of modeling the problem domain.*

- **Poucas Interfaces**
	- Restringe o número de *canais de comunicação* entre módulos de uma arquitetura.
	- A solução implementada em um módulo deve ser máxima no sentido de buscar resolver aquele sub-problema de maneira integral, ou algo perto disto.

> [!info] Poucas interfaces
> *Every module should communicate with as few others as possible.*
> Se um sistema é composto por $n$ módulos, então o número de conexões intermodulares deve ser no mínimo $n-1$ (que é o caso de um módulo central que chama dos demais módulos apenas uma vez) e no máximo $\frac{n(n-1)}{2}$ vezes.
> ![[Pasted image 20240409200259.png]]

> [!about] Comunicação entre módulos
> A comunicação entre módulos pode ocorrer $(1)$ através de chamadas a procedimentos do outro módulo, $(2)$ divisão de estruturas de dados etc.

- **Interfaces Pequenas**
	- O princípio das interfaces pequenas ou do **acoplamento fraco** (*weak coupling*) relaciona-se com o tamanho das conexões intermodulares:

> [!info] Interfaces pequenas (acoplamento fraco)
> *If two modules communicate, they should exchange as little information as possible*
> Além de reduzir o número de conexões intermodulares, também queremos que estas conexões sejam de tamanho reduzido, de modo que cada módulo dependa minimamente dos demais. Quando temos uma dependência muito grande, dizemos que os módulos possuem **acoplamento forte** ou *intimidade inadequada*.

- **Interfaces Explícitas**
	- Quando dois módulos se comunicam, é necessário que esta comunicação seja **óbvia**, **bem documentada** e **explícita, pública**.
	- Isto garantirá uma maior tendência tanto à *decomponibilidade* quanto à *componibilidade* dos módulos na construção da aplicação, pois saberemos exatamente como os módulos interagem entre si.

> [!info] Interfaces explícitas
> *Whenever two modules $A$ and $B$ communicate, this must be obvious from the text of $A$ or $B$ or both.*

- **Implementação privada** (*information hiding*)
	- O desenvolvedor irá escolher racionalmente quais informações são necessárias a serem expostas na interface do módulo, para que outros desenvolvedores possam fazer pleno uso deste módulo;
	- Entretanto, uma possivelmente grande parte da implementação **não será** explicitamente exposta, e será mantida **privada**.
	- A **interface** de um módulo contém as **propriedades públicas** do módulo, necessárias e essenciais para seu uso. As **propriedades privadas**, como os **detalhes de implementação**, não são necessárias ou essenciais para o uso do módulo e são mantidas secretas.

> [!info] *Information Hiding*
> *The designer of every module must select a subset of the module’s properties as the official information about the module, to be made available to authors of client modules.*

## 5 Princípios
1. **Linguistic Modular Units principle** (princípio linguístico das unidades modulares $?$): os módulos devem corresponder a unidades sintáticas da linguagem utilizada. Os módulos devem ser arquitetados de modo a estabelecer uma correspondência com a linguagem (de programação, de especificação, de design) utilizado.
2. **Princípio da Auto-Documentação**: *toda* informação sobre um módulo *deve estar no próprio módulo*.
3. **Princípio do Acesso Uniforme**: todos os *serviços* oferecidos por um módulo devem estar disponíveis através de uma **notação uniforme de acesso**; isto é, a implementação do acesso aos serviços oferecidos de um módulo deve ser padronizada e constante.
4. **Princípio Aberto-Fechado**: *módulos devem ser ao mesmo tempo fechados e abertos*.
	- **Abertos** pois **podem ser estendidos**, expandidos, terem suas estruturas de dados aumentadas (introdução de novos campos de dados, por exemplo) ou seu conjunto de operações aumentado;
	- **Fechados** quando seu uso é feito por outros módulos, a fim de não aumentar consideravelmente a dependência intermodular. 
5. **Princípio da Escolha Única**: consequência do princípio aberto-fechado e da política de esconder informações pertinentes somente à implementação, o princípio da escolha única afirma que se várias alternativas para suprir um serviço estão disponíveis no sistema (na aplicação como um todo), somente um módulo deve saber quais são as alternativas possíveis. Caso alterações posteriores sejam introduzidas, então somente este módulo deverá ser alterado na sua introdução. Todos os demais módulos deverão continuar funcionando normalmente, pois não serão dessa forma afetados.

---