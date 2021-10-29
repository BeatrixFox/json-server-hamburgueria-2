## Endpoints 9 disponiveis

como base da Url para as requisições temos :

https://my-notebook-json.herokuapp.com

# Rotas que não precisam de autenticação

> > > Cadastro < < <

Para cadastrar usuario use :

    	POST /register

    Seguindo o seguinte formato de requisição :
    	{
    		"email": "olivier@mail.com",
    		"password": "bestPassw0rd",
    		"name" : "oliver",
    		"age": 32
    	}

     campos obrigatórios são email e password.

> caso o retorno positivo :

POST /register - FORMATO DA RESPOSTA - STATUS 201

    {
    	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6Im9saXZpZXJAbWFpbC5jb20iLCJpYXQiOjE2MzUxOTk2MjcsImV4cCI6MTYzNTIwMzIyNywic3ViIjoiMyJ9.tgkGl1fNgFMocVAakn_i21f1j0iTsoQ5jjdoSjW-v-Q",
    	"user": {
    		"email": "olivier@mail.com",
    		"name": "oliver",
    		"age": 32,
    		"id": 3
    	}
    }

> caso o retorno seja negativo:

possiveis erros

POST /register - FORMATO DA RESPOSTA - STATUS 400

"Email already exists"

POST /register - FORMATO DA RESPOSTA - STATUS 400

"Email and password are required"

> > > Login do usuário < < <

Para logar usuario use :

    	POST /login

    Seguindo o seguinte modelo de requisição :
    	{
    		"email": "olivier@mail.com",
    		"password": "bestPassw0rd",

    	}

> > > Produtos da API < < <

Para listar friends use :

    	GET /products

## Rotas que precisam de autenticação

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

    Authorization: Bearer {token}

> > > Listar produtos do carrinho geral < < <

Para listar use :

    	GET /card

> > > Listar produtos do carrinho por usuário < < <

Para listar produtos por usuário use :

    	GET /card?userId={id}

a onde o id é o id do usuário

> > > Usuário adicionar produtos no carrinho< < <

Para adicionar produtos ao cart use :

    	POST /cart

    Seguindo o seguinte formato de requisição :

    {
    	"name": "X-burguer",
    "image": "assets/burguer-1.webp",
    	"category": "Comida",
    	"price": "10.90",
     	"quant" : 1,
      	"userId": 3
    }

a onde o userId deve ser correspondente ao id do usuário que está logado.

> > > Usuário aumentar a quantidade de um mesmo produtos no carrinho< < <

Para adicionar produtos ao cart use :

    	Patch /cart/{id}

    Seguindo o seguinte formato de requisição :

    {
     	"quant" : 1,
    }

a onde o id deve ser correspondente ao id do produto que será atualizado.

> > > Usuário deletar produtos do carrinho< < <

Para deletar produtos do cart use :

    	Patch /cart/{id}

a onde o id deve ser correspondente ao id do produto que será deletado.
