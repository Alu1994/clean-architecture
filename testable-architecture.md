# Testable Architecture

## Por que testes são dificeis e ineficientes?

  - Não há tempo, por que temos uma sprint gigante pra entregar e testes não tem o mesmo valor.
  - Não é meu trabalho, pois existem QAs/POs para fazer esse trabalho.
  - É muito difícil devido à arquitetura do projeto.

Normalmente são essas e mais algumas outras desculpas que utilizamos para não fazer os testes necessários para os nossos projetos.

Para nos ajudar, uma das funções do Clean Architecture é justamente facilitar os testes, em conjunto ao TDD os dois se potencializam para que tenhamos uma arquitetura bem desenvolvida e facilmente testavel.

## Test-Driven Development

TDD é uma pratica de desenvolvimento onde criamos primeiramente um teste que vai falhar, antes de escrevermos qualquer código de produção e usamos esse teste para direcionar o design da arquitetura do projeto.

  - O TDD é divido em 3 passos (RED, GREEN, REFACTOR):
    - RED - Criamos o teste que irá falhar, pois ainda não existe nenhum código de produção.
    - GREEN - Criamos o código de produção para que este teste passe.
    - REFACTOR - Refatoramos tanto o código de testes como o código de produção.

Nós devemos repetir esses 3 passos, para todos os métodos e classes até que a feature esteja completada.

<p align="center">
  <img src="https://github.com/matsennin/clean-architecture/blob/master/images/Test_Driven_Development.png" />
</p>

- Com isso, nós estamos criando testes unitários que fazem sentido para cada cenário que deve ser testado do nosso projeto.
- Se seguirmos TDD, todas as classes do nosso projeto seram testaveis, ja que os testes estaram guiando o design do projeto.
- TDD facilita a manutenção do nosso código, pois se escrevermos código para que seja possível testar, ele por default será menos acoplado e mais coeso.
- Ele também diminui o medo, medo que se fizermos mudanças em nosso código teremos erros e muita dor de cabeça. Se diminuirmos o medo de alteração no nosso código, iremos aceitar mudanças mais abertamente e manteremos nossa arquitetura limpa.

## Test Automation Pyramid

- Existem varios tipos de testes no ambiente de desenvolvimento.
  - Alguns testes se baseiam em **o que** eles estão testando:
    - Unit Tests
    - Integration Tests
    - Component Tests
    - Service Tests
    - Coded UI Tests
  - Outros testes se baseiam no **por que** eles estão testando:
    - Functional Tests
    - Acceptance Tests
    - Smoke Tests
    - Exploratory Tests
  - Outros testes se baseiam em **como** eles estão testando:
    - Automated Tests
    - Semi-automated Tests
    - Manual Tests

A piramide automatizada de testes descrita no livro _**Succeeding with agile**_ de Mike Cohn, identifica 4 tipos de testes.
  - Na base da piramide temos os Unit Tests, que são testes automatizados que verificam a funcionalidade de uma unidade de código isolada.
  - No meio temos os Service Tests, que são testes automatizados que verificam a funcionalidade de um conjunto de classes e métodos que representam um serviço/funcionalidade disponibilizada ao usuário.
  - No topo temos os Coded UI Tests, que são testes automatizados que verificam a funcionalidade da aplicação como um todo, desde um input do usuário até a base de dados.
  - Por fim temos os Manual Tests, que são testes executados por humanos que verificam a funcionalidade da aplicação como um todo também.
  
<p align="center">
  <img src="https://github.com/matsennin/clean-architecture/blob/master/images/Test_Automation_Pyramid.png" />
</p>

A piramide de testes consegue captar a essencia de que, cada teste que escolhemos é mais caro dependendo do quanto subimos a piramide.

Por consequencia quanto mais descemos a piramide, é possível ter mais testes de forma mais barata. 
- Por exemplo os testes unitários são simples e rápidos de fazer, rodam extremamente rapido, raramente falham devidos a falsos positivos, e são bem baratos de serem mantidos. Portanto existem menos custos do que outros testes mais acima na piramide.
- Por outro lado Coded UI Tests são dificeis e tomam muito mais tempo para serem criados. Eles também demoram mais tempo para executar, eles são mais frágeis, relativamente não confiavéis e mais dificeis de se manter. Portanto existem mais custos do que outros testes mais abaixo na piramide.

Com isso devemos focar nossos esforços no que trás um bom retorno com a medida exata de esforço. Tendo muitos testes unitários, alguns testes de Serviço, poucos de UI e menos ainda manuais e repetitivos. Na teoria isso nos dá o melhor cenário para nossos esforços na criação de testes.

## Acceptance Tests

Acceptance Tests são testes feitos para verificar a funcionalidade do projeto na linguagem de negócio.
É possível fazer de forma manual ou através de Coded UI Tests.
No entanto usar testes manuais ou Coded UI podem ser problematicos devido ao que foi pontuado acima.

Para fazer isso de forma menos custosa podemos implementar uma camada intermediária de Testes de Aceite Automatizados. Isso só é possível implementando Clean Architecture, que nos obriga a deixar nosso domínio e regas de negócio da nossa camada de _Application_ isolados das necessidades tecnicas do projeto.
- Para isso nós devemos primeiro eliminar a camada de Usuário (API/User Interface), fazemos isso chamando diretamente nossos _Commands & Queries_ da nossa camada de _Application_(Mais um motivo de ser importante removermos qualquer regra de negócio da _Presentation Layer_).

- Depois removemos a nossa base de dados dos testes de aceite, fazemos isso mockando nossa base de dados utilizando (por exemplo) _In-Memory Database_.

- Depois nós removemos qualquer dependencia externa ou do _Sistema Operacional_ da nossa camada de _Infrastructure_, fazemos isso mockando essas dependencias.

- O mesmo é feito para a camada de _Cross Cutting Concerns_.

<p align="center">
  <img src="https://github.com/matsennin/clean-architecture/blob/master/images/Example_Acceptance_Tests.png" />
</p>

- A implementação deve ser feita na linguagem de negócio e **não deve focar na maneira como ele foi implementado**, deve focar no essencial para o fluxo de negócio.
- Com isso diminuimos a quantidade de Coded UI Tests na nossa aplicação.
- Assim podemos usar Smoke Tests, que são um número pequeno de testes que verificam a aplicação como um todo, e validam se a aplicação executa e nada mais, quando todas as peças são unidas e utilizadas em tempo de execução.
- Também diminuimos a quantidade de testes manuais, assim liberando nossos QAs/POs para fazer um trabalho muito mais importante e gratificante. Por exemplo fazendo testes exploratórios, garantindo a melhor experiencia para nossos usuários finais.


## Prós :) & :( Contras em utilizar Testable Architecture
### Prós:
  - Aplicando esses conceitos nós facilitamos a testabilidade do nosso código, também facilitando sua manutenção. (Queremos que todos façam testes e pratiquem TDD {se possivel for rs}).
  - Criar uma arquitetura testavel, melhora a arquitetura em si.
  - Eliminamos o medo.    

### Contras:
  - É mais caro no inicio. Pode não valer a pena se o projeto for (por exemplo) um console application simples com 0 ou pouquissima regra de negócio que pode ser que rode vez ou outra.
  - TDD exige prática e disciplina, e demora um tempo consideravel para você ficar eficiente e que você se policie para não voltar aos hábitos antigos de desenvolvimento.
  - Normalmente exige que o time todo esteja comprado com essa ideia. Se o time como um todo não estiver comprado, uma hora ou outra o Teste + o Código Testavel se tornaram obsoletos.
