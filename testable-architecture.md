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

## Test Automation Pyramid

## :) Prós & :( Contras em utilizar Testable Architecture

