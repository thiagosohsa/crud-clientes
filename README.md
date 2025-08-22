# Desafio: CRUD de Clientes

## 🎯 Objetivo

Construir uma API REST com **Spring Boot** para gerenciar clientes,
implementando as operações básicas de CRUD com:

- Busca paginada de
recursos
- Busca de recurso por ID
- Inserção de novo recurso
- Atualização de recurso
- Deleção de recurso

O projeto utiliza **Java + Maven + Spring Data JPA** com **H2 Database**
para testes.

------------------------------------------------------------------------

## 🏗️ Especificação da entidade

A entidade `Client` possui os seguintes atributos: 
- `id` (Long)
- `name` (String)
- `cpf` (String)
- `income` (Double)
- `birthDate` (Instant/LocalDate)
- `children` (Integer)

------------------------------------------------------------------------

## ⚙️ Tecnologias utilizadas

-   Java 21
-   Spring Boot
-   Spring Data JPA
-   Maven
-   H2 Database

------------------------------------------------------------------------

## 🚦 Regras de validação

-   **Nome**: não pode ser vazio.
-   **Data de nascimento**: não pode ser futura (`@PastOrPresent`).
-   Exceções tratadas:
    -   **404**: recurso não encontrado (GET por id, PUT, DELETE).
    -   **422**: erro de validação com mensagens customizadas.

------------------------------------------------------------------------

## 📡 Endpoints principais

### 🔍 Buscar cliente por ID

``` http
GET /clients/1
```

### 📑 Busca paginada

``` http
GET /clients?page=0&size=6&sort=name
```

### ➕ Inserir cliente

``` http
POST /clients
{
  "name": "Maria Silva",
  "cpf": "12345678901",
  "income": 6500.0,
  "birthDate": "1994-07-20",
  "children": 2
}
```

### ✏️ Atualizar cliente

``` http
PUT /clients/1
{
  "name": "Maria Silvaaa",
  "cpf": "12345678901",
  "income": 6500.0,
  "birthDate": "1994-07-20",
  "children": 2
}
```

### ❌ Deletar cliente

``` http
DELETE /clients/1
```

------------------------------------------------------------------------

## 🧪 Como rodar o projeto

1.  Clone o repositório:

    ``` bash
    git clone https://github.com/thiagosohsa/crud-clientes.git
    ```

2.  Entre na pasta do projeto:

    ``` bash
    cd crud-clientes
    ```

3.  Execute com Maven:

    ``` bash
    ./mvnw spring-boot:run
    ```

4.  Acesse o console do H2 (opcional):\
    <http://localhost:8080/h2-console>

    -   JDBC URL: `jdbc:h2:mem:testdb`
    -   User: `sa`
    -   Password: *(em branco)*

## 💾 Seeding da Base de Dados

O projeto já vem com instâncias de dados (seeding) carregadas automaticamente.

```sql
INSERT INTO tb_client (name, cpf, income, birth_date, children) VALUES('Ana rosa', '78945612301', 3500.0, '1987-06-02', 2);
INSERT INTO tb_client (name, cpf, income, birth_date, children) VALUES('Paulo Rodrigues', '32165498798', 6000.0, '1998-08-11', 0);
INSERT INTO tb_client (name, cpf, income, birth_date, children) VALUES('Bruno Ferreira', '96385274110', 5500.0, '1981-02-20', 3);
INSERT INTO tb_client (name, cpf, income, birth_date, children) VALUES('Fernanda Sousa', '14725815996', 4000.0, '1997-05-01', 0);
INSERT INTO tb_client (name, cpf, income, birth_date, children) VALUES('Alex Juarez', '65432198732', 7500.0, '1971-02-19', 4);
INSERT INTO tb_client (name, cpf, income, birth_date, children) VALUES('Maria Gabriela', '54862532662', 1500.0, '1999-03-07', 1);
INSERT INTO tb_client (name, cpf, income, birth_date, children) VALUES('Marcelo Costa', '95184762585', 10000.0, '1995-10-02', 1);
INSERT INTO tb_client (name, cpf, income, birth_date, children) VALUES('Jessica Bittencourt', '32198735702', 30000.0, '1981-11-07', 5);
INSERT INTO tb_client (name, cpf, income, birth_date, children) VALUES('Cristiano Pereira', '84595687421', 7000.0, '1988-02-17', 0);
INSERT INTO tb_client (name, cpf, income, birth_date, children) VALUES('Larissa Alves', '36569885622', 5500.0, '1998-01-20', 1);
```