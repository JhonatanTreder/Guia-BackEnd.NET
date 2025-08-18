# Recapitulação Anterior
Na parte anterior, vimos como o protocolo **HTTP/HTTPS** funciona dentro da **Web**. Também falamos sobre as certificações **_SSL_** e **_TLS_**, que são 
utilizadas no **HTTP** para oferecer uma camada a mais de _segurança_, dando origem ao **HTTPS**. Além disso, abordamos conceitos como **_JSON_** e, por fim, **_Status Codes_**.
Agora iremos entrar no tópico de **APIs**, que são nada mais nada menos que a forma como o **Front-End** e o **Back-End** se comunicam entre si.

# Introdução
**`Sigla A.P.I:`** A sigla **"API"** vem de _"**A**pplication **P**rogramming **I**nterface"_,
que traduzindo para o português seria algo como _"**I**nterface de **P**rogramação **A**plicada"_. <br>

**`Explicação do Termo:`** O termo **API** se refere a um mecanismo utilizado entre dois ou mais sistemas para a comunicação entre si. Pode imaginar que a **API** é uma "ponte"
entre dois tipos de sistemas. Por exemplo: imagina que você esteja em um restaurante e em determinado momento você pede ao garçom um tipo de comida específica, o garçom por sua vez,
vai levar esse pedido aos cozinheiros informando o que você pediu. Depois que os cozinheiro terminarem o prato, o garçom vai te servir com base no que você pediu. Analisando esse cenário,
podemos encontrar três tipos de "entidades" diferentes para entendermos como isso se encaixaria no _desenvolvimento Web_, que são elas: <br>

- **A pessoa que realizou o pedido:** Essa entidade se trata do _usuário que realizou uma requisição_ (pedido no exemplo do restaurante), que passou por algum tipo de **API**,
chegou no **servidor** e por fim recebeu uma _resposta_. Seja essa resposta um redirecionamento para alguma página, um login realizado com sucesso e etc. <br>

- **O garçom que atendeu a pessoa:** Essa entidade se refere _à API que recebeu a requisição_ (o garçom que anotou o pedido). Ela é a responsável por **intermediar a comunicação**
entre o usuário (`Front-End`, `aplicativo` ou `cliente que fez o pedido`) e o servidor (cozinha do restaurante). A **API** entende o que foi solicitado, organiza esse pedido para o servidor,
e quando recebe a resposta, devolve ao usuário passando primeiro pelo **Front-End**. <br>

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
Logo abaixo está sendo ilustrado um fluxo simples de como toda esse processo acontece de do lado do **cliente** até o lado do **servidor**
por meio das _requisições_ e _respostas_ que já foram explicadas.

```md
                                                +------------------+
                                                |   Front-End      |
                                                | (Navegador)      |
                                                +------------------+
                                      1)             |        ^           2)
                               HTTP/HTTPS Request -- |        | -- JSON + Status Code
                                                     v        |
                                                +------------------+
                                                |   Back-End       |
                                                | (Servidor/API)   |
                                                +------------------+
```
> Note que primeiramente o **lado do cliente** (Front-End) envia um pedido de requisição para o **lado do servidor** (Back-End), que por consequência é devolvido um objeto **JSON**
junto com o **Status Codes** da operação para o **Front-End**.

## Headers
Headers (ou _cabeçalhos_ em português) é um conjunto de informações que descrevem as _requisições_ e _respostas_. Eles ajudam a definir o que está sendo enviado ou recebido,
como interpretar e até mesmo como se comportar. Exsitem vários, porém o que iremos abordar aqui serão os **Request Headers** (cabeçalhos de _requisições_ enviados pelo cliente)
e sobre os **Respose Headers** (cabeçalhos de _respostas_ enviados pelo servidor). <br>

### Request Headers
Como já dito acima, os **Requests Headers** fazem parte da _requisição_ que é enviada pelo **lado do cliente**. A estrutura de um **Request Header** é parecida com a de um **Response Header**,
porém o que diferencia entre cada um é **_o que_** está sendo informado. <br>

- **Estrutura de um Request Header**: A estrutu
