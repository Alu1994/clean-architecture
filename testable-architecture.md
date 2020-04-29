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
  <img src="https://github.com/matsennin/domain-driven-design/blob/master/images/Test_Driven_Development.png" />
</p>

- Com isso, nós estamos criando testes unitários que fazem sentido para cada cenário que deve ser testado do nosso projeto.
- Se seguirmos TDD, todas as classes do nosso projeto seram testaveis, ja que os testes estaram guiando o design do projeto.
- TDD facilita a manutenção do nosso código, pois se escrevermos código para que seja possível testar, ele por default será menos acoplado e mais coeso.
- Ele também diminui o medo, medo que se fizermos mudanças em nosso código teremos erros e muita dor de cabeça. Se diminuirmos o medo de alteração no nosso código, iremos aceitar mudanças mais abertamente e manteremos nossa arquitetura limpa.

## Test Automation Pyramid

- Existem varios tipos de testes no ambiente de desenvolvimento.
  - Alguns testes se baseiam em **o que** eles estão testando, como:
    - Unit Tests
    - Integration Tests
    - Component Tests
    - Service Tests
    - Coded UI Tests
  - Outros testes se baseiam no **por que** eles estão testando, como:
    - Functional Tests
    - Acceptance Tests
    - Smoke Tests
    - Exploratory Tests

## :) Prós & :( Contras em utilizar Testable Architecture

