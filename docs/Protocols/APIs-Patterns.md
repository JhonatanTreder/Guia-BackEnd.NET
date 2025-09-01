# Recapitulação Anterior
Anteriormente, falamos sobre **websockets**, que é uma tecnologia muito utilizada em aplicações hoje em dia que tem a necessidade de _manter_ uma conexão aberta entre **cliente** e **servidor** para o **envio**
e **recebimento** de dados de maneira contínua. Também falamos sobre as vantagens e desvantagens de se utilizar **websockets**, já que o uso dessa tecnologia deve ser realizada de forma consciente para não haver
perca de performance na aplicação.

# Introdução
Agora iremos falar sobre os três modelos arquiteturais mais utilizados hoje em dia: o **REST** (como já falamos anteriormente), o **GraphQL** (criado pelo **FaceBook**) e o **gRPC** (Google RPC).
Todos esses modelos arquiteturais possuem características e necessidades de uso únicas, ou seja, cada um deles foram criados para **suprir** um ou mais problemas específicos em aplicações web hoje em dia.
Neste caso, eu irei estar mostrando as características e casos de uso para cada um dos três modelos arquiteturais.

# REST - Resumo
> **ATENÇÃO:** Nesse tópico eu não irei me aprofundar no conceito **REST** porque esse conceito já foi abordado anteriormente, então caso você não entenda como funciona esse padrão arquitetural,
eu recomendo que você acesse a documentação que fala sobre ele em: [Parte 1 (Conceitos Básicos) Padrão RESTful vs. Padrão SOAP](/docs/Basics/RESTful-SOAP.md). <br>

Como já falamos anteriormente, o **REST** (**RE**presentational **S**tate **T**ransfer) é um estilo arquitetural que define um conjunto de diretrizes que devem ser implantadas nas **APIs Web**.
Esse conjunto de diretrizes é um padrão arquitetural que se baseia em **recursos** da aplicação, ou seja, entidades que representam objetos ou conceitos do domínio da aplicação
(por exemplo: **usuários**, **produtos**, **pedidos**). As 6 regras que define o **REST** são: <br>

- **Arquitetura Cliente-Servidor:** O cliente (**Front-End** consumidor) e o servidor (**Back-End** fornecedor de dados/serviços) devem ser separados.
O cliente só se preocupa em **consumir** dados e o servidor só se preocupa em **fornecer** dados e **gerenciar** a lógica de negócio. <br>

- **Sem Estado (Stateless):** Cada _requisição_ do cliente para o servidor deve conter todas as informações necessárias para ser processada e o servidor
**não** deve armazenar informações de estado do cliente entre as _requisições._ <br>

- **Cacheabilidade:** Se for possível, dados devem ser armazenados em cache para melhorar o desempenho e evitar buscas extras no servidor. <br>

- **Interface Uniforme:** Essa é uma das regras mais importantes, pois a comunicação deve ser padronizada. Inclui quatro sub-regras:
  - **Identificação de recursos:** Cada recurso deve ter uma URL única, por exemplo: `/users/123`. 
  - **Manipulação de Recursos Via Representações:** Você interage com recursos através de representações, como **JSON**, **XML**, etc.
  - **Mensagens Autodescritivas:** A requisição deve ter contexto suficiente para poder ser entendida, por exemplo: headers informando formato (**Content-Type: application/json**).
  - **Hypermedia (HATEOAS):** As respostas podem incluir links para indicar ações possíveis, por exemplo: a resposta de um pedido pode incluir um link para cancelar aquele pedido.

- **Sistemas em Camadas:** A **API** pode ser composta por várias camadas, como por exemplo: servidores intermediários, proxies, balanceadores de carga, gateaways, etc. <br>

- **Código Sob Demanda (Opcional):** O servidor pode oferecer **scripts** e **códigos executáveis**, ampliando assim as funcionalidades da aplicação.
Porém é opcional e pouco utilizado hoje em dia. <br>

