# Domain Driven Design

## [Clean Architecture](https://github.com/matsennin/domain-driven-design/blob/master/clean-architecture.md)
## [CQRS](https://github.com/matsennin/domain-driven-design/blob/master/cqrs-command-query-responsibility-segregation.md)

### Application Layer
   - É onde fica todo o caso de uso do projeto, as ações que são necessárias para cumprir um determinado objetivo, seja gravar um registro, executar um processo ou buscar um relatório.
   - Prós:
        - Foco no caso de uso, que é um dos pontos essenciais aos "habitantes" do projeto.
        - Fácil de entender, pois com o projeto quebrado em pequenos pedaços por assunto, fica tudo mais simples de se entender, ajudando assim no desenvolvimento e manutenção.
        - Segue o DIP(Princípio da Inversão de Dependência), deixando o código mais flexivel e sustentavel, e nos ajuda a decidir as implementações e evoluir a arquitetura ao longo do projeto.
   - Contras:
        - Camadas são dificeis de manter, e quanto mais camadas, mais complexo o projeto.
        - Exige mais tempo para decidir o que deve estar na camada de **Aplicação**, e o que deve estar na camada de **Domínio**. Ao invés de simplesmente jogar tudo em uma **Camada de Negócio**.
