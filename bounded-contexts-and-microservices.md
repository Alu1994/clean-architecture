# Bounded Contexts

## O que é?
- Contextos limitados é basicamente você separar um grande domínio em domínios menores. Quando temos um domínio como por exemplo um sistema de compras, nós temos:
  - Compra
  - Produto
  - Estoque
  - E outras entidades complementares
- Tudo poderia ficar em um mesmo domínio, mas as coisas começam a ficar complicadas quando as peculiaridades da **Compra** aumentam e as do **Estoque** também. Ficaria bem mais simples o entendimento do sistema bem como o seu desenvolvimento se dividissimos em 2, cada um com sua responsabilidade.
    - 1 - Receber as Ordens de compra e gerenciar os processos dessas ordens.
    - 2 - Gerenciamento do Estoque de produtos que são utilizados nessas ordens.
- Isso causaria provavelmente em uma consistencia eventual, porém é uma troca justa, tendo em vista a maior clareza e separação das responsabilidades.

- Abaixo um outro exemplo:
  <p align="center">
    <img src="https://github.com/matsennin/domain-driven-design/blob/master/images/Single_Domain_Model.png" />
  </p>
  
  <p align="center">
    <img src="https://github.com/matsennin/domain-driven-design/blob/master/images/Overlaping_Contexts.png" />
  </p>
  
  <p align="center">
    <img src="https://github.com/matsennin/domain-driven-design/blob/master/images/Bounded_Contexts.png" />
  </p>

# Microservices

## O que é?
- Os limites de contextos nos levam aos microserviços. Microserviços dividem aplicações monolíticas com um super contexto, em subsistemas com contextos menores.
- Esses microserviços se comunicam através de interfaces bem especificadas, utilizando por exemplo Requests HTTP.
- Ele nos permite dividir equipes enormes que cuidam de um super contexto, em equipes menores que cuidam de contextos especificos.
- Cada um desses microserviços são muito independentes uns dos outros, podendo utilizar bases de dados diferentes, design patterns diferentes bem como linguagens de programação diferentes, tudo conforme suas necessidades especificas.
- Cada um dos microserviços podem ser publicados individualmente e escalados individualmente conforme a necessidade de cada um deles.

## Como dividir?
- Normalmente ele é divido por _Bounded Contexts_(Contextos Limitados) isso trás a vantagem de alta coesão e baixo acoplamento. O que ajuda ao time focar em um único domínio com suas regras. Com isso não há necessidade de conhecer nenhuma regra interna especifica de outro microserviço de outro time, somente suas interfaces para a devida comunicação.
