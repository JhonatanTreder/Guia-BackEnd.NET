# Recapitulação Anterior
Na parte anterior, vimos como o protocolo **HTTP/HTTPS** funciona dentro da **Web**. Também falamos sobre as certificações **_SSL_** e **_TLS_**, que são 
utilizadas no **HTTP** para oferecer uma camada a mais de _segurança_, dando origem ao **HTTPS**. Além disso, abordamos conceitos como **_JSON_** e, por fim, **_Status Codes_**.
Agora iremos entrar no tópico de **APIs**, que são nada mais nada menos que a forma como o **Front-End** e o **Back-End** se comunicam entre si.

# Introdução
**`Sigla A.P.I:`** A sigla **"API"** vem de _"**A**pplication **P**rogramming **I**nterface"_,
que traduzindo para o português seria algo como _"**I**nterface de **P**rogramação de **A**plicações"_. <br>

**`Explicação do Termo:`** O termo **API** se refere a um mecanismo utilizado entre dois ou mais sistemas para a comunicação entre si. Pode imaginar que a **API** é uma "ponte"
entre dois tipos de sistemas. Por exemplo: imagina que você esteja em um restaurante e em determinado momento você pede ao garçom um tipo de comida específica, o garçom por sua vez,
vai levar esse pedido aos cozinheiros informando o que você pediu. Depois que os cozinheiros terminarem o prato, o garçom vai te servir com base no que você pediu. Analisando esse cenário, podemos encontrar três tipos de "entidades" diferentes para entendermos como isso se encaixaria no _desenvolvimento Web_, que são elas: <br>

- **A pessoa que realizou o pedido:** Essa entidade se trata do _usuário que realizou uma requisição_ (pedido no exemplo do restaurante), que passou por algum tipo de **API**,
chegou no **servidor** e por fim recebeu uma _resposta_. Seja essa resposta um redirecionamento para alguma página, um login realizado com sucesso, etc. <br>

- **O garçom que atendeu a pessoa:** Essa entidade se refere _à API que recebeu a requisição_ (o garçom que anotou o pedido). Ela é a responsável por **intermediar a comunicação**
entre o usuário (`Front-End`, `aplicativo` ou `cliente que fez o pedido`) e o servidor (cozinha do restaurante). A **API** entende o que foi solicitado, organiza esse pedido para o servidor, e quando recebe a resposta, devolve ao usuário passando primeiro pelo **Front-End**. <br>

- **Os cozinheiros que prepararam o prato:** Essa entidade representa o servidor/Back-End, que é o lugar onde a lógica de negócios realmente acontece.
Ele recebe a instrução da **API**, processa o pedido (seja `buscar um dado no banco`, `autenticar um usuário`, ou` aplicar alguma regra de negócio`) e prepara a resposta.
Essa resposta, será enviada pela **API** para o usuário. <br>

<hr>

> _"Front-End? Back-End?"_ <br>
> ---
> **`Front-End:`** Responsável por tratar toda a parte da experiência do usuário no lado do _cliente_. <br>
> **`Back-End:`** Responsável por tratar toda a parte da regra de negócio gerenciada no lado do _servidor_.

<hr>

## Fluxo de Requisição
Logo abaixo está sendo ilustrado um fluxo bem simples de como todo esse processo geralmente acontece no lado do **cliente** até o lado do **servidor**
por meio das _requisições_ e _respostas_ que já foram explicadas.

```md
                                                +------------------+
                                                |    Front-End     |
                                                |   (Navegador)    |
                                                +------------------+
                                      1)             |        ^           2)
                               HTTP/HTTPS Request -- |        | -- JSON + Status Code
                                                     v        |
                                                +------------------+
                                                |    Back-End      |
                                                |  (Servidor/API)  |
                                                +------------------+
```
> Note que primeiramente o **lado do cliente** (Front-End) envia um pedido de requisição para o **lado do servidor** (Back-End), que por consequência é devolvido um objeto **JSON**
junto com o **Status Codes** da operação para o **Front-End**.

## Estrutura de Requisições e Respostas
As estruturas que compõem mensagens de _requisição_ e de _resposta_ são parecidas, mas com diferenças entre si. Primeiramente, observe esses dois tipos de mensagens:<br>

<hr>

1) Mensagem de uma **_Requisição POST_** enviada para o servidor

```md
POST /users HTTP/1.1
User-Agent: curl/7.16.3
Host: www.site-example.com
Accept-Language: en-us
Connection: Keep-Alive
Content-Type: application/json

{
  "firstName": "Matheus",
  "lastName": "Sampaio",
  "email": "matheussampaio@example.com"
}
```

<hr>

2) Mensagem de **_Resposta com Status Code_** devolvida para o cliente
 
```md
HTTP/1.1 Created
Server: Apache/2.4.1 (Unix)
Date: Mon, 18 Dec 2024 10:25:30 GMT
Content-Length: 88
Content-Type: application/json
Connection: Closed

{
  "message": "User successfully created",
  "user": {
    "id": 101,
    (more data)
  }
}
```

<hr>

A estrutura de ambas mensagens parecem iguais, certo? Porém não são exatamente as mesmas e cada uma define algo único de acordo com 3 partes, que são elas: <br>

1) **Start Line:** Essa parte resume a mensagem em si com uma única diferença, a forma como é escrita de acordo com uma _requisição_ ou _resposta_. <br>
Para uma _requisição_, a **Start Line** especificaria primeiramente o **método HTTP** utilizado, depois o _endpoint_ apontando para algum recurso do servidor e por fim a versão do HTTP. Como nesse caso: <br>

