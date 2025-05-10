# 2 SEMESTRE 2022/2
## PRO4JOBS
Cliente: PRO4TECH
PRO4Jobs é uma aplicação Desktop com o objetivo de gerenciar vagas de emprego, otimizar o trabalho das pessoas do setor de Recursos Humanos O Candidato poderá vizualizar e se candidatar as vagas de emprego que o RH disponibilizará, enquanto o Rh pode analisar e filtrar os perfis dos candidatos as vagas e decidir se devem aporva-los ou não.

### Tecnologias e Bibliotecas Utilizadas
- Java: Linguagem de programação back-end;
- Java Swing: Conjunto de bibliotecas da linguagem Java, utilizado para construção de interfaces gráficas de usuário (GUIs);
- MySQL: Sistema Gerenciador de Banco de Dados utilizado para armazenar os dados provenientes da aplicação desenvolvida.

## Contribuições Pessoais
### Criação de Mockups e prototipação do projeto
Num primeiro momento do projeto foi necessario planejá-lo então atuei desenvolvendo as telas atravaes do aplicativo web Figma, prototipando detalehs como campos de inserção e o design das telas, pensando sempre na experiencia do usuário e em criar jum sistema intuitivo.
<details>
<summary><h4>Mais Detalhes</h4></summary>
<p>Para a criação das telas foi pensado e deixar o sistema facil de ser utilizado e tmabem com design simples para que evitasse poluição visual e também as telas brancas padrão do java,
a preferência tmabem era de ceerta forma estilizar as telas do Java Swing pois o mesmo não da opção apra customização ou estilização das telas.</p>
<p>Alguns exemplos</p>
  
  <p><h5>Tela de Login</h5></p>
  
  ![Image](https://github.com/user-attachments/assets/961f159c-eb2b-433e-b22f-a79003879e20)

  <p><h5>Tela de Cadastro</h5></p>

  ![Image](https://github.com/user-attachments/assets/3b0ce68a-ab4f-42dc-b434-d2e40b682829)

</details>

### Cadastro de candidatos
<p>Uma das principais partes do projeto, pois é necessário que o usuário consiga acessar a plataforma e para utiliza-la é necessário a inserção dos dados tais como nome, email, senha, telefone, CPF, pretensão salarial, cargo de interesse e currículo uma breve descrição de experiencias profissionais</p>

<details>
<summary><h4>Mais Detalhes</h4></summary>

Após isso, uma nova classe em Java foi criada para inserir registros dentro do banco de dados. Dentro desta classe, foi implementado um método específico que chama outro método de outra classe para estabelecer a conexão com o banco de dados. Depois, um comando SQL foi escrito para cadastrar as vagas de emprego no banco. As informações sobre o usuário são coletadas por meio de uma interface gráfica (GUI). Esta interface coleta os dados e os passa para a classe que armazena temporariamente essas informações.

A classe que contém o método de cadastro de vagas no banco então coleta os dados do DTO e os incorpora ao comando SQL. Finalmente, este método executa o comando no banco de dados, criando o novo usuário. Este processo garante que as vagas sejam inseridas corretamente e de maneira eficiente no sistema, facilitando o gerenciamento e a manutenção das informações sobre as oportunidades de emprego disponíveis.  </p>
</details>
