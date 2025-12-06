# 4 Semestre 2024/2
## LocalTracker

Repositório: <a href="https://github.com/TechHorizonBR/API_5SEM">GIT</a>

### Problema
<p>O desenvolvimento do projeto contou com a colaboração da ITO1, uma empresa com expertise em dados e Internet das Coisas (IoT). 
A ITO1 atua coletando dados de diversos ambientes por meio de dispositivos IoT, utilizando essas informações para criar soluções inovadoras, com destaque para a geolocalização de pessoas e objetos. d
Seu objetivo principal é administrar, de forma eficaz, grandes volumes de dados provenientes desses dispositivos, oferecendo soluções escaláveis e com alta disponibilidade para o registro e a consulta da localização de ativos, dispositivos e outros elementos em bancos de dados relacionais.</p> 
<p>O maior desafio envolvido foi lidar com a quantidade massiva de dados gerados pelos dispositivos IoT, especialmente os relacionados à geolocalização, e garantir um armazenamento eficiente e que permitisse expansão conforme a demanda. 
Além disso, era necessário assegurar respostas rápidas às consultas e manter os dados sempre disponíveis para diversos usuários e dispositivos simultaneamente. Outro ponto crítico era preservar a integridade e a rastreabilidade das informações coletadas.</p>

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

### Contribuições Pessoais

#### Deletar Usuários do sistema
Fiquei responsável pelo elndpoint que deletar usuários do sistema afim de tornar o proejto 100% funcional com o Crud Relacional Impecável tendo todas suas principais funções implementadas
<summary>Mais detalhes</details>
<details>

``` java
    @Operation(
        summary = "Delete System user.",
        description = "Endpoint responsible for deleting a User. Just Admin has access to this endpoint.",
        responses = {
            @ApiResponse(
                    responseCode = "200",
                    description = "User has been deleted.",
                    content = @Content(mediaType = "application/json",
                    schema = @Schema(implementation = UserSysResponseDTO.class))) 
            }
    )
    @PreAuthorize("hasAnyRole('ADMIN')")
    @DeleteMapping("/delete/{username}")
    public ResponseEntity<Void> deleteUser(@PathVariable String username) {
        userSysServiceImpl.deleteByUsername(username);
        return ResponseEntity.noContent().build();
}
```
Este trecho de código define um endpoint REST para deletar um usuário do sistema, acessível apenas por administradores. Ele utiliza anotações do Swagger para documentar a operação, informando que o endpoint remove um usuário com base no nome de usuário fornecido na URL. A anotação `@PreAuthorize` restringe o acesso a perfis com o papel de ADMIN. Quando chamado com sucesso, o método invoca o serviço `deleteByUsername` e retorna uma resposta HTTP 204 (sem conteúdo), indicando que a exclusão foi concluída sem erros.
</details>

#### Domcumentação dos Endpoints no Swagger
Fiquei também responsável pela documentação dos endpoints do projeto no Swgger afim de de tornar o projeto mais organizado e com o código limpo para que pudesse auxiliar ao máximo todo e qualquer desenvolvedor a saber como funciona cada endpoint do projeto
<summary>Mais Detalhes</summary>
<details>

```java
@Operation(
        summary = "Get all Locals.",
        description = "Endpoint responsible for retrieving a list of all locals.",
        responses = {
            @ApiResponse(
                    responseCode = "200",
                    description = "Getting has been executed successfully.",
                    content = @Content(mediaType = "application/json", schema = @Schema(
                        implementation = Local.class))
                    )
            }
    )
```
Este código documenta um endpoint que retorna uma lista de todos os locais cadastrados. Utiliza anotações do Swagger para descrever a operação e o tipo de resposta esperada. O código informa que, em caso de sucesso, será retornado um status HTTP 200 com os dados no formato JSON. A resposta está modelada com base na classe `Local`.
</details>

#### Criação de rota no mapa
Foi necessária tambem a implementação de uma rota rastreável para cada coordenada no mapa então fui o responsável pela implementação deste código no frontendo do projeto.
<summary>Mais detalhes</summary>
<details>

``` javascript
        const routeId = `route${elementData.userCode}`;
        map.value?.addSource(routeId, {
            type: "geojson",
            data: {
                type: "Feature",
                properties: {},
                geometry: {
                    type: "LineString",
                    coordinates: formattedCoords,
                },
            },
        });

        map.value?.addLayer({
            id: routeId,
            type: "line",
            source: routeId,
            layout: {
                "line-join": "round",
                "line-cap": "round",
            },
            paint: {
                "line-color": "#0f53ff",
                "line-width": 4,
            },
        });

        formattedCoords = null;
        allCoords.value = [];

        actualUser.value++;
        changeLoading();
    }
}
```
Este código adiciona uma rota em formato de linha ao mapa usando a biblioteca Mapbox. Ele realiza as seguintes ações:

Cria um ID único para a rota com base no código do usuário (userCode).

Adiciona uma fonte GeoJSON ao mapa, contendo uma LineString formada pelas coordenadas presentes em formattedCoords.

Adiciona uma camada de linha ao mapa, utilizando essa fonte. A linha é estilizada com cor azul (#0f53ff) e largura de 4 pixels, com cantos e junções arredondados.

Limpa os dados temporários, resetando as coordenadas (formattedCoords e allCoords.value) e avança para o próximo usuário (actualUser.value++), além de acionar a função changeLoading() para atualizar o estado da interface.
</details>

#### Hard Skills

<details>

| Habilidade | Nota | Classificação |
| :-----: | :-----: | :-----: | 
| Spring Boot | ★★★★★ | Sei fazer com autonomia |
| Oracle | ★★★☆☆ | Sei fazer com ajuda |


</details>

#### Soft Skills


<details>

| Habilidade | Classificação |
| :-----: | :-----: |
| Trabalho em Equipe | Durante o desenvolvimento do gerenciamento de usuários e da autenticação de usuários, colaborei ativamente com outros membros da equipe para garantir que o sistema estivesse funcionando de forma coesa, implementando soluções técnicas de forma eficaz e dentro dos requisitos do projeto. |
| Gerenciamento de Tempo | Ao entrar no projeto tive que readequar a minha rotina para encontrar um alinhamento entre trabalho e faculdade e sempre encontrando horários bons para desenvolver os códigos e funções que a mim eram indicados. |

</details>

[Página Inicial](https://github.com/wunderlich-15/PortfolioTG/tree/main)