<br>

```bash
 POST /users HTTP/1.1
```

---

Para uma _resposta_ estaria especificando primeiramente a **versão do HTTP** e depois o **Status Code**, como esse caso: <br>

```bash
HTTP/1.1 201 Created
```

<br>

> Note que a **Start Line** em uma _requisição_ define um **método HTTP**, um **endpoint apontando para um recurso** e por fim a **versão do HTTP**.
Por outro lado, a **Start Line** de uma _resposta_ define a **versão do HTTP** e o **Status Code** da operação (como já dito acima). <br> <br>

2) **Headers:** Os **Headers** são um conjunto de informações que definem algumas configurações específicas, como o tipo de conteúdo que será apresentado (**"Content-Type: application/json"** para especificar que a mensagem vai ser tratada como um **JSON**), conexão, host, linguagem aceita, etc. No caso da mensagem de exemplo mostrada lá acima, o header seria este: <br>

```bash
User-Agent: curl/7.16.3
Host: www.site-example.com
Accept-Language: en-us
Connection: Keep-Alive
Content-Type: application/json
```

---

Ou este para a _resposta_ do servidor:

```bash
Server: Apache/2.4.1 (Unix)
Date: Mon, 18 Dec 2024 10:25:30 GMT
Content-Length: 88
Content-Type: application/json
Connection: Closed
```

> Observe que o conjunto de informações presentes em cada **Header** são definidos por **chave-valor**, ou seja, são bem semelhantes a estrutura **JSON**.
Mas não se engane, os **Headers** e **objetos JSON** são completamente diferentes (apesar de compartilharem o mesmo conceito de **chave-valor**).

<br>

3) **Body:** Um **Body** não é nada mais nada menos que um conjunto de informações enviadas com base no tipo de _requisição_ ou _resposta_ gerada por um dos dois lados (**cliente** ou **servidor**). Esse conjunto de informações pode estar em diversos formatos, porém os formatos mais utilizados são **JSON** e **XML** (**E**xtensive **M**arkup **L**anguage). Observe esses dois exemplos de body das mensagens HTTP mostradas lá em cima: <br>

Body da _requisição_ <br>

```json
{
  "firstName": "Matheus",
  "lastName": "Sampaio",
  "email": "matheussampaio@example.com"
}
```

---

Agora veja o body da _resposta_ devolvida pelo servidor <br>

```json
{
  "message": "User successfully created",
  "user": {
    "id": 101,
    "firstName": "Matheus",
    "lastName": "Sampaio",
    "email": "matheussampaio@example.com"
  }
}
```

> **OBS:** O **JSON** é o formato mais utilizado para descrever um body nas _requisições_ e _respostas_, porém pode ser utilizado **XML**, **HTML**,
entre outras (mas o **JSON** é o mais utiliazado atualmente). Um outro ponto que merece ser destacado, é que o **envio de um body** pode ser opcional dependendo do **método HTTP** utilizado e/ou do **Status Code** devolvido. **Métodos HTTP** como **GET**, **DELETE** e até mesmo o **HEAD** não possuem body. E **Status Code** como **204 No Content** e **304 Not Modified** também não possuem body. <br>

# Resumo

- **API**: Interface que permite comunicação entre sistemas, funcionando como um "garçom" entre **Front-End** e **Back-End**.  
- **Front-End**: Responsável pela interface e experiência do usuário (lado cliente).  
- **Back-End**: Responsável pela lógica de negócio e processamento de dados (lado servidor).  
- **Fluxo de Requisição**: O cliente envia uma _requisição_ HTTP/HTTPS, depois o servidor processa e por fim retorna uma _resposta_ com **Status Code** e **Body**.  
- **Mensagens HTTP** Têm três partes principais:
1. **Start Line**: Método, endpoint e versão (_requisição_) ou versão e status code (_resposta_).  
2. **Headers**: Informações adicionais (ex.: `Content-Type`, `Connection`, `Host`).  
3. **Body**: Conteúdo enviado ou recebido (opcional), geralmente em **JSON**, mas pode ser **XML**, **HTML**, ou outros formatos.
 
- **Body opcional**:
  - Requisições: GET, DELETE, HEAD → normalmente não têm body.  
  - Respostas: 204 No Content, 304 Not Modified → não possuem body. <br>
  
- **JSON** É o formato mais comum, mas outros tipos podem ser utilizados conforme a necessidade. <br>

# Documentações de Referência

| Conceitos               | Links                                                                 |
|-------------------------|----------------------------------------------------------------------|
| API                     | [AWS - O que é API](https://aws.amazon.com/pt/what-is/api/)          |
| Front-End e Back-End    | [AWS - Diferença entre Front-End e Back-End](https://aws.amazon.com/pt/compare/the-difference-between-frontend-and-backend/) |
| Métodos HTTP            | [MDN - Métodos HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Reference/Methods) |
| JSON                    | [MDN - JSON](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/JSON) |
| XML                     | [AWS - O que é XML](https://aws.amazon.com/pt/what-is/xml/)          |
| HTML                    | [MDN - HTML](https://developer.mozilla.org/pt-BR/docs/Web/HTML)      |
| Mensagens HTTP          | [MDN - Mensagens HTTP](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Guides/Messages) |
| Headers                 | [MDN - Elemento Header](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Reference/Elements/header) |
