# Introdução
Na parte anterior, explicamos que o **cliente** e **servidor** se comunicam através de _requisições_ e _respostas_.
Essa comunicação pode acontecer por meio de vários protocolos, porém o mais utilizado pela **Web** e a maior parte das plataformas existentes é o **HTTP/HTTPS**. <br>

**`HTTP/HTTPS Disclaimer`:** A sigla **HTTP** vem de **H**yper**t**ext **T**ransfer **P**rotocol, que é um termo explicativo referente a _transmissão de documentos de hipermídia_,
como o HTML por exemplo. A sigla **HTTPS** é praticamente a mesma coisa, mas com um porém: ela adiciona uma camada de **segurança** ao protocolo, ficando 
**H**yper**t**ext **T**ransfer **P**rotocol **S**ecure. Essa camada de segurança adicionada geralmente se utiliza **SSL** ou **TLS** para criptografar toda a comunicação
entre um cliente e um servidor. "_Então quer dizer que utilizar HTTPS é melhor?_" Sim, é melhor por justamente utilizar essa camada a mais de segurança,
possibilitando assim um _envio_ e _recebimento_ de dados mais seguros. <br> <br>

> **OBS:** Irei abordar de uma forma mais aprofundada o conceito de _criptografia_ mais adiante, então não se preocupe muito com esse termo agora.<br>

# O que é o **`TLS`** e o **`SSL`?**
**`Sigla TLS:` TLS** se refere a **T**ransport **L**ayer **S**ecurity (_"Segurança da Camada de Transporte"_ em Português). <br>
**`Sigla SSL:` SSL** se refere a **S**ecure **S**ocket **L**ayer (_"Camada de Soquete Segura"_ em Português). <br> <br>

**Explicação:** Esses dois protocolos são utilizados para criptografar os dados, oferecer uma camada de segurança criptográfica,
disponibilizar integridade e/ou confidencialidade nos dados e pode ser usado também para prover autenticação. <br> <br>

## Diferença?

> **_"TLS e SSL são dois certificados que aplicam protocolos de segurança baseados em criptografia de informações em sites.
Essa é uma definição que não muda, mas, ainda assim, gera muita confusão em usuários que não têm conhecimento técnico sobre o tema.
A realidade é que há diferenças bem pequenas entre eles, mas que vale a pena destacar.
O SSL foi o primeiro certificado a usar esse tipo de protocolo de segurança, revolucionando os parâmetros de proteção no acesso a sites.
No entanto, em determinado momento a sua capacidade de cumprir com a criptografia de informações foi testada e houve o entendimento de que 
era necessário desenvolver a tecnologia. Foi assim que o TLS passou a ser o certificado principal, praticamente substituindo o SSL, já que
ele é um recurso mais avançado e mais seguro. Portanto, há sim diferenças entre SSL e TLS, que, apesar de pequenas, são essenciais, uma vez
que o TLS é um protocolo mais eficaz."_** <br>

## Nomenclatura

> **_"Muitos usuários podem se sentir em dúvida quando entendem que o TLS é pouco falado, mas ainda assim ele é um protocolo mais seguro que o SSL.
Há uma questão fundamental nesse ponto: a maioria dos certificados utilizados hoje são o TLS, no entanto, eles ainda continuam sendo chamados 
de SSL. Tecnicamente, o TLS é encarado como uma evolução do SSL, de modo que é comum que seu nome original não seja usado com tanta frequência. 
Portanto, um site que tem um certificado SSL não é necessariamente inseguro, já que, na verdade, é provável que ele tenha um TLS e use a nomenclatura antiga."_** <br>

**Fonte Textual:** _https://pingback.com/br/resources/tls-ssl/_ <br>

# Funcionamento da Comunicação na Web
As _requisições_ e _respostas_ se comportam através dos **métodos HTTP/HTTPS**. Os métodos HTTPs, por sua vez, são aqueles que definem qual é o tipo
da _requisição_ para o servidor. Por exemplo: Em uma página de registro, nós podemos enviar uma _requisição_ para o servidor de acordo com o formulário
de registro que preenchemos (Nome, Email, Senha, etc). Esse formulário seria enviado para o servidor por meio de uma **_requisição POST_** (POST Request em Inglês),
e o servidor iria devolver para o cliente uma _resposta_. Essa resposta seria tratada primeiramente no **Front-End** de acordo com o **_Status Codes_** recebido da resposta.
o **Front-End**, por sua vez, poderia permitir o cadastro do usuário, avisar que o Email especificado já está sendo utilizado ou até mesmo redirecionar o usuário para uma outra página.

## "Métodos HTTPs??" "Status Codes??"
### Métodos HTTPs

**Explicação:** São aqueles que explicam para o servidor qual é o tipo da _requisição_ que está sendo enviada pelo cliente. Existem vários métodos HTTPs,
porém os mais utilizados são eles: **`HTTP POST`**, **`HTTP GET`**, **`HTTP PUT`**, **`HTTP PATCH`** e **`HTTP DELETE`** <br>

