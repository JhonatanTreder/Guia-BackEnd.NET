# [ Guia ] Back-End .NET/.NET Core <img width="30" height="30" alt="6132221" src="https://github.com/user-attachments/assets/42e075bc-8362-4225-8f6b-63c61750fc2d"/>

Repositório que serve como um guia de consulta para os termos no desenvolvimento Back-End no .NET. Facilitando assim a vida de pessoas que desejam consultar um conceito sobre o desenvolvimento back-end de forma rápida.

## Visão Geral
Antes de entender como o Back-End funciona, é importante se atentar aos conceitos básicos que o compõem. Da mesma forma que um prédio precisa de fundamentos sólidos antes de ser construído, também precisamos **aprender** e **entender** como funcionam esses conceitos básicos para que não venhamos se perder lá na frente. A primeira parte se diz respeito aos conceitos básicos que você vai encontrar ao decorrer da sua trajetória como desenvolvedor Back-End (conceitos esses que se irão se estender por toda a sua carreira) e as demais partes necessitam da primeira, então é de grande importância que você **NÃO** pule essa parte caso não tenha um conhecimento prévio antes. <br>

## Parte 1 - Conceitos Básicos
Aqui iremos abordar assuntos básicos que você com toda certeza encontrará em sua trajetória, assuntos como **_Requests/Responses_**, Comunicação com **_JSON e XML_**, Como funciona a comunicação entre **_Cliente e Servidor_** serão abordados aqui. <br>

[Servidores e Clientes](docs/Basics/Client-Server.md) <br>
[HTTP e HTTPS](docs/Basics/HTTP-HTTPS.md) <br>
[Padrão RESTful vs. Padrão SOAP](docs/Basics/RESTful-SOAP.md) <br>
[JSON e XML](docs/Basics/JSON-XML.md) <br>
[Banco de Dados](docs/Basics/DataBase.md) <br>
[Autenticação e Autorização](docs/Basics/Authentication-Authorization.md) <br>

## Parte 2 - Protocolos e Comunicação
Aqui trataremos conceitos de como os protocolos e comunicações se complementam entre si por meio de **_Rotas_**, **_EndPoints_**, **_APIs_**, etc. Essa parte já é um caminho andado para o entendimento de como se estruturar um Back-End com base em fundamentos de comunicação e tipos de protocolos. <br>

[DNS](docs/Protocols/DNS.md) <br>
[Web Sockets](docs/Protocols/WebSockets.md) <br>
[APIs RESTful vs GraphQL vs gRPC](docs/Protocols/APIs-Patterns.md) <br>
[Roteamento e Endpoints](docs/Protocols/Routes-EndPoints.md) <br>

## Parte 3 - Conceitos de Arquitetura
Essa parte abordará conceitos gerais sobre arquiteturas, bem como **_Padrões de Projetos_**, **_Injeção de Dependência_**, **_Tipos de Camadas em um Sistema_**, etc. Aqui estamos abordando o assunto de Back-End em um nível mais arquitetural das coisas, isto é, estamos falando sobre como um sistema deve se comportar como um todo por meio de boas práticas que vão desde um tipo de arquitetura até as nuances de sistemas.<br>

[Padrão MVC - Model View Controller](docs/ArchitectureConcepts/MVC-Architecture.md) <br>
[Camadas de um Sistema](docs/ArchitectureConcepts/SystemLayers.md) <br>
[Clean Architecture e SOLID](docs/ArchitectureConcepts/GoodDevelopmentPractices.md) <br>
[Injeção de Dependência](docs/ArchitectureConcepts/DependencyInjection.md) <br>
[Versionamento de APIs](docs/ArchitectureConcepts/API-Versioning.md) <br>
[Padrões de Projetos mais Utilizados no Back-End](docs/ArchitectureConcepts/ProjectPatterns.md) <br>

## Parte 4 - Fundamentos Específicos do .NET
Essa parte se diz respeito aos conceitos básicos que integram o .NET como um todo. Aqui estaremos falando mais sobre o nível técnico de como o Back-End se comporta de forma geral atrás dos panos e iremos realizar recomendações de cada conceito observado aqui. <br>

[.NET Runtime e .NET SDK](docs/DotNetFundamentals/RuntimeAndSDKs.md) <br>
[ASP.NET Core](docs/DotNetFundamentals/ASPNetCore.md) <br>
[Middlewares](docs/DotnetFundamentals/Middlewares.md) <br>
[Bibliotecas e Frameworks](docs/DotNetFundamentals/LibrariesAndFrameworks.md) <br>
[Controllers e Actions no ASP.NET Core](docs/DotNetFundamentals/ActionsAndControllers.md) <br>
[Configurações e o uso de JSON em Projetos](docs/DotNetFundamentals/ConfigsAndJSON.md) <br>

## Parte 5 - DevOps para Back-End
Essa parte abordará conceitos essenciais de **DevOps** aplicados ao desenvolvimento back-end, desde **_controle de versão_** até **_automação de deploy_**, **_monitoramento_** e **_práticas de segurança_**. O objetivo é apresentar ferramentas e processos que facilitam a entrega contínua e a manutenção de sistemas que estão em produção.

[Introdução ao DevOps](docs/DevOps/DevOpsIntroduction.md) <br>
[Ambientes de Desenvolvimento](docs/DevOps/DevelopmentEnvironments.md) <br>
[Controle de Versão com Git](docs/DevOps/VersionControl-Git.md) <br>
[Integração Contínua (CI)](docs/DevOps/ContinuousIntegration.md) <br>
[Entrega Contínua (CD)](docs/DevOps/ContinuousDelivery.md) <br>
[Containers e Docker](docs/DevOps/Containers-Docker.md) <br>
[Infraestrutura como Código (IaC)](docs/DevOps/InfrastructureAsCode.md) <br>
[Observabilidade e Monitoramento](docs/DevOps/Observability.md) <br>
[Segurança e Gerenciamento de Segredos](docs/DevOps/Security-SecretsManagement.md) <br>
[Gerenciamento de Ambientes](docs/DevOps/EnvironmentManagement.md) <br>