# GraphQL
Diferente do **REST** e de outros modelos arquiteturais, o **GraphQL** é uma **linguagem de consulta** e um **runtime** que define exatamente **quais** dados o cliente quer receber da **API**,
evitando assim o **_overfetching_** (trazer dados demais) quanto **_underfetching_** (trazer dados insuficientes). Esses dois conceitos de **_overfetching_** e **_underfetching_** é um problema
observável que pode ocorrer em **APIs RESTful** (ou em outras implementações) quando o usuário precisa requisitar vários endpoints para conseguir juntar os dados necessários. Porém o **GraphQL**
veio justamente para resolver essa limitação, além de oferecer uma grande flexibilidade na forma de **consultar** e **manipular** os dados existentes nas aplicações.

## Como Surgiu o GraphQL?
> **_"No início da década de 2010, o Facebook estava passando por um crescimento e transformação massivos. Mas uma base de usuários em crescimento e um ambiente de aplicativo móvel cada vez mais
> complexo tornaram sua abordagem RESTful existente insustentável, já que ela exigia múltiplas idas e voltas a diferentes endpoints de API para buscar todos os dados necessários da consulta.
> As APIs REST não estavam equipadas para lidar com interfaces de usuário complexas e orientadas por dados, e frequentemente enfrentavam problemas de latência e ineficiências de dados,
> especialmente para usuários móveis com planos de dados limitados ou caros. Em resposta a esses desafios, engenheiros do Facebook desenvolveram o GraphQL
> (junto com a plataforma de aplicação de página única React), lançando-o como uma solução de código aberto em 2015. Por fim, o Facebook transferiu o serviço para a GraphQL Foundation,
> que inclui empresas membros como AWS, Gatsby, Intuit e IBM, em 2018."_** <br>

**Fonte Textual:** https://www.ibm.com/br-pt/think/topics/graphql

## Funcionamento - GraphQL
O funcionamento de uma **API GraphQL** possui uma estrutura que é composta por quatro processos na tratativa de dados, que são eles: <br>
- **Schemas (Esquemas):** O **Schema** é um "contrato" que define quais dados ou recursos que o usuário deseja acessar na **API**.
Essa definição resume quais dados e tipos de objetos o usuário está solicitando. Veja um exemplo em **GraphQL:** <br>

  ---
    ```graphql
      type User {
      id: ID!
      name: String!
      email: String!
    }
    
    type Query {
      user(id: ID!): User
      users: [User!]!
    }
    ```
  ---

- **Resolvers (Resolvedores):** Os **Resolvers** são funções responsáveis por retornar os dados definidos nos Schemas. Eles atuam como uma ponte entre o **Schema** e a fonte de dados
(banco de dados, API externa, etc.). Cada campo definido no Schema precisa de um **resolver** correspondente para que os dados sejam efetivamente retornados. Por exemplo: <br>

  ---
  ```graphql
    const resolvers = {
      Query: {
        user: (parent, args, context, info) => {
          return database.findUserById(args.id);
        },
        users: () => {
          return database.getAllUsers();
        },
      },
    };
  ```
  ---


- **Queries (Consultas):** As **Queries** são operações de leitura que permitem ao cliente solicitar dados específicos da API. Elas seguem a definição do Schema e usam os resolvers para obter os dados.
Exemplo de **Query** que poderia ser feita pelo cliente: <br>

  ---
  ```graphql
    query {
      user(id: "1") {
        id
        name
        email
      }
    }
  ```
  ---

  - Resultado esperado: <br>
    ---
    ```json
      {
        "data": {
          "user": {
            "id": "1",
            "name": "João",
            "email": "joao@example.com"
          }
        }
      }
    ```
    ---


- **Mutations (Modificações):** As Mutations são operações que permitem criar, atualizar ou deletar dados na API. Funcionam de maneira similar às queries, mas modificam o estado da aplicação.
Cada mutation também precisa de um resolver correspondente. Por exemplo: <br>

  ---
  ```graphql
    type Mutation {
      createUser(name: String!, email: String!): User
    }
  ```
  ---


  - Exemplo de Mutation feita pelo cliente: <br>

    ---
    ```graphql
      mutation {
        createUser(name: "Maria", email: "maria@example.com") {
          id
          name
          email
        }
      }
    ```
    ---


    - Resultado esperado: <br>
  
     ---
      ```json
          {
          "data": {
            "createUser": {
              "id": "2",
              "name": "Maria",
              "email": "maria@example.com"
            }
           }
          }
      ```
      ---

