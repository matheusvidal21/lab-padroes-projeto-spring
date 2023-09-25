# 🧩 API com Padrões de Projeto em Spring
Este é um projeto de exemplo que demonstra o uso de alguns padrões de projeto em Spring, como Singleton, Strategy, e Facade. Vamos explicar cada um deles e apresentar detalhes sobre a API.

## Padrões de Projeto Utilizados

### **1. Singleton**
O padrão Singleton é implementado pelo Spring Framework de forma automática com anotações, exemplo do "@Autowired". Isso significa que os componentes gerenciados pelo Spring, como os serviços e repositórios, são instanciados apenas uma vez e compartilhados em toda a aplicação. Não é necessário fazer nada especial para aplicar o Singleton no Spring, pois ele cuida disso internamente.

### **2. Strategy**
O padrão Strategy é implementado na interface ClienteService. Essa interface define um conjunto de operações relacionadas a clientes que podem ter várias implementações diferentes. Isso permite que você escolha dinamicamente qual implementação usar, tornando seu sistema flexível e extensível.

### **3. Facade**
O padrão Facade é implementado na classe ClienteRestController. Essa classe atua como uma fachada que abstrai a complexidade das integrações com o banco de dados H2 e a API do ViaCEP em uma interface REST simples e coesa. Os endpoints REST expostos nesta classe permitem que os clientes interajam com a API de forma transparente, sem se preocupar com os detalhes de implementação.

## 📋 Descrição da API
Esta API gerencia informações de clientes, incluindo detalhes sobre seus endereços obtidos através do serviço ViaCEP. Ela oferece os seguintes recursos:
- **`GET /clientes:`** Retorna a lista de todos os clientes cadastrados.
- **`GET /clientes/{id}:`** Retorna um cliente específico com base no ID.
- **`POST /clientes:`** Cria um novo cliente.
- **`PUT /clientes/{id}:`** Atualiza um cliente existente com base no ID.
- **`DELETE /clientes/{id}:`** Remove um cliente com base no ID.

### 🔍 Detalhes Importantes da Implementação
- O serviço de busca de CEP na API do ViaCEP é acessado através do cliente HTTP criado com o Spring Cloud OpenFeign. O método consultarCep do ViaCepService é responsável por essa integração.
- A classe ClienteServiceImpl implementa a interface ClienteService, aplicando o padrão Strategy. Ela também gerencia a integração com o ViaCEP e persistência no banco de dados.
- Os repositórios ClienteRepository e EnderecoRepository facilitam o acesso e a manipulação dos dados no banco de dados H2.

### ⚙️ Pré-requisitos
Antes de usar esta API, certifique-se de ter o seguinte instalado:
- Java JDK 8 ou superior
- Spring Boot (geralmente gerenciado pelo Maven ou Gradle)
- Dependência Spring Web
- Dependência Spring Data JPA
- Dependência H2 Database
- Dependência do Spring Cloud OpenFeign (para acessar o serviço ViaCEP)

## 🛠️ Instalação 
1. Clone este repositório.
2. Importe o projeto em sua IDE Java.
3. Certifique-se de que todas as dependências sejam resolvidas automaticamente.
4. Execute o aplicativo Spring Boot.

## 🔧 Uso
Para interagir com esta API e testar os endpoints de forma mais conveniente, você pode utilizar o Swagger UI. O Swagger UI fornece uma interface de usuário interativa para explorar e testar os endpoints da API.
Para acessar o Swagger UI, siga os passos abaixo:
1. Certifique-se de que o aplicativo está em execução.
2. Abra seu navegador e navegue até o seguinte URL:
```http://localhost:PORT/swagger-ui/index.html#/```
Substitua PORT pela porta em que o aplicativo está sendo executado. Por padrão, o Spring Boot geralmente usa a porta 8080.
- No Swagger UI, você verá uma lista de todos os endpoints disponíveis na API, juntamente com detalhes sobre os parâmetros e os modelos de dados necessários para fazer as chamadas.

Aqui estão alguns exemplos de como usar os endpoints:
- **`GET /clientes:`** Recupere a lista de todos os clientes.
- **`GET /clientes/{id}:`** Recupere um cliente específico substituindo {id} pelo ID do cliente desejado.
- **`POST /clientes:`** Crie um novo cliente enviando os dados JSON no corpo da solicitação.
- **`PUT /clientes/{id}:`** Atualize um cliente existente substituindo {id} pelo ID do cliente e enviando os dados JSON atualizados no corpo da solicitação.
- **`DELETE /clientes/{id}:`** Remova um cliente específico substituindo {id} pelo ID do cliente a ser excluído.

## 📂 Estrutura de Diretórios
```
src/
├── main/
│   ├── java/
│   │   ├── one.digitalinnovation.gof/
│   │   │   ├── controller/
│   │   │   │   └── ClienteRestController.java
│   │   │   ├── model/
│   │   │   │   ├── Cliente.java
│   │   │   │   ├── ClienteRepository.java
│   │   │   │   ├── Endereco.java
│   │   │   │   ├── EnderecoRepository.java
│   │   │   │   └── ...
│   │   │   ├── service/
│   │   │   │   ├── impl/
│   │   │   │   │   ├── ClienteServiceImpl.java
│   │   │   │   ├── ClienteService.java
│   │   │   │   ├── ViaCepService.java
│   │   │   │   └── ...
│   │   ├── Application.java
│   ├── resources/
│   └── ...
└── ...
```

## 🤝 Contribuição
Se você deseja contribuir com melhorias ou correções para esta API, sinta-se à vontade para abrir um Pull Request. Ficaremos felizes em revisar e incorporar suas contribuições.
