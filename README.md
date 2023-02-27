# PiggyBank

Uma API para o sistema de controle de gastos pessoais.

## Endpoints
- Despesas
    - [Cadastrar](#cadastrar-despesa)
    - Listar todas
    - Apagar
    - Alterar
    - [Mostrar os detalhes](#detalhar-despesa)
- Contas
    - Cadastrar
    - Listar todas
    - Apagar
    - Alterar
    - Mostrar os detalhes
- Categorias

---

### Cadastrar Despesa
`POST` /piggybank/api/despesa

| campo | tipo | obrigatório | descrição
|-------|------|:-------------:|--
| valor | decimal | sim | é o valor da despesa. deve ser maior que zero
| categoria_id | int | sim | é o id de uma categoria previamente cadastrada
| conta_id | int | sim | é o id de uma conta previamente cadastrada
| data | data | sim | é data da despesa
| descricao | texto | não | uma descrição da despesa com no máximo 255 caracteres

**Exemplo de corpo do request**

```js
{
    "valor": 100.00,
    "categoria_id": 1,
    "conta_id" : 1,
    "data": "2023-01-27",
    "descricao": "cinema com os amigos"
}
```

**Códigos de Resposta**

| código | descrição 
|-|-
| 201 | despesa cadastrada com sucesso
| 400 | erro na validação dos dados da requisição

---

### Detalhar Despesa
`GET` /piggybank/api/despesa/{id}

**Exemplo de corpo da resposta**

```js
{
    "valor": 100.00,
    "categoria": {
        "categoria_id": 1,
        "nome": "lazer"
    }
    "conta": {
        "conta_id" : 1,
        "nome": "itaú"
    }
    "data": "2023-01-27",
    "descricao": "cinema com os amigos"
}
```

**Códigos de Resposta**

| código | descrição 
|-|-
| 200 | dados retornados no corpo da resposta
| 404 | não foi encontrada despesa com o id informado