# gRPC
Antes de falarmos sobre o**gRPC**, precisamos entender o que é o **RPC**. O **RPC** (**R**emote **P**rocedure **C**all) ou **Chamada de Procedimento Remoto**, é um protocolo/abordagem que permite que um
programa execute funções ou métodos em outro computador/servidor remoto como se estivesse chamando uma função local. Ou seja, em vez de você se preocupar em **como** enviar uma requisição **HTTP** ou como
os dados serão transmitidos pela rede, o **RPC** abstrai isso e faz parecer que você só está chamando uma função comum no seu código.

## Como Funciona o RPC
O funcionamento do **RPC** pode ser feito da seguinte forma: O Cliente chama uma função como se fosse local, depois o **RPC** intercepta essa chamada, transforma em uma mensagem e envia para o servidor remoto.
Depois que o servidor receber a requisição, ele executa a função do lado dele e retorna o resultado. Por fim o Cliente recebe o resultado como se tivesse rodado a função localmente. <br>

## Funcionamento - gRPC
O **gRPC** segue a mesma ideia do **RPC tradicional**, ou seja, ele também realiza funções remotamente como se fosse local, porém o **gRPC** contém diversas melhorias.
Ele é construído sobre o protocolo **HTTP/2**, que oferece vantagens como:

- **Comunicação Bidirecional (streaming)**: O cliente e servidor podem enviar e receber dados de forma contínua (algo parecido com o **websockets** que já foi mencionado anteriormente).
- **Compactação e Eficiência**: O **gRPC** utiliza o formato **Protobuf (Protocol Buffers)** para serialização de mensagens, que é mais rápido e leve que **JSON** ou **XML**.
  - Exemplo de um código escrito em Protobuf (**.proto**): <br>
  
    ---
    ```protobuf
      syntax = "proto3";

      // Aqui estamos definindo o pacote
      package biblioteca;
      
      // Exemplo de serviço gRPC
      service LivroService {
        // Um método para buscar um livro pelo Id
        rpc ObterLivro (LivroRequest) returns (LivroResponse);
      
        // E outro método para adicionar um novo livro
        rpc AdicionarLivro (NovoLivroRequest) returns (LivroResponse);
      }
      
      // Uma mensagem de requisição para buscar um livro
      message LivroRequest {
        int32 id = 1;
      }
      
      // Uma mensagem de resposta com informações do livro
      message LivroResponse {
        int32 id = 1;
        string titulo = 2;
        string autor = 3;
        int32 anoPublicacao = 4;
      }
      
      // E uma mensagem de requisição para adicionar um novo livro
      message NovoLivroRequest {
        string titulo = 1;
        string autor = 2;
        int32 anoPublicacao = 3;
      }
    ```
    ---
    
- **Suporte a Múltiplas linguagens**: O **gRPC** gera códigos automaticamente para várias linguagens, como **C#**, **Java**, **Go**, **Python**, entre outras.  
- **Baixa Latência e Alta Performance**: O uso do **gRPC** é muito útil em cenários de **microsserviços** e ambientes que precisam de **respostas rápidas**.  

O fluxo do **gRPC** pode funcionar da seguinte forma:

1. O desenvolvedor define os métodos e mensagens em um arquivo **.proto** (Protocol Buffers).  
2. O **gRPC** gera automaticamente o código do **cliente** e **servidor** para uma linguagem desejada.  
3. O **Cliente** chama o método como se fosse local, porém na verdade envia uma requisição para o servidor por meio do **HTTP/2**.  
4. O **Servidor** recebe a requisição, logo em seguida processa e por fim retorna a resposta, que o cliente trata como se fosse o retorno de uma função local. <br>

# Casos de Uso
Cada um desses modelos arquiteturais possuem características próprias que o tornam mais adequado para determinados tipos de cenários existentes, e a escolha correta
de qual tecnologia abordar pode ser muito benéfica para o estado da aplicação. Abaixo está alguns exemplos de casos onde é recomendável usar cada um deles. <br>

