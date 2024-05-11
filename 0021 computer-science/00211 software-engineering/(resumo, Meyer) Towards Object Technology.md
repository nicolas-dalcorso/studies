---
id: 202404231730
name: Resumo do Capítulo (5) "Towards Object Technology" do [[Object-Oriented Software Construction]] de [[Bertrand Meyer]]
aliases:
  - Object-Oriented Software Construction - Software Quality
  - Qualidade de Software (B. Meyer)
tags:
  - computer-science/software-engineering
---
## Software orientado a Objetos
1. A base arquitetônica do software orientado a objetos são os *módulos*, deduzidos sobre **tipos de objetos** (geralmente *tipos abstratos de dados*) aos quais manipula.
	1. **Identificar** os tipos de objetos relevantes. **Descrever** os tipos e suas **relações com outros tipos**. **Determinar** o uso de cada objeto no sistema como um todo.
	2. Fazemos um mapeamento dos objetos do mundo real (domínio do problema) para tipos de dados abstratos a serem implementados. Esses tipos são, geralmente, implementados enquanto **classes**, que possuem tanto campos para dados, quanto métodos (funções de classe).
	3. As classes devem ser construídas levando em consideração seu **reuso**.
	4. As **relações entre classes** devem ser claras e bem-documentadas (se sua implementação já não for legível o suficiente)

## Diferenças entre a decomposição funcional e a decomposição orientada a objetos
Quando nos deparamos com um problema do mundo concreto a ser modelado em software, diversas estratégias distintas de mapeamento podem ser utilizadas. Dentre elas, destacam-se a decomposição orientada à funções e a decomposição orientada a objetos.

A decomposição funcional irá modelar os objetos do mundo real enquanto funções no software. Um programa, portanto, será uma composição destas funções.

Já a decomposição orientada a objetos permite uma abstração mais próxima à realidade por mapear cada objeto do domínio do problema em um ou mais tipos de objetos em software. Assim, as propriedades (dados) do objeto serão variáveis de cada instância da classe, e as transformações sobre objetos reais serão os métodos de classe. As interações entre as partes do problema serão relações interclasses.