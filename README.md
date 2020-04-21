# Domain Driven Design

## Clean Architecture

- O principal motivo para implementar Arquitetura limpa é para o beneficio de seus "habitantes".
    - **É em pról dos usuários do sistema:** para que ele tenha a melhor experiencia possivel.
    - **É em pról dos desenvolvedores do sistema:** para que tudo desenvolvido seja de mais simples entendimento, desenvolvimento e manutenção.
    - Nada de **egos ou desejos**.
    - **Implementações complexas** só devem ser feitas caso o beneficio ao usuário/desenvolvedor seja maior do que sua complexidade.
    - **Foco no essencial** para o usuário.
    - Construir somente **o que é necessário quando for necessário**.
    - A Arquitetura Limpa ajuda na **Otimização e Manutenabilidade**, que é a maioria das atividades do nosso dia a dia.

### Domain Centric Architecture

- O principal motivo para implementar o Modelo de Arquitetura Centrada em Domínio é focar no que é mais importante o Dominio de Negócio.
    - Tipos de Domain Centric Architecture:
        - Hexagonal (by: Alistair Cockburn)
        - Onion (by: Jeffrey Palermo)
        - Clean (by: Uncle Bob [Robert C. Martin])
    - Prós:
        - **Focar no domínio** é essencial para os "habitantes", pois é o ponto mais importante para eles na nossa arquitetura.
        - Nos da **menos acoplamento** entre a lógica de domínio e os detalhes de implementação como apresentação, banco de dados e o sistema operacional. Com isso o sistema fica mais flexível e adaptável, e mais simples de evoluir a arquitetura ao redor durante os anos de desenvolvimento e manutenção do projeto.
        - **Nos possibilita usar o DDD**, que é um auxiliar para generenciar domínios de negócio com um alto grau de complexidade.
    - Contras:
        - **Mudanças são difíceis**, pelo fato de nem todos os desenvolvedores saberem, as vezes ter somente 1 pessoa no time que saiba a fundo sobre o padrão, torna a utilização dele complicada, pois é necessário conhecimento estruturado e tempo para passar para frente.
        - **Requere mais análise**, para saber exatamente o que pertence a camada de Domínio e o que pertence a camada de Aplicação.
        - **Maior custo inicial**, no começo o custo pode ser maior devida a maior complexidade de implementação do padrão, mas normalmente ela se paga ao passar do tempo.
- **Obs**: Um domínio não pode ter nada além do domínio de negócio em si que será representado no código, tudo fora isso, classes, métodos, qualquer código que não represente o domínio de négocio, deve ficar fora deste projeto.
    - Ex: 
        - Camadas de apresentação
        - Infraestrutura
        - Persistencia

### O que são Layers?
   - Layers são limites ou partições verticais de um aplicativo ou projeto que ajudam a gerenciar complexidade.
        - Eles ajudam a:
            - Representar diferentes níveis de abstração
            - Manter o princípio de responsabilidade única
            - Isolar grupos e skills
            - Suportar várias implementações
            - E ajudar nas alterações e variações.
        
        

### Application Layer
   - É onde fica todo o caso de uso do projeto, as ações que são necessárias para cumprir um determinado objetivo, seja gravar um registro, executar um processo ou buscar um relatório.

#### Classic Three-Layer Architecture
   <img src="https://github.com/matsennin/domain-driven-design/blob/master/images/Classic_Three-Layer_Architecture.png" />

#### Modern Four-Layer Architecture
   <img src="https://github.com/matsennin/domain-driven-design/blob/master/images/Modern_Four-Layer_Architecture.png" />
   