**Caso de Usos** <br>

**`HTTP POST:`** Utilizado para **criar** algum tipo de recurso em um servidor. Esse método é utilizado bastante em criação de contas (telas de registro),
quando uma pessoa publica um comentário, quando alguém faz um pedido de algum item e etc. <br>

**`HTTP GET:`** Utilizado para **buscar** por algum recurso específico em um servidor. Esse método é amplamente utilizado para buscar detalhes sobre determinado produto,
buscas por itens em algum catálogo, pesquisar sobre certa coisa, quando um usuário clica no perfil de um outro usuário, etc. <br>

**`HTTP PUT:`** Utilizado para **atualizar** alguma coisa no lado do servidor. Esse método é utilizado quando o usuário atualiza informações do seu perfil,
atualiza uma mensagem em uma rede social, etc.

**`HTTP PATCH:`** Também é utilizado para **atualizar** algum recurso no servidor, porém ele é utilizado para realizar _atualizações parciais_ de um determinado recurso,
ou seja, ele é encontrado quando alguém atualiza apenas o nome de usuário e não o perfil todo (foto de perfil, nome de usuário, email, senha, etc.). <br>

**`HTTP DELETE:`** Por fim, esse método HTTPs serve para **deletar** determinado recurso no servidor. É bastante utilizado quando o usuário decide excluir uma conta,
excluir um comentário, remover a interação sobre uma publicação, etc. <br>

> **ATENÇÃO:** Por mais que os métodos HTTPs começam com _`HTTP`_ e não _`HTTPS`_ isso é apenas uma nomenclatura que serve nos dois tipos de protocolos. <br>

### Status Codes

**Expicação:** Os **_Status Codes_** (ou _"código de status"_ em português) fazem parte da _resposta_ que o servidor devolve para o cliente. Essa resposta como foi
explicada anteriormente, primeiramente passa pelo **Front-End**, depois o **Front-End** trata o **_Status Code_** recebido pelo servidor e por fim realiza algum tipo
de ação no lado do cliente. Os **_Status Codes_** servem para especificar se uma _requisição_ foi **recebida**, **analisada**, **processada** e **devolvida** corretamente de
acordo com a ação do usuário. O servidor pode retornar tipos de **_Status Code_** diferentes em cada requisição (dependendo do cenário é claro), como por exemplo: **`200 OK`**,
**`404 NotFound`**, **`500 Internal Server Error`**, e assim por diante. <br>

> **OBS:** O servidor não retorna apenas um _Status Code_ nas respostas das requisições, o servidor retorna um objeto **_JSON_** (**J**ava**S**cript **O**bject **N**otation)
> que **CONTÉM** o _Status Code_ do servidor. Por fim, o **JSON** é um padrão de comunicação amplamente utilizado entre o **Front-End** e o **Back-End** na tratativa das _requisições_
>  e _respostas_. <br> <br>

**Hierarquia dos Status Codes** <br> <br>

---

**`Família 2xx:`** A família _"200"_ explica que a _requisição_ foi **recebida**, **analisada**, **processada** e **devolvida**
corretamente para o usuário (passando primeiramente pelo **Front-End**). <br> <br>

**200 OK:** Esse **Status Code** explica que a _requisição_ seguiu o seu fluxo normal e tudo ocorreu conforme o esperado. Geralmente esse **Status Code** possui um _body_, ou seja,
ele contém um objeto **_JSON_** na _resposta_ do servidor para o **Front-End**

**201 Created:** Esse **Status Code** indica que a requisição resultou na **criação de um recurso** no servidor. Geralmente é retornado após uma requisição **POST** bem-sucedida.  
Exemplo: quando um usuário cria uma conta ou quando um produto é cadastrado em um sistema de e-commerce.  

**204 No Content:** Esse **Status Code** informa que a requisição foi processada corretamente, mas o servidor **não possui conteúdo** para retornar.  
Exemplo: quando um recurso é excluído com sucesso através de um **DELETE**.  

---

**`Família 3xx:`** A família _"300"_ representa **redirecionamentos**. Isso significa que o cliente precisa realizar outra ação para obter o recurso desejado.  

**301 Moved Permanently:** O recurso solicitado foi **movido permanentemente** para outra URL. O cliente deve atualizar o link.  
Exemplo: quando um site migra de `http://` para `https://` e precisa redirecionar permanentemente os acessos.  

**302 Found:** Indica que o recurso foi encontrado, mas está **temporariamente em outra URL**.  
Exemplo: redirecionamentos temporários em campanhas de marketing digital.  

**304 Not Modified:** Esse código é retornado quando o recurso **não foi modificado** desde a última vez que foi requisitado.  
Exemplo: utilizado em **cache** para evitar transferência desnecessária de dados.  

---

**`Família 4xx:`** A família _"400"_ representa **erros do cliente**, ou seja, o problema ocorreu na requisição enviada.  

