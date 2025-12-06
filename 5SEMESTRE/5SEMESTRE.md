# 5 Semestre 2025/1
## VISION

Repositório: <a href="https://github.com/new-ge/VISION">GIT</a>


### Problema
<p>O desenvolvimento do projeto se trata de uma solução sob medida para a empresa Youtan, localizada no parque tecnológico de São José dos Campos, a youtan lida com desenvolvimento de softwares desde 2002, a Youtan atua com metodologias ágeis e tecnologias modernas para transformar ideias em soluções digitais para Web, Desktop e Mobile. Além disso, oferece o SIGI, seu próprio ERP em modelo SaaS, voltado para empresas B2B de pequeno e médio porte.</p> 
<p>A proposta do VISION, é ser uma ferramenta de visualização de indicadores integrada à plataforma Taiga, com foco em tornar a gestão de projetos mais eficiente, visual e transparente. A Vision permite que usuários acompanhem o progresso de tarefas através de dados como tempo médio de finalização, distribuição de responsabilidades, uso de etiquetas e mais.</p>

### Tecnologias Utilizadas
- Vue.js: Framework JavaScript voltado para a criação de interfaces de usuário dinâmicas e responsivas.

- Spring Security: Módulo do ecossistema Spring que trata da segurança das aplicações, oferecendo recursos de autenticação e controle de acesso.

- Hibernate: Ferramenta ORM que facilita a comunicação entre aplicações Java e bancos de dados relacionais.

- JavaScript: Linguagem de programação utilizada para adicionar interatividade a páginas web e aplicações no navegador.

- CSS (Cascading Style Sheets): Linguagem de estilo responsável pela aparência visual das páginas web.

- Java 17: Versão estável e com suporte estendido da linguagem Java, trazendo melhorias de performance e novas funcionalidades.

- Figma: Plataforma usada para desenhar interfaces e criar protótipos visuais de aplicações.

- Oracle: Sistema de banco de dados relacional usado para armazenar e consultar dados de forma estruturada.

- HTML (HyperText Markup Language): Linguagem de marcação responsável por estruturar o conteúdo das páginas web.

- Pinia: Biblioteca de gerenciamento de estado utilizada em aplicações com Vue.js.

- Spring Boot: Framework Java que facilita o desenvolvimento de aplicações e APIs com configuração simplificada e integração rápida de componentes.

- Spring Boot Starter Test: para a realização de testes unitários no bakcend da aplicação

- Sonarqube: para monitorar a cobertura dos testes

### Contribuições Pessoais

Durante o 5 semestre pela primeira vez atuei como Product Owner de um projeto de API, tive como contribuições partes mais administrativas porém ainda trabalhei no código em determinados pontos do projeto

#### Backlog

Fui responsável pela criação do backlog do projeto e adequação de acordo com os requisitos funcionais e não funcionais solicitados 

<summary>Mais Detalhes</summary>
<details>
    
| **Rank** | **Épico** | **User Storie** | **Estimativa** | **Requisito do Parceiro** | **Status**|
|---------|-----------|-----------------|---------------|--------------------------|---------------|
| 1 | Dashboard de Indicadores | Como um operador, quero visualizar a quantidade de cards por etiqueta, para que eu possa entender a distribuição das minhas tarefas. | 1 | RF1, RF2 | ✅ | 
| 2 | Dashboard de Indicadores | Como um operador, quero visualizar a quantidade de cards criados por período, para que eu possa acompanhar a criação das minhas tarefas. | 1 | RF1, RF3, RFN2, RFN3 | ✅ | 
| 3 | Dashboard de Indicadores | Como um operador, quero visualizar a quantidade de cards finalizados por período para que eu possa acompanhar a entrega de tarefas ao longo do tempo. | 1 | RF1, RF4, RFN2 | ✅ | 
| 4 | Dashboard de Indicadores | Como um operador, quero visualizar a quantidade de cards por status, para que eu possa entender o andamento das tarefas. | 1 | RF1, RF5 | ✅ | 
| 5 | Dashboard de Indicadores | Como um operador, quero visualizar o tempo médio de execução de cards, para que eu possa analisar a minha eficiência no processo de desenvolvimento. | 2 | RF1, RF6, RFN2 | 🔧 |
| 6 | Dashboard de Indicadores | Como um operador, quero visualizar os retrabalhos, para que eu possa acompanhar os meus cards que retornaram para o desenvolvimento devido a bugs. | 2 | RF1, RF8, RFN2 | ✅ |
| 7 | Dashboard de Indicadores | Como um admin, quero visualizar a quantidade de cards por status, para que eu possa entender o andamento das tarefas. | 2 | RF1, RF5 | ✅ | 
| 8 | Dashboard de Indicadores | Como um admin, quero visualizar o tempo médio de execução de cards, para que eu possa analisar a eficiência no processo de desenvolvimento. | 2 | RF1, RF6 | ✅ |
| 9 | Dashboard de Indicadores | Como um admin, quero visualizar os cards por colaborador, para que eu possa analisar a distribuição de tarefas. | 2 | RF1, RF7 | ✅ |
| 10 | Dashboard de Indicadores | Como um admin, quero visualizar os retrabalhos, para que eu possa acompanhar os cards que retornaram para o desenvolvimento devido a bugs. | 2 | RF1, RF8 | ✅ | 
| 11 | Dashboard de Indicadores | Como gestor, quero visualizar indicadores de meu time, para que eu possa avaliar a performance dos colaboradores e do time como um todo. | 2 | RF1, RNF2 | 🔧 |  
| 12 | Dashboard de Indicadores | Como gestor, quero visualizar os retrabalhos relacionados ao meu projeto, para que eu possa monitorar a qualidade do trabalho e identificar áreas que precisam de melhorias. | 2 | RF1, RF8 | ✅ | 
| 19 | Autenticação | Como um usuário, eu desejo que o sistema realize a autenticação do usuário, para que apenas usuários autorizados possam acessar as funcionalidades do sistema. | 2 | RF9, RFN1 | ✅ |
| 13 | Níveis de Acesso | Como admin, quero configurar os níveis de acesso para diferentes tipos de usuários (Operador, Gestor, Admin), para garantir que as permissões sejam corretamente atribuídas. | 2 | RF9, RFN1, RFN4 | ✅ | 
| 14 | Gestão de Acessos | Como admin, quero garantir que apenas um único gestor tenha acesso aos projetos do seu time, para evitar conflitos de acesso entre diferentes gestores. | 3 | RF9, RFN1, RFN4 | 🔧 |
| 15 | Dashboard de Indicadores | Como um admin, quero visualizar indicadores relacionados a todos os cards de todos os times, para que eu possa acompanhar a carga de trabalho e a distribuição das tarefas. | 3 | RF01, RFN01, RFN02, RFN03 | 🔧 |
| 16 | Dashboard de Indicadores | Como um admin, quero visualizar a quantidade de cards por etiqueta, para que eu possa entender a distribuição de tarefas. | 3 | RF1, RF2 | 🔧 | 
| 17 | Dashboard de Indicadores | Como um admin, quero visualizar a quantidade de cards criados por período, para que eu possa acompanhar a criação das tarefas ao longo do tempo. | 3 | RF1, RF3 | 🔧 |
| 18 | Dashboard de Indicadores | Como um admin, quero visualizar a quantidade de cards finalizados por período, para que eu possa acompanhar a entrega das tarefas ao longo do tempo. | 3 | RF1, RF4 | 🔧 | 

