# BCU API: cadastro e autenticação de usuários

## Descrição do Projeto

Contexto: desenvolvido como desafio técnico de processo seletivo.

## Funcionalidades

- **Cadastro de usuários** com validação de nome (3 a 50 caracteres), e-mail válido, senha (6 a 20 caracteres) e confirmação de senha.
- **API RESTful** para registro, login, consulta do usuário logado e logout, com respostas em JSON.
- **Persistência** em PostgreSQL.
- **Testes automatizados** garantindo que os dados sejam validados e gravados corretamente.
- **Ambiente** 100% em contêineres com Docker Compose.

## Tecnologias e Ferramentas Utilizadas

<div align="left">
    <img src="https://img.shields.io/badge/-Docker-%23fff?style=for-the-badge&logo=docker&logoColor=2496ED" target="_blank">
    <img src="https://img.shields.io/badge/-PHP-%23fff?style=for-the-badge&logo=php&logoColor=777BB4" target="_blank">
    <img src="https://img.shields.io/badge/-Laravel-%23fff?style=for-the-badge&logo=laravel&logoColor=FF2D20" target="_blank">
    <img src="https://img.shields.io/badge/-PHPUnit-%23fff?style=for-the-badge&logo=phpunit&logoColor=4FC08D" target="_blank">
    <img src="https://img.shields.io/badge/-PostgreSQL-%23fff?style=for-the-badge&logo=postgresql&logoColor=2496ED" target="_blank">
    <img src="https://img.shields.io/badge/-Vite-%23fff?style=for-the-badge&logo=vite&logoColor=4FC08D" target="_blank">
</div>

## Configuração do Ambiente Docker
1. Clone o repositório do projeto
```shellScript
git clone git@github.com:websterl3o/bcu_api.git
```
2. Crie o arquivo .env a partir do .env.example
```shellScript
cp src/.env.example src/.env
```
3. Execute o comando para subir o ambiente
```shellScript
docker-compose up -d --build
```
4. Execute o comando para instalar as dependências do projeto
```shellScript
docker-compose exec app composer install
```
5. Execute o comando para gerar a chave do projeto
```shellScript
docker-compose exec app php artisan key:generate
```
6. Execute o comando para criar a estrutura do banco de dados
```shellScript
docker-compose exec app php artisan migrate
```
7. Instale as dependências do node
```shellScript
docker-compose exec app npm install
```
8. Execute o comando para subir o servidor de desenvolvimento
```shellScript
docker-compose exec app npm run dev
```
9. Acesse o projeto em http://localhost:9898

### Rotas da Aplicação

| Método | URI        | Descrição                       |
| ------ | ---------- | ------------------------------- |
| GET    | /register  | Página de registro de usuário.  |
| GET    | /login     | Página de login de usuário.     |
| GET    | /dashboard | Página de dashboard de usuário. |
| GET    | /logout    | Logout de usuário.              |

### Rotas da API

| Método | URI                                | Descrição                            | Body                                                                                                         |
| ------ | ---------------------------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| POST   | http://localhost:9898/api/register | Registra um novo usuário.            | ``` { "name": "Leo", "email": "leo@gmail.com", "password": "dasdas", "password_confirmation": "dasdas" } ``` |
| POST   | http://localhost:9898/api/login    | Login em um usuário.                 | ``` { "email": "leo@gmail.com", "password": "dasdas" } ```                                                   |
| GET    | http://localhost:9898/api/me       | Busca informações do usuário logado. |                                                                                                              |
| POST   | http://localhost:9898/api/logout   | Remove sessão de usuário logado.     |                                                                                                              |
