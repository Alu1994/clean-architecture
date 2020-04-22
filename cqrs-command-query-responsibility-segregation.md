# Command Query Responsibility Segregation

- Segundo _**Bertrand Meyer**_ nós temos 2 tipos de métodos em POO.
  - Command:
    - Ele faz algo.
    - Ele **deve** modificar o estado do sistema.
    - **Não deve** retornar um valor.
  - Query:
    - Responde uma chamada/pergunta.
    - Ele **não deve** alterar o estado do sistema.
    - Ele **deve** retornar um valor.
- Também deveriamos separar os dois conceitos(_Command & Query_) **quando possível**, para não criar métodos que violem este princípio.
