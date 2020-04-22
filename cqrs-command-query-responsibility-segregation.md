# Command Query Responsibility Segregation

- Segundo _**Bertrand Meyer**_ nós temos 2 tipos de métodos em POO.
  - **Command**:
    - Ele faz algo.
    - Ele **deve** modificar o estado do sistema.
    - **Não deve** retornar um valor.
  - **Query**:
    - Responde uma chamada/pergunta.
    - Ele **não deve** alterar o estado do sistema.
    - Ele **deve** retornar um valor.
- Também deveriamos separar os dois conceitos(_Command & Query_) **quando possível**, para não criar métodos complexos e possívelmente problematicos que violem este princípio.

<p align="center">
  <img align="center" src="https://github.com/matsennin/domain-driven-design/blob/master/images/CQRS_Architecture.png" />
</p>

- Normalmente a divisão se da na camada de _application_ e fica divido em uma stack para Comandos e outra para Queries. E isso deve ser feito por alguns motivos:
  - As Queries devem ser otimizadas para leitura de dados.
  - Os Comandos devem ser otimizados para escrita de dados.
  - Comandos mudam estado, executam comportamentos nos objetos de domínio, levantam eventos e escrevem na base de dados.
  - Queries usam qualquer meio para retornar os dados de forma mais performatica, projetam os dados em formato de apresentação e disponibilizam ao usuário.
  - Seguindo as ideias dos dois conceitos a segregação e clareza do código aumentam.
  - CQRS é a ideia de Domain Centric Architecture implementado de uma maneira inteligente, pois ele sabe como conversar com o domínio, via _Commands_ e quando conversar direto com a base de dados via _Queries_.
  
