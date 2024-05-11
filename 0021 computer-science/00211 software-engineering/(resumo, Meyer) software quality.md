---
id: 202404081823
name: Resumo do Capítulo "Software Quality" do [[Object-Oriented Software Construction]] de [[Bertrand Meyer]]
aliases:
  - Object-Oriented Software Construction - Software Quality
  - Qualidade de Software (B. Meyer)
tags:
  - computer-science/software-engineering
---
# Qualidade de Software
## Fatores que determinam a qualidade do software
Os fatores determinantes da qualidade do software visam garantir a construção de software *rápido*, *fácil de usar*, *confiável*, *seguro*, *legível*, *modular* e *estruturado*. Dividimos os fatores para alcançar tais objetivos em
- Fatores externos
	- relacionados à usabilidade e facilidade de uso do software; são facilmente reconhecidos pelos usuários do software ou do produto ao qual o software é embutido
	- **rapidez**, **facilidade de uso**, **confiabilidade** e **segurança** são fatores externos ao software;
	- os fatores externos tornam-se óbvios no produto final da construção do software; por serem percebidos pelos usuários, importam mais do que os fatores internos.
	- outros fatores externos são **corretude** (a propriedade do software de ser *correto* quanto ao esperado deste), **robustez** (reagir de forma adequada não somente aos comportamentos esperados do usuário ou do sistema como um todo, mas também às condições anormais de funcionamento), **extensibilidade** (o software deve poder ser *estendido* conforme necessário ou conforme as regras de negócio são modificadas; novas *features* devem ser implementadas sem a necessidade de refatorização de todo o sistema) e **reusabilidade** (muito relacionado à *modularidade*, o processo de construção de software deve ser capaz de desenvolver elementos individuais aplicáveis à construção de aplicações distintas e não necessariamente relacionadas entre si). A **compatibilidade** implica que queremos construir aplicações compatíveis com outras aplicações já em uso pelo usuário ou pelo sistema que embarcará nossa aplicação, enquanto a **portabilidade** é a meta a ser alcançada para que a aplicação possa ser executada em ambientes de software ou de hardware distintos, e não necessite portanto de uma máquina específica para ser executada.
	- **Eficiência** ou boa **performance** é a propriedade buscada em todo produto de engenharia e envolve utilizar a menor quantidade possível de recursos para executar o trabalho desejado de maneira correta. Em software, os recursos envolvem o próprio hardware (tempo de processamento, espaço ocupado em memória ou uso de memória secundária, uso de banda em aplicações em rede). Também é necessário lembrar que *optimização prematura é a origem de todo mal*, pois buscar otimizar sistemas que não estão corretos ou propriamente robustos gerará mais problemas e necessidade de refatorização do que benefícios ao projeto.
	- **Funcionalidade** é uma medida qualitativa da extensão das possibilidades do sistema, isto é, *daquilo que o sistema pode fazer.* Já a **pontualidade** é uma característica do time de desenvolvimento em calcular previamente, e cumprir o combinado, quanto ao tempo necessário para desenvolver o software. O excesso de funcionalidade (*creeping featurism*) é sempre tanto um inimigo da consistência interna do software, quanto da pontualidade, uma vez que a inserção de novas funcionalidades de forma descompromissada gerará o risco de não entregar o básico daquilo que é esperado da aplicação no tempo acordado.
	- Outros fatores externos: **verificabilidade** (facilidade em produzir testes e em testar o software, identificar falhas, validar procedimentos e acompanhar a propagação de erros), **integridade** (relacionado à proteção do código e dos dados do software quanto a exposição indevida ou a ataques), **reparabilidade** (habilidade de identificar e reparar erros ou defeitos de implementação) e **economia** (capacidade de cumprir as metas financeiras definidas no projeto; relaciona-se muito com a pontualidade).
