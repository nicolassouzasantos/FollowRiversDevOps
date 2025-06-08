Guia para uso da API e containers Docker

Após o clone do repositório executar os seguintes passos:

1- Reload do Maven para carregar todas as dependências.

2- No caminho SalvandoGS-main\src\main\java\br\com\salvando executar a classe main SalvandoApplication para a criação da pasta target.

3- na raiz do projeto abra o terminal e execute os comandos docker:
docker-compose down -v  # Remove containers e volumes
docker-compose build --no-cache  # Rebuild sem cache
docker-compose up -d  # Sobe em background
docker-compose logs -f app  # Acompanha logs do app

para logs:
docker-compose logs mysql-db  # Logs do MySQL

4- Com isso, a aplicação estará rodando e retornando as chamadas na porta 8080, vamos aos testes do CRUD:
Classe Usuario:
- GET http://localhost:8080/api/usuarios
- POST http://localhost:8080/api/usuarios
body JSON:
{
  "nome": "Teste da Silva",
  "email": "teste.silva@email.com",
  "senha": "123456789",
  "telefone": "(11) 11111-1111",
  "endereco": "Rua dos Testes, 123 - São Paulo, SP"
}
- PUT http://localhost:8080/api/usuarios/{id}
body JSON:
{
  "nome": "Teste da Silva",
  "email": "teste.silva@email.com",
  "senha": "1234567",
  "telefone": "(11) 22222-2222",
  "endereco": "Rua dos Testes, 123 - São Paulo, SP"
}
- DELETE http://localhost:8080/api/usuarios/{id}

Classe Sensor:
- GET http://localhost:8080/api/sensores
- POST http://localhost:8080/api/sensores
body JSON:
{
  "numeroSensor": 1004,
  "latitude": -55,
  "longitude": -50
}
- PUT http://localhost:8080/api/sensores/{id}
body JSON:
{
  "numeroSensor": 1004,
  "latitude": -60,
  "longitude": -60
}
- DELETE http://localhost:8080/api/sensores/{id}

Classe Evento:
- GET http://localhost:8080/api/eventos
- POST http://localhost:8080/api/eventos
body JSON:
{
  "dataHora": "2024-06-08T14:30:00",
  "idSensor": 1004
}
- DELETE http://localhost:8080/api/eventos/{id}
