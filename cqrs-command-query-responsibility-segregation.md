# Command Query Responsibility Segregation

## O que é CQRS?
- É a divisão das atividades por responsabilidade, é a ideia de Domain Centric Architecture implementado de uma maneira inteligente, pois ele sabe como conversar com o domínio, via _Commands_ e quando conversar direto com a base de dados via _Queries_.

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

## Como é divido?
<p align="center">
  <img align="center" src="https://github.com/matsennin/domain-driven-design/blob/master/images/CQRS_Architecture.png" />
</p>

- Normalmente a divisão se da na camada de _application_ e fica divido em uma stack para Comandos e outra para Queries. E isso deve ser feito por alguns motivos:
  - As Queries devem ser otimizadas para leitura de dados.
  - Os Comandos devem ser otimizados para escrita de dados.
  - Comandos mudam estado, executam comportamentos nos objetos de domínio, levantam eventos e escrevem na base de dados.
  - Queries usam qualquer meio para retornar os dados de forma mais performatica, projetam os dados em formato de apresentação e disponibilizam ao usuário.
  - Seguindo as ideias dos dois conceitos a segregação e clareza do código aumentam.
  
## Existem 3 tipos de implementação de CQRS
  ### "Single-database CQRS"
   - Esse tipo de CQRS tem somente 1 banco de dados, que normalmente é um SQL ou NoSQL.
   - Commandos executam comportamentos no domínio que modificam estados, depois são salvos na base de dados através de uma camada de persistência.
   - Queries são executadas diretas na base de dados, usando uma camada fina de acesso a dados.
   - É o mais simples dos 3.
  ### "Two-database CQRS"
   - Ele possuí 2 bancos de dados, um para leitura e outro para escrita.
   - O primeiro banco de dados é otimizado para escrita.
   - O segundo banco de dados é otimizado para leitura.
   - Os dados salvos no banco de dados de escrita são sincronizados através de uma transação coordenação dos dados ou usando um padrão de Consistencia Eventual.
   - Ele é mais complexo que o primeiro, porém ele beneficia as melhorias de performance na parte de leitura do projeto.
  ### Event Sourcing CQRS
   - Não é armazenado o estado corrente das entidades em uma base de dados normalizada.
   - É armazenado somente os eventos de modificações das entidades ao longo do tempo, representados como eventos que ocorreram nas entidades. O histórico de todos os eventos ocorridos é armazenado em um meio chamado de _Event Store_.
   - Quando precisamos saber o estado atual de uma entidade, nós reproduzimos os eventos ocorridos nessa entidade e acabamos com o seu estado atual.
   - Após isso e ter o estado atual, nós executamos nossa lógica de domínio e modificamos o estado da entidade. Esse novo evento será armazenado em nosso _Event Store_, que será executado quando o seu novo estado atual for requisitado.
   - Finalmente nós enviamos o estado corrente do domínio para a base de dados de leitura, para que nossas queries sejam rápidas.
   - Ele é o mais complexo dos 3.
   - Como temos todos os eventos ocorridos em uma entidade armazenados, teremos a completa auditoria do sistema.
   - Podemos reconstruir o estado de uma entidade em qualquer ponto do tempo, assim temos todo o histórico o que facilita muito também no _debug_.
   - É possível ter multiplas bases de dados de leitura.
   - É possível reconstruir a base de dados de produção simplesmente re-executando os eventos.