**400 Bad Request:** O servidor não conseguiu entender a requisição devido a **sintaxe inválida**.  
Exemplo: quando o cliente envia um JSON malformado.  

**401 Unauthorized:** Indica que a requisição **não foi autenticada**. Geralmente é usado quando o usuário não está logado ou o token JWT é inválido.  

**403 Forbidden:** O servidor entendeu a requisição, mas o cliente **não possui permissão** para acessar o recurso.  
Exemplo: tentar acessar uma área administrativa sem ser administrador.  

**404 Not Found:** O servidor não conseguiu encontrar o recurso solicitado.  
Exemplo: acessar uma URL inexistente como `/api/produtos/999`.  

**409 Conflict:** Indica que houve um **conflito no processamento** da requisição.  
Exemplo: tentar cadastrar um usuário com um e-mail já existente.  

**422 Unprocessable Entity:** O servidor entendeu a requisição, mas os dados fornecidos são **inválidos** ou não podem ser processados.  
Exemplo: tentar registrar um usuário sem fornecer todos os campos obrigatórios.  

---

**`Família 5xx:`** A família _"500"_ representa **erros no servidor**, ou seja, a falha aconteceu do lado do servidor e não do cliente.  

**500 Internal Server Error:** Um erro genérico que indica que algo deu errado no servidor.  
Exemplo: uma exceção não tratada na aplicação.  

**502 Bad Gateway:** O servidor, atuando como **gateway ou proxy**, recebeu uma resposta inválida de outro servidor.  
Exemplo: quando um servidor intermediário não consegue processar corretamente a requisição.  

**503 Service Unavailable:** O servidor está **indisponível temporariamente** para processar a requisição.  
Exemplo: durante manutenções ou quando há sobrecarga de tráfego.  

**504 Gateway Timeout:** O servidor, atuando como **gateway ou proxy**, não recebeu resposta a tempo de outro servidor.  
Exemplo: quando o servidor **upstream** demora demais para responder.

---

# Resumo dos Status Codes
- **2xx: Sucesso** (requisição processada corretamente).  
- **3xx: Redirecionamento** (o cliente precisa tomar outra ação).  
- **4xx: Erro do cliente** (requisição inválida ou não permitida).  
- **5xx: Erro do servidor** (falha na aplicação ou infraestrutura).  

> Em resumo: os **Status Codes** ajudam o cliente a entender o que aconteceu com sua requisição e como reagir a ela.
> São fundamentais para a comunicação entre o **Front-End** e o **Back-End**.

# Resumo Geral

Como mencionado anteriormente, as _requisições_ e _respostas_ são a base da comunicação entre **cliente** e **servidor** na Web.  
Esse processo acontece principalmente através dos protocolos **HTTP** e **HTTPS**. O HTTPS, por sua vez, adiciona uma camada extra de segurança utilizando **TLS/SSL**, que garantem **confidencialidade**, **integridade** e **autenticação** dos dados trafegados.  

Para que essa comunicação faça sentido, utilizamos os **métodos HTTPs**, que indicam ao servidor a intenção da requisição:  
- **POST:** Criar recursos (ex: criar conta, enviar formulário).  
- **GET:** Buscar informações (ex: consultar produtos, visualizar perfis).  
- **PUT/PATCH:** Atualizar recursos (ex: editar perfil, alterar dados específicos).  
- **DELETE:** Excluir recursos (ex: deletar conta, apagar comentário).  

Após o servidor processar a requisição, ele responde ao cliente com um **Status Code**,
que indica o resultado da operação, que no caso esses códigos são divididos em famílias:  

- **2xx: Sucesso** (requisição concluída corretamente).  
- **3xx: Redirecionamento** (nova ação necessária).  
- **4xx: Erro do cliente** (requisição inválida ou não autorizada).  
- **5xx: Erro do servidor** (falha na aplicação ou infraestrutura).  

Por fim, além do **Status Code**, o servidor normalmente retorna um objeto **JSON**,
que é amplamente utilizado para transportar dados entre **Front-End** e **Back-End**,
facilitando a interpretação e o tratamento das respostas no lado do cliente.

# Documentações de Referência

| Conceitos              | Links                                                                 |
|-------------------------|----------------------------------------------------------------------|
| **HTTP/HTTPS**          | [AWS - Diferença entre HTTP e HTTPS](https://aws.amazon.com/pt/compare/the-difference-between-https-and-http/) |
| **Requisições e Respostas** | [DevMedia - HTTP: Requisição e Resposta](https://www.devmedia.com.br/http-requisicao-e-resposta/41217) |
| **TLS/SSL**             | [AWS - Diferença entre SSL e TLS](https://aws.amazon.com/pt/compare/the-difference-between-ssl-and-tls/) |
| **Métodos HTTPs**       | [MDN - Métodos HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Reference/Methods) |
| **JSON**                | [MDN - JSON](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/JSON) |
| **Status Codes**        | [MDN - Status HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Reference/Status) |
