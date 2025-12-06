# 6 Semestre 2025/2
## LuminIA - Pro4Tech

Repositório: <a href="https://github.com/new-ge/LuminIA">GIT</a>

### Problema
<p> A estrutura atual do banco de dados de suporte da Empresa Pro4Tech já não atende às demandas da operação: apresenta riscos de não conformidade legal com a Lei Geral de Proteção de Dados (LGPD), dificulta processos de auditoria e não favorece análises históricas ou preditivas. Como resultado, os relatórios gerados são limitados e repetitivos, sem entregar uma visão abrangente para a tomada de decisões.
<p> A proposta de modernização vem justamente para superar essas falhas, oferecendo mais segurança no tratamento das informações, maior transparência no acompanhamento das atividades e dashboards que permitam a cada nível da equipe – de analistas a gestores e responsáveis estratégicos – enxergar com clareza os dados necessários para trabalhar com mais eficácia.

### Tecnologias Utilizadas
  - Python e FastAPI: Linguagem principal utilizada no backend da aplicação desde a conexão com o banco ate requisições endpoints e para testar a API
  - MongoDB: Banco de dados não relacional utilizado no armazenamento de dados do projeto
  - Github e Git: Para o versionamento do código
  - Jira: Ferramenta de gestãod o projeto
  - Postman: Ferramenta de testes dos endpoints
  - Prophet e Flair: Para a criação dos códigos de prediçãod e sentimento FAQ e demanda de chamados
  - Vue.js, HTML e CSS: Utilizado na criação e estilização do frontend do projeto

### Contribuições Pessoais 
No sexto semestre contribui como desenvolvedor no projeto e atuei diretamente no desenvolvimento do backend, principalmente em algumas funções principais como o CRUD do sistema

#### Criação de usuários no sistema
<details>
<summary>Código em Python para a criação de usuários </summary>

<P>Repository</P>

```python
from bson import ObjectId
from datetime import datetime, timezone, timedelta
from api_6sem_back_end.db.db_configuration import db_data

def serialize_user(user):
    if not user:
        return None
    user["_id"] = str(user["_id"])
    return user

class UserRepository:

    @staticmethod
    def get_last_agent_id():
        last_user = db_data["users"].find_one(sort=[("agent_id", -1)])
        return last_user["agent_id"] if last_user else 0

    @staticmethod
    def create_user(user_data: dict):
        now = datetime.now(timezone(timedelta(hours=-3))).isoformat(timespec='seconds')
        user_data["created_at"] = now
        user_data["modified_at"] = now
        user_data["firstaccess"] = True

        last_id = UserRepository.get_last_agent_id()
        user_data["agent_id"] = last_id + 1

        result = db_data["users"].insert_one(user_data)
        user_data["_id"] = result.inserted_id
        return serialize_user(user_data)
```

<P>Service</P>

```python
from api_6sem_back_end.repositories.user_repository import UserRepository


class UserService:

    @staticmethod
    def create_user(data: dict):
        email = data.get("email")
        password = data.get("password")

        user_data = {
            "email": email,
            "isActive": True,
            "login": {
                "username": email,
                "password": password
            },
            "name": data.get("name"),
            "role": data.get("role"),
            "department": data.get("department", "-")
        }

        return UserRepository.create_user(user_data)
```

<P>Router</P>

```python
from fastapi import APIRouter, HTTPException
from api_6sem_back_end.services.user_service import UserService

router = APIRouter(prefix="/users", tags=["Users"])


@router.post("/create")
def create_user(user: dict):
    try:
        new_user = UserService.create_user(user)
        return {"message": "Usuário criado com sucesso!", "user": new_user}
    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))
```


</details>

#### Edição de usuários
<details>
<summary>Código para o Update de usuários</summary>

<P>Repository</P>

```python
from api_6sem_back_end.db.db_configuration import db_data
from bson import ObjectId

collection = db_data["users"]

class UpdateRepository:
    @staticmethod
    def find_by_email_or_name(identifier: str):
        return collection.find_one({
            "$or": [
                {"email": identifier},
                {"name": identifier}
            ]
        })

    @staticmethod
    def update_user(agent_id: int, update_data: dict):
        result = collection.update_one(
            {"agent_id": agent_id},
            {"$set": update_data}
        )
        return result.modified_count > 0
    
    @staticmethod
    def find_by_agent_id(agent_id: int):
        return db_data["users"].find_one({"agent_id": agent_id})
    
    @staticmethod
    def find_by_name_or_email(identifier: str):
        return db_data["users"].find_one({
            "$or": [
                {"name": identifier},
                {"email": identifier}
            ]
        })
```
<P>Router</P>

```python
from fastapi import APIRouter
from api_6sem_back_end.services.update_service import UpdateService

router = APIRouter(prefix="/users", tags=["Users"])

@router.put("/edit")
def edit_user(data: dict):
    return UpdateService.edit_user(data)
```
<P>Service</P>

