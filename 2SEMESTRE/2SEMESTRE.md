# 2 SEMESTRE 2022/2
## PRO4JOBS
Cliente: PRO4TECH

Repositório: <a href="https://github.com/lucasetdasilva/GrupoCodados">GIT</a>

PRO4Jobs é uma aplicação Desktop com o objetivo de gerenciar vagas de emprego, otimizar o trabalho das pessoas do setor de Recursos Humanos O Candidato poderá vizualizar e se candidatar as vagas de emprego que o RH disponibilizará, enquanto o Rh pode analisar e filtrar os perfis dos candidatos as vagas e decidir se devem aporva-los ou não.

### Tecnologias e Bibliotecas Utilizadas
- Java: Linguagem de programação back-end;
- Java Swing: Conjunto de bibliotecas da linguagem Java, utilizado para construção de interfaces gráficas de usuário (GUIs);
- MySQL: Sistema Gerenciador de Banco de Dados utilizado para armazenar os dados provenientes da aplicação desenvolvida.

## Contribuições Pessoais
### Criação de Mockups e prototipação do projeto
Num primeiro momento do projeto foi necessario planejá-lo então atuei desenvolvendo as telas atravaes do aplicativo web Figma, prototipando detalhes como campos de inserção e o design das telas, pensando sempre na experiência do usuário e em criar um sistema intuitivo.
<details>
<summary><h4>Mais Detalhes</h4></summary>
<p>Para a criação das telas foi pensado e deixar o sistema facil de ser utilizado e também com design simples para que evitasse poluição visual e também as telas brancas padrão do java,
a preferência também era de certa forma estilizar as telas do Java Swing pois o mesmo da muito poucas opções para customização ou estilização das telas.</p>
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

Após isso, uma nova classe em Java foi criada para inserir registros dentro do banco de dados. Dentro desta classe, foi implementado um método específico que chama outro método de outra classe para estabelecer a conexão com o banco de dados. Depois, um comando SQL foi escrito para cadastrar os candidatos no banco. As informações sobre o usuário são coletadas por meio de uma interface gráfica (GUI). Esta interface coleta os dados e os passa para a classe que armazena temporariamente essas informações.

A classe que contém o método de cadastro de vagas no banco então coleta os dados do DTO e os incorpora ao comando SQL. Finalmente, este método executa o comando no banco de dados, criando o novo usuário. Este processo garante que os candidatos sejam inseridos corretamente e de maneira eficiente no sistema, facilitando o gerenciamento e a manutenção das informações pessoais com segurança e eficiência.  </p>

```

  public void cadastrarCandidato(Candidato objcandidato) {

        String sql = "insert into candidato (cpf, nome_completo, data_nascimento, email, telefone, endereco, pretencao_salarial, senha) values (?,?,?,?,?,?,?,MD5(?))";
        conn = new ConexaoDAO().conectaBD();

        try {
            
            pstm = conn.prepareStatement(sql);
            
            pstm.setString(1, objcandidato.getCPF());
            pstm.setString(2,objcandidato.getNome_Completo());
            pstm.setString(3, objcandidato.getData_Nascimento());
            pstm.setString(4, objcandidato.getEmail());
            pstm.setLong(5, objcandidato.getTelefone());
            pstm.setString(6, objcandidato.getEndereco());
            pstm.setDouble(7, objcandidato.getSalario());
            pstm.setString(8, objcandidato.getSenha());
            
            pstm.execute();
            pstm.close();
            
            JOptionPane.showMessageDialog(null, "Os dados foram salvos !");

        } catch (SQLException erro) {
            JOptionPane.showMessageDialog(null, "CandidatoDAO" + erro);
        }

    }
```

</details>

### Exlusão de vagas do Sistema
<p>A exclusão das vagas do banco de dados também é um script essecial do gerenciamento do sistema já que faz parte do CRUD de uma das principais vertentes do projeto como um todo</p>

<details>
<summary><h4>Mais Detalhes</h4></summary>
<p>Este método Java realiza a exclusão de vagas em um banco de dados. Ele recebe um objeto Vaga como parâmetro, estabelece conexão com o banco usando a classe ConexaoDAO e executa um comando SQL DELETE com prepared statements, utilizando o ID da vaga obtido do objeto. O sistema mostra uma mensagem de sucesso após a exclusão ou trata possíveis erros com mensagens adequadas.

A implementação segue boas práticas de programação, como separação de responsabilidades (DAO e DTO), prevenção contra injeção SQL (usando prepared statements) e tratamento de exceções. Isso garante que a exclusão seja segura e eficiente, mantendo a integridade dos dados no banco.  </p>

```
       public void excluirVaga(Vaga objvagadto){
            String sql = "delete from vaga where id_vaga = ?";
            conn = new ConexaoDAO().conectaBD();
            
            try {
                
                pstm = conn.prepareStatement(sql);
                
                pstm.setInt(1, objvagadto.getId_vaga());
                
                pstm.execute();
                pstm.close();
                
                JOptionPane.showMessageDialog(null, "Vaga Excluida");
                
                
            } catch (SQLException erro) {
                JOptionPane.showMessageDialog(null,"VagaDAO: Excluir" + erro);
            
            }
```

</details>

#### Hard Skills


<details>

| Habilidade | Nota | Classificação |
| :-----: | :-----: | :-----: | 
| Java | ★★★☆☆ | Sei fazer com ajuda |
| Figma | ★★★★☆ | Entendi |
| Git |	★★★☆☆ | Sei fazer com ajuda |


</details>

#### Soft Skills


<details>

| Habilidade | Classificação |
| :-----: | :-----: |
| Comunicação | Utilizei a comunicação constante ao longo do projeto para organizar o backlog, definir tarefas e garantir que as atualizações e feedbacks fossem compartilhados de maneira clara e eficiente. |
| Gestão de Tempo | Aprendi a lidar com diferentes cargas de trabalho ao logno do projeto conciliando-as com a vida pessoal e profisssional fora da faculdade. |
| Proatividade	| Tive uma maior noção do significado correto de proatividade onde aprendi a como me portar corretamente num modelo de projeto orientado a metodologia ágil Scrum e como cada task impacta no desenvolvimento. |

</details>


[Página Inicial](https://github.com/wunderlich-15/PortfolioTG/tree/main)
