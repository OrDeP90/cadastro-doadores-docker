Sistema de Cadastro de Doadores de Sangue
Este projeto é uma aplicação composta por três contêineres Docker: frontend em React servido via Nginx, backend em Node.js com Express, e banco de dados MySQL 8.0. A aplicação permite cadastrar doadores de sangue pela interface web e salva os dados no banco.

Para rodar o sistema, você precisa do Docker e Docker Compose instalados. Após clonar o repositório, basta executar docker-compose up --build na pasta do projeto. Os contêineres irão subir e se comunicarão entre si usando os nomes dos serviços definidos no docker-compose (como mysql e backend), conforme a boa prática recomendada de não usar localhost para comunicação entre contêineres.

O frontend ficará acessível em http://localhost:3000 e a API backend em http://localhost:5000. O backend expõe um endpoint POST /doadores para cadastrar novos doadores, que devem enviar os dados: nome, tipo sanguíneo, data de nascimento, email e consentimento (booleano). O banco de dados MySQL pode ser acessado externamente via porta 3306, usuário root e senha root, na database projetoDevOps.

As variáveis de ambiente para o backend estão no arquivo .env, configurando a conexão com o banco via hostname mysql (nome do serviço no Docker Compose), usuário, senha e nome do banco. O banco de dados inicializa com um script init.sql para criar a tabela de doadores.

Para acessar o banco e verificar os dados cadastrados, use o MySQL Workbench ou qualquer cliente conectado ao localhost:3306 com as credenciais citadas. Lembre-se que os contêineres se comunicam internamente pelo nome dos serviços, e as portas expostas servem para acesso externo (ex: seu PC para o MySQL e frontend).



## 🚀 Como Executar o Projeto

### Pré-requisitos

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

### Passos

# Clone o repositório
git clone https://github.com/seuusuario/projeto-devops.git
cd projeto-devops

# Suba os contêineres
docker-compose up --build



#Acesso à Aplicação
Frontend: http://localhost:3000

Backend (API): http://localhost:5000


📦 Endpoints da API (Backend)

POST /doadores
Cadastra um novo doador:
{
  "nome": "João da Silva",
  "email": "joao@email.com",
  "tipo_sanguineo": "O+",
  "consentimento": true
}