- Fatores internos
	- relacionados, mais frequentemente, à percepção dos desenvolvedores ou analisadores do código, isto é, para aqueles que possuem acesso ao código-fonte do software
	- **legibilidade** e **modularidade** são fatores internos ao software.
	- **Documentação**
		- Documentação **externa**: o usuário deve ser capaz de entender as possibilidades, funcionalidades e o modo de usar o produto;
		- Documentação **interna**: voltada para descrever a implementação e a estrutura de um sistema, a documentação interna é a base sobre a qual o sistema é estendido.
		- Documentação das *interfaces dos módulos*: os desenvolvedores devem ser capazes de entender minimamente a interface de um módulo para poderem utilizá-lo na construção de outros módulos ou da aplicação geral.

## Princípios
- Simplicidade de *design*: arquiteturas simples serão sempre mais fáceis de serem adaptadas a mudanças do que arquiteturas complexas;
- Descentralização: os *módulos* que constituem o sistema devem ser o mais independentes o possível, tanto para $(1)$ poderem ser utilizados em aplicações distintas, quanto $(2)$ para que a alteração em um módulo não acarrete alterações (ou inviabilização do uso) de outros módulos.
- Padronização de processos, de formatos de arquivos, de estruturas de dados, de documentação, das rotinas de trabalho... devem ser sempre buscadas.
- *Make it right before you make it fast*: a optimização deve ser sempre posterior à implementação adequada à solução do problema.
- Não devemos **supor entender o usuário**: a clara obtenção dos requisitos e a captura daquilo que o cliente deseja são processos longos e muitas vezes difíceis; não devemos *supor* o que o usuário quer, nem esperar que o usuário irá se adaptar às dificuldades de um sistema complexo.
- *Creeping featurism*: sistemas que buscam implementar uma quantidade absurda de *features* para assim aumentar a funcionalidade do software correm o risco da perda de consistência (para que, afinal, serve esta aplicação?)
- **Trade-offs**: como todo produto de engenharia, o desenvolvimento de software deverá escolher entre diferentes virtudes. Como manter a integridade do software, sem torná-lo complexo e com pouca facilidade de uso? Como manter a economia e a pontualidade do projeto, sem afetar ou diminuir excessivamente a funcionalidade da aplicação? 

> Necessary as tradeoffs between quality factors may be, one factor stands out from the rest: **correctness**. There is never any justification for compromising correctness for the sake of other concerns such as efficiency. If the software does not perform its function, the rest is useless.
> Bertrand Meyer, *Object-oriented Software Construction*, p. 15

## Métodos para atingir os fatores externos: conceitos
- **Corretude** e **robustez** $\to$ métodos sistemáticos de construção de software, especificação formal, checagem dos processos de construção, tipagem estática, asserções (utilização de estruturas do tipo `assert` que testam certa propriedade do sistema), manejo automatizado da memória, detecção prévia de inconsistências e métodos para lidar com exceções e erros de forma adequada.
- **Extensibilidade** e **reusabilidade** $\to$ software deve ser fácil de ser modificado; para tanto, deve-se visar a construção de um repertório de componentes, elementos de software sob a forma de módulos, capazes de serem aplicados sobre diferentes projetos e com pouca ou nenhuma modificação. A propriedade de **modularidade** lida justamente com isto.

De modo geral, a abordagem orientada a objetos é de especial interesse para melhorar sistemas quanto aos fatores acima. Os outros fatores previamente citados também são positivamente afetados por este método.

## Manutenção de software
- **Manutenibilidade** é a propriedade relacionada à *facilidade de manutenção* de um sistema.
- Diferente de sistemas baseados em elementos físicos, o software não sofre desgaste com o tempo; ao contrário, sua manutenção refere-se às modificações necessárias para seu pleno funcionamento conforme o tempo passa e alterações de tecnologia, regras de negócio, necessidades dos usuários, introdução de novas *features* são introduzidas.
- Tanto a **extensão das funcionalidades** da aplicação, quanto as **mudanças em formatos de dados** são fontes de manutenção que requerem menor ou maior refatorização do código-fonte.
- Os **tipos abstratos de dados** permitem justamente a abstração (sic) dos fatores relacionados aos dados nas estruturas, permitindo que o programa lide separadamente com as modificações em formatos de dados e que estas modificações não necessitem alterações em outros módulos do software.