```python
from datetime import datetime, timezone, timedelta
from api_6sem_back_end.repositories.update_repository import UpdateRepository

class UpdateService:
    @staticmethod
    def edit_user(data: dict):
        identifier = data.get("identifier")
        update = data.get("update", {})

        if not identifier:
            return {"error": "É necessário fornecer o nome ou e-mail do usuário a ser atualizado"}

        user = UpdateRepository.find_by_name_or_email(identifier)

        if not user:
            return {"error": f"Usuário com nome ou e-mail '{identifier}' não encontrado"}

        agent_id = user.get("agent_id")
        if not agent_id:
            return {"error": "Usuário encontrado não possui agent_id válido"}

        update_fields = {}
        if "name" in update:
            update_fields["name"] = update["name"]
        if "role" in update:
            update_fields["role"] = update["role"]
        if "email" in update:
            update_fields["email"] = update["email"]
            update_fields["login.username"] = update["email"]

        update_fields["modified_at"] = datetime.now(
            timezone(timedelta(hours=-3))
        ).isoformat(timespec="seconds")

        updated = UpdateRepository.update_user(agent_id, update_fields)

        if updated:
            return {"message": f"Usuário '{identifier}' atualizado com sucesso"}
        else:
            return {"error": "Nenhum dado foi alterado"}
```
</details>

#### Filtros por status do chamado

<details>
<summary>Código em python para os filtros por status</summary>
<P>Router</P>

```python
from fastapi import APIRouter
from api_6sem_back_end.models.filter import Filtro
from api_6sem_back_end.services.ticket_status_service import TicketStatusService

router = APIRouter(prefix="/tickets", tags=["Tickets"])

@router.post("/count-by-status")
def count_tickets(filtro: Filtro):
    return TicketStatusService.count_tickets_by_status(filtro.filtro)
```

<P>Service</P>

```python
from api_6sem_back_end.repositories.ticket_status_repository import TicketStatusRepository

class TicketStatusService:
    @staticmethod
    def count_tickets_by_status(filtro: dict):
        result = TicketStatusRepository.count_by_status(filtro)

        # Constrói dicionário por status
        by_status = {r["_id"]: r["count"] for r in result}
        total_count = sum(by_status.values())

        return {
            "total": total_count,
            "by_status": by_status
        }
```

<P>Repository</P>

```python
import re
from api_6sem_back_end.db.db_configuration import db

collection = db["tickets"]

class TicketStatusRepository:
    @staticmethod
    def count_by_status(filtro: dict):
        query_filter = {
            "$or": [
                {"closed_at": None},
                {"closed_at": {"$exists": False}}
            ]
        }

        if filtro:
            for k, v in filtro.items():
                if v not in [None, "", [], {}]:
                    if isinstance(v, str):
                        query_filter[k] = re.compile(f"^{v.strip()}$", re.IGNORECASE)
                    else:
                        query_filter[k] = v

        
        matched_count = collection.count_documents(query_filter)
       
        pipeline = [
            {"$match": query_filter},
            {"$group": {"_id": "$status", "count": {"$sum": 1}}},
            {"$sort": {"_id": 1}}
        ]

        cursor = collection.aggregate(pipeline)


        result = list(cursor)

       
        return result
```
</details>

### Soft e Hard Skills
<p>Consegui conciliar durante o desenvolvimento do projeto com eficiência coordenando as tarefas de maneira eficaz, pude notar algumas dificuldades pontuais minhas onde pude trabalhar nelas sendo ou não auxiliado e realmente entender o que ocorria em determinadas situações tudo isso sem preudicar o desenvolvimento do projeto, o que foi exetremamente importante além disso colaborei de forma eficaz com meus colegas de equipe os auxiliando também em suas dificuldades pessoais </p>


#### Soft Skills
<details>

| Habilidade | Classificação |
| :-----: | :-----: |
| Proatividade | Busquei ao máximo trabalhar em tasks e auxiliar sempre que necessário o grupo |
| Responsabilidade | Fiz de tudo para semrpe priorizar o desenvolvimento do projeto para não atrasar o time |
| Companheirismo	| Após finalizar o que eu era encarregado buscava auxiliar os colegas |
| Flexibilidade	| Tive de equilibrar trabalho, demais materias da faculdade e a produção do projeto |

</details>

#### Hard Skills
<details>

| Habilidade | Nota | Classificação |
| :-----: | :-----: | :-----: | 
| Python | ★★★★★ | Sei fazer com autonomia |
| Jira | ★★★☆☆ | Sei fazer com ajuda |
| Git |	★★★★☆ | Entendi |
| Postman | ★★★★☆ | Sei fazer com autonomia |
| HTML5 | ★★★☆☆ | Entendi |
| JavaScript |	★★★☆☆ | Entendi |
| VueJS | ★★★☆☆ | Entendi |
| VSCode | ★★★★★ | Sei fazer com autonomia |
| GitHub | ★★★★★ | Sei fazer com autonomia |
| TypeScript | ★★★☆☆ | Entendi |
| MongoDB |	★★★☆☆ | Entendi |
| Porphet | ★★★☆☆ | Sei fazer com ajuda |

</details>
