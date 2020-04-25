# Bounded Contexts

- Contextos limitados é basicamente você separar um grande domínio em domínios menores. Quando temos um domínio como por exemplo um sistema de compras, nós temos:
  - Compra
  - Produto
  - Estoque
  - E outras entidades complementares
- Tudo poderia ficar em um mesmo domínio, mas as coisas começam a ficar complicadas quando as peculiaridades da **Compra** aumentam e as do **Estoque** também. Ficaria bem mais simples o entendimento do sistema bem como o seu desenvolvimento se dividissimos em 2, cada um com sua responsabilidade.
  1 - Receber as Ordens de compra e gerenciar os processos dessas ordens.
  2 - Gerenciamento do Estoque de produtos que são utilizados nessas ordens.
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