## REST
O **REST** é mais recomendável em cenários onde a aplicação requer um bom nível de simplicidade/organização e de uma estrutura mais padronizada para os recursos existentes. Por exemplo: <br>

- **Em APIs Públicas ou Internas Simples:** Quando os recursos podem ser acessados de forma padronizada via **URLs**.  
- **Em Sistemas CRUD Tradicionais:** Em sistemas de **CRUD** clássicos é recomendável utilizar o **REST**.
- **Em Integração Entre Sistemas Heterogêneos:** Por causa da compatibilidade com **HTTP** e formatos como **JSON** e **XML**.  
- **Cache e Performance Básica:** Quando é importante aproveitar mecanismos de cache via **HTTP** o **REST** também é recomendável neste cenário
(tendo em vista que uma das diretrizes do **REST** é a **_cacheabilidade_**). <br>
---

## GraphQL
A implementação do **GraphQL** é mais indicado quando há necessidade do cliente controlar exatamente o que deseja receber ou em sisemas que necessita de uma flexibilidade/controle maior nos dados.
Por exemplo: <br>

- **Em Aplicações com Interfaces Complexas:** Aplicações como dashboards, aplicativos móveis ou **SPAs** (**S**ingle **P**age **A**pplications).  
- **Em Redução de Overfetching/Underfetching:** Quando múltiplos recursos precisam ser combinados em uma única requisição.  
- **Em Agregação de Dados de Múltiplas Fontes:** Quando os dados vêm de diferentes **APIs** ou bancos de dados.  
- **Em Ambientes com Limitações de Banda ou Alta Latência:** Como dispositivos móveis ou **IoT** (**I**nternet **o**f **T**hings ou "Internet das Coisas" em português).
---

## gRPC
Já o **gRPC** é mais indicado em cenários que exigem alta performance, baixa latência ou uma comunicação eficiente entre os serviços existentes. Por exemplo: <br>

- **Em Microsserviços Distribuídos:** Como comunicações eficientes entre serviços internos de uma aplicação.  
- **Em Streaming de Dados em Tempo Real:** Como **chats**, monitoramento de métricas ou no envio contínuo de dados/informações.  
- **Em Aplicações que Precisam de Baixa Latência:** Como jogos online, trading financeiro ou sistemas de **IoT**.  
- **Em Cenários de Suporte a Múltiplas Linguagens e Plataformas:** Quando diferentes sistemas precisam se comunicar de forma consistente e performática.
---

# Resumo
Hoje em dia podemos implementar vários modelos arquiteturais de acordo com a necessidade da aplicação. A implementação do tipo arquitetural não está limitada apenas ao **REST**
que é muito utilizado na maioria dos sistemas atualmente, podemos utilizar outros meios como o **GraphQL** para maior controle dos dados e o **gRPC** em aplicações que exigem alta
performance e integridade interna do sistema. Cada estilo arquitetural vai depender das necessidades da aplicação, mas não tem problema algum utilizar o **REST** como alternativa,
apenas é importante frizar que existem outras alternativas.

# Documentações de Referência

| Conceitos                            | Links                                                                                                                                                |
|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| O Que é uma API RESTful?             | [RedHat - O Que é uma REST API](https://www.redhat.com/pt-br/topics/api/what-is-a-rest-api)                                                          |
| O Que é o GraphQL?                   | [RedHat - O Que é GraphQL](https://www.redhat.com/pt-br/topics/api/what-is-graphql#graphql-vantagens-e-desvantagens)                                 |
| O Que é o RPC?                       | [IBM - Remote Procedure Call](https://www.ibm.com/docs/pt-br/aix/7.3.0?topic=concepts-remote-procedure-call)                                         |
| O Que é o gRPC?                      | [YouTube - O Que é gRPC](https://www.youtube.com/watch?v=F4t3ZBVMlvo)                                                                                |
| Podcast - RESTful vs GraphQL vs gRPC | [YouTube - Podcast RESTful vs GraphQL vs gRPC](https://www.youtube.com/watch?v=47KxEv2F8TY)                                                          |
