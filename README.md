# 📚 Sistema de Biblioteca – CRUD de Gêneros, Autores e Livros

Projeto fullstack desenvolvido como desafio técnico, contemplando **API REST (Spring Boot + Java 21)**, **SPA (Angular)** e **Banco de Dados MySQL**.  

O sistema permite:
- Cadastro, consulta, edição e exclusão de **Gêneros**.
- Cadastro, consulta, edição e exclusão de **Autores**.
- Cadastro, consulta, edição e exclusão de **Livros**, vinculados a **um Autor** e **um Gênero**.

---

## 🚀 Tecnologias

### Backend
- Java 21
- Spring Boot 3.3.x
- Spring Data JPA + Hibernate
- Spring Security (JWT)
- Flyway (migrations)
- MySQL
- Swagger / OpenAPI
- JUnit 5 (testes)

### Frontend
- Angular 17
- Angular Router
- HttpClient / Axios
- State Management (Services/Store)
- Nginx (deploy containerizado)

### Infra
- Docker / Docker Compose
- Containers independentes (frontend, backend, db)
- Persistência de dados via volume Docker

---

## 📂 Estrutura do Projeto

```
.
├── backend/        # API Spring Boot
│   ├── src/main/java/com/biblioteca
│   ├── src/main/resources/db/migration (Flyway)
│   └── Dockerfile
│
├── frontend/       # SPA Angular
│   ├── src/app
│   └── Dockerfile
│
├── docker-compose.yml
└── README.md
```

---

## ⚙️ Configuração do Ambiente

### 1. Pré-requisitos
- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- (Opcional) [Node.js + Angular CLI](https://angular.io/cli) para rodar o frontend localmente em desenvolvimento

---

### 2. Subir os containers
Na raiz do projeto:

```bash
docker-compose up --build
```

Isso vai levantar:
- **MySQL** → porta `3306`
- **Backend (Spring Boot)** → porta `8080`
- **Frontend (Angular + Nginx)** → porta `4200`

---

### 3. Acessar aplicações

- **Frontend Angular:** [http://localhost:4200](http://localhost:4200)  
- **API Swagger:** [http://localhost:8080/api/v1/swagger-ui.html](http://localhost:8080/api/v1/swagger-ui.html)  
- **Banco MySQL:** `localhost:3306` (usuário `root`, senha `root`)

---

## 🔑 Autenticação e Segurança

A API utiliza **JWT (JSON Web Token)** para autenticação.  
- Usuários com role **READER** podem apenas listar dados.  
- Usuários com role **WRITER** podem criar, atualizar e deletar registros.  

Token JWT deve ser enviado no **header Authorization**:

```
Authorization: Bearer <seu_token>
```

---

## 🧪 Testes

### Backend
```bash
cd backend
./mvnw test
```

### Frontend
```bash
cd frontend
npm test
```

---

## 📌 Rotas principais da API

- `GET /api/v1/authors` → listar autores  
- `POST /api/v1/authors` → criar autor  
- `GET /api/v1/genres` → listar gêneros  
- `POST /api/v1/genres` → criar gênero  
- `GET /api/v1/books` → listar livros  
- `POST /api/v1/books` → criar livro  

---

## 👨‍💻 Desenvolvimento

### Rodar Backend sem Docker
```bash
cd backend
./mvnw spring-boot:run
```

### Rodar Frontend sem Docker
```bash
cd frontend
ng serve -o
```

---

## 📜 Licença
Este projeto foi desenvolvido para fins acadêmicos/avaliativos.  
Sinta-se livre para utilizar como base em estudos ou projetos similares.
