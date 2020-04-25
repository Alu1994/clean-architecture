# Functional Organization

- Organização funcional ou Coesão Funcional, nada mais é do que você organizar o seu projeto por assunto, ao invés de scaffoldings ou convenções de frameworks (Coesão por Categoria utilizando MVC por exemplo).
- Obs: E também ele segue a Screaming Architecture, que é justamente organizar seu projeto pelo assunto pelo qual ele está apelando.
  - Ex: Assistencia Técnica
    - Produtos
    - Ordem de Serviço
    - Clientes

<p align="center">
  <img src="https://github.com/matsennin/domain-driven-design/blob/master/images/Framework_Convention_x_Functional_Organization.png" />
</p>

- Afinal é muito mais simples entender a intenção/real motivo do projeto quando organizamos por assunto.


## Prós e Contras em utilizar Functional Organization
  - Prós:
    - Agrupar os itens quando eles fazem sentido juntos. (Garfos, Facas e Colheres) x (Tridente, Garfo e Garfo para colher folhas)
    - Facilita a navegação na estrutura do projeto.
    - Nos livra de ficar reféns da estrutura do framework que utilizamos em nossos projetos.
  - Contras:
    - Se você não utilizar a estrutura padrão dos frameworks (Coesão por Categoria), normalmente o mesmo lhe forçará a indicar onde classes e arquivos forão definidos.
    - Coesão por Categoria no começo é muito mais simples de implementar, pois geralmente só é necessário seguir a estrutura do scaffolding. Mas ao longo do desenvolvimento a Coesão por Funcionalidade faz mais sentido.