</details>

#### Protótipos de telas

Num primeiro momento do projeto foi necessario planejá-lo então atuei desenvolvendo as telas atravaes do aplicativo web Figma, prototipando detalehs como campos de inserção e o design das telas, pensando sempre na experiencia do usuário e em criar jum sistema intuitivo.

<summary>Mais detalhes</summary> 
<details>

Alguns protótipos que foram utilizados na versão final do projeto

<p><h5>Tela de Login</h5></p>

![image](https://github.com/user-attachments/assets/12dab46d-2283-42ed-8b58-ca82036c9936)

<p><h5>Tela principal da aplicação</h5></p>

![image](https://github.com/user-attachments/assets/4df00210-4604-4909-8785-3c4a1cbec699)


</details>

#### Devops: Testes Unitários

Como parte da matéria de Devops fui responsável pela parte de documentação e implementação dos testes unitários no projeto após análise criteriosa foram definidos os principais pontos necessários para qeu so testes fossem implementados como bibiliotecas a serem utilizadas e como deveria ser a estrutura dos mesmos e como deveriam ser apresentados no códigos

<summary></summary>
<details>
<p><h5>Exemplo de Teste Implementado no Backend</h5></p>
    ´´´ java

        @Operation(summary = "Processa o login com base no username e a senha.", description = "Processa o username e a senha e verifica se há um login válido para entrar na aplicação")
        @ApiResponses(value = {
                @ApiResponse(responseCode = "200", description = "Usuário existe."),
                @ApiResponse(responseCode = "500", description = "Não há um usuário existente.")
        })
    ´´´

<p><h5>Exemplo de Teste Implementado no Frontend</h5></p>
    ´´´
        it('should create graphics instances correctly', () => {
            const chartJs = require('chart.js')                     // Arrange
            const createChart = () => new chartJs.Chart()           // Act
            expect(createChart).not.toThrow()                       // Assert
        })

    ´´´
</details>

### Hard Skill e Soft Skills

#### Hard Skills

<details>

| Habilidade | Nota | Classificação |
| :-----: | :-----: | :-----: | 
| Spring Boot | ★★★★★ | Sei fazer com autonomia |
| Oracle | ★★★★☆ | Entendi |


</details>


#### Soft Skills
<details>

| Habilidade | Classificação |
| :-----: | :-----: |
| Trabalho em Equipe | Durante o desenvolvimento do gerenciamento de usuários e da autenticação de usuários, colaborei ativamente com outros membros da equipe para garantir que o sistema estivesse funcionando de forma coesa, implementando soluções técnicas de forma eficaz e dentro dos requisitos do projeto. |
| Gerenciamento de Tempo | Ao entrar no projeto tive que readequar a minha rotina para encontrar um alinhamento entre trabalho e faculdade e semrpe encontrando horários bons para desenvolver os códigos e funções que a mim eram indicados. |
| Liderança | Durante o desenvlvimento aprendi como liderar e como tomar decisões importantes para o grupo e o futuro da aplicação |
| Metodologia Scrum	| Pude ter mais contato com a metodologia scrum a fundo de uma posição naqual nunca tinha estado antes trazendo melhor entendimento dos papéis de cada um no projeto e como auxiliar em determinadas dúvidas |

</details>

[Página Inicial](https://github.com/wunderlich-15/PortfolioTG/tree/main)
