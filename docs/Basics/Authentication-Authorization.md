# Recapitulação Anterior
Na parte anterior, abordamos o assunto de **banco de dados**, que resumidamente é um mecanismo para **armazenamento** e **gerenciamento** de dados hoje em dia.
Os bancos de dados atualmente são divididos em vários tipos, mas os principais entre eles são os **bancos relacionais** e os **bancos não-relacionais**. Um **banco relacional**
é aquele que os dados podem ser relacionados entre si, com o uso de tabelas (**linhas** e **colunas**) e geralmente esses bancos utilizam o **SQL** (**S**tructured **Q**uery **L**anguage)
para realizar consultas aos dados. Por outro lado, um **banco não-relacional** é aquele que não utilizam o modelo de tabelas (como no banco de dados relacional) e podem utilizar o método **chave-valor**
para o aramazenamento das informações, tendo como consequência um armazenamento mais otimizado.

# Introdução
Nessa parte, iremos tratar sobre o assunto de **autenticação** e **autorização**, que são dois assuntos extremamente importantes, principalmente em diversos tipos de aplicações hoje em dia.
Sendo direto ao ponto, o termo **"autenticação"** diz **"quem você é"** enquanto a **autorização** diz o **"o que você pode fazer"** em determinado sitema, plataforma ou aplicação.
Um usuário pode **estar autenticado**, ou seja, o sistema **sabe quem ele é**, mas ainda assim pode **não ter autorização** para acessar um recurso específico.
Por outro lado, um **usuário autorizado** precisa **obrigatoriamente estar autenticado primeiro**, pois não é possível autorizar alguém **sem saber quem ele é**.

## Autenticação
Autenticação é o processo de **confirmar a identidade** de um **usuário** ou **sistema**, esse processo garante que o sistema saiba quem está tentando acessar e toma uma certa atitude em relação a isso.
Esse processo pode ocorrer de várias maneiras, tais como:

- **JWT (JSON Web Token):** Muito usado em **APIs**, gera um token após o login que comprova a identidade do usuário.  
- **OAuth2:** Protocolo usado principalmente para permitir acesso seguro a recursos de terceiros. Por exemplo,
encontramos muito esse tipo de autenticação em cenários onde aparece aquela opção de “Entrar com Google”.  
- **OpenID Connect:** Extensão do **OAuth2** voltada especificamente para autenticação de usuários.  
- **API Key:** Chave única usada geralmente para autenticar **sistemas** ou **serviços**.  
- **Cookies e Sessões:** Abordagem tradicional em aplicações web.  
- **MFA (Multi-Factor Authentication):** Autenticação em mais de um fator, aumentando a segurança.  

Cada abordagem tem seus prós e contras. A escolha depende do **contexto** da aplicação e das necessidades de segurança que o sistema exige. 

## Autorização
Autorização é o processo de **definir** e **controlar** o acesso a determinados recursos com base no tipo de usuário ou em suas permissões.
Esse processo determina o que o usuário **pode** ou **não** fazer dentro de uma aplicação ou sistema. Por exemplo, em um sistema de biblioteca,
um **usuário comum** pode estar autorizado apenas a **consultar livros** e **pedir empréstimos**, por outro lado um **bibliotecário** (administrador)
pode estar autorizado a **gerenciar o acervo**, **aplicar multas** ou **controlar os empréstimos**. A autorização é exatamente isso,
ela é aplicada para definir o que o usuário pode fazer logo após se **autenticar** em um sistema.

## Exemplo de Autenticação e Autorização com JWT
Mais adiante desse guia, eu irei explicar mais detalhadamente como aplicar outros tipos de **autenticação** em uma aplicação. Por enquanto, eu irei utilizar apenas
o **JWT (JSON Web Token)** como exemplo de **autenticação/autorização**.

### JWT - O que é?
Como já foi explicado anteriormente, o **JWT** é uma forma de você **autenticar o usuário** por meio de **Tokens** gerados quando o usuário realiza um login com sucesso.
Esse token gerado vai conter informações que serão utilizadas para definir **o que o usuário pode fazer**.

### JWT - Estrutura
A estrutura de um **Token JWT** é formada por três partes, que são elas: <br>
- **Header:** Contém o tipo de token (**JWT**) e o algoritmo de criptografia utilizado, no caso seria **HMAC SHA256** ou **RSA SHA256**.
Essa parte é codificada em **Base64Url** e assim é formado a primeira parte do token.
- **Paylaod:** O **Payload** contém um _conjunto de claims_ (dados) relacionadas a aquele usuário em específico. Essas claims são atribuidas
ao **Token JWT** para definir informações específicas do usuário. A baixo segue alguns exemplos de claims:

  ---
  **Claims Padrões:** Essas claims geralmente são as mais utilizadas para definir informações importantes na hora de criar o **payload** do token.
   > - **`iss`:** **Issuer** (quem emitiu o token).
   > - **`sub`:** **Subject** (quem é o dono do token. No caso o **usuário**).
   > - **`aud`:** **Audience** (quem deve usar esse token. Por exemplo, a **API** ou algum outro sistema).
   > - **`exp`:** **Expiration Time** (quando o token expira).
   > - **`nbf`:** **Not Before** (momento antes do qual o **JWT** não deve ser usado).
   > - **`iat`:** **Issued At** (quando o token foi emitido).
   > - **`jti`:** **JWT ID** (identificador único do token).
  ---

  ---
  **Claims Customizadas:** As claims customizadas são utilizadas em sua aplicação como informações complementares para especificar o tipo de usuário com mais detalhes.
   > - **`name`:** Nome do usuário.
   > - **`email`:** E-mail do usuário.
   > - **`role`:** Função/papél do usuário no sistema. Por exemplo: **"admin"** ou **"user"**.
   > - **`permissions`:** Lista de permissões específicas.
  ---

- **Signature:** A **Signature** (ou **Assinatura** em português) é utilizada para validar o token utilizando uma **chave secreta**.
Para gerar a assinatura, precisamos do **Header** e do **Payload**, codificando-os em **Base64** e em seguida assinamos utilizando o algoritmo específico imposto no **Header**.

   **Exemplo de Assinatura:** Exemplo ilustrativo utilizando o algoritmo **HMAC SHA256**.
    ```
      HMACSHA256(
        base64UrlEncode(header) + "." +
        base64UrlEncode(payload),
        secret)
    ```

### JWT - Explicação de Termos

- **Claims:** Claims basicamente são um conjunto de atributos específicos que definem as informações do usuário para ageração do **Payload** do **Token JWT**.
As claims podem conter **informações padrões** (como quem emitiu o token, quem é o dono do token, quando o token expira, etc.) e **informações customizadas** (como email do usuário, função do usuário, etc.).
- **HMAC SHA256 ou RSA SHA256:** Esses dois termos são **algoritmos de criptografia de dados** que são utilizados para codificar informações (no nosso caso, é utilizado para codificar o **Header**).
- **Base64Url:** **Base64** é um método de codificação (não de criptografia) que transforma dados binários em texto legível (ASCII). É uma variação do Base64 tradicional, usada para **URLs** e **tokens**
(como **JWTs**). O **Base64** normal pode gerar caracteres como `+`, `/` e `=`. Esses caracteres podem causar problemas em **URLs** e **cabeçalhos HTTP** (porque `+` pode ser interpretado como espaço, `/` como separador de diretórios,
`=` como parâmetro de query). Por isso foi criada a versão **Base64Url**, que é segura para **URLs**.

### JWT - Autorização
Quando o usuário realiza um login, é gerado um **Token JWT**. Esse token não serve apenas para prover autenticação (provar **quem o usuário é**),
mas também para autorizar o usuário (definir **o que ele poder fazer** na aplicação). Isso ocorre porque um **Token JWT** contém as **claims**, e as claims podem conter as **roles** (papéis e funções) do usuário.
Possibilitando assim que a aplicação especifique **quais recursos** o usuário terá acesso naquele sistema. Veja este exemplo logo abaixo: <br>

Imagine um sistema de e-commerce com três tipos de usuários. <br>

- **Cliente:** Pode **consultar** produtos e **realizar compras**.
- **Vendedor:** Pode **cadastrar** e **gerenciar seus próprios produtos**.
- **Administrador:** pode acessar **todas as informações**, **suspender contas** e **controlar permissões**.

O token JWT poderia ter um payload parecido como este:

---
```json
  {
    "sub": "1234567890",
    "name": "Maria da Silva",
    "email": "maria@email.com",
    "role": "vendedor",
    "permissions": ["cadastrar_produto", "editar_produto", "ver_vendas"],
    "iat": 1692649190,
    "exp": 1692656390
  }
```
---

Quando a Maria tentar cadastrar um produto, a **API** lê o token, verifica a claim "role": "vendedor" e a permissão "cadastrar_produto",
e autoriza a ação. Se Maria tentasse acessar o painel de administrador, a **API** iria verificar a claim "role": "vendedor", não encontraria
as permissões necessárias e retornaria um erro de acesso negado (no caso uma _resposta_ para o **Front-End** com o **Status Code 403 Forbidden**).

# Resumo
**Autenticação** e **Autorização** são fundamentais para garantir mais segurança a um sistema. Existem várias formas de **prover autenticação** de
um usuário, como o uso de **OAuth2**, **OpenID Connect**, **Cookies/Sessões** e várias outras formas. Foi mostrado um exemplo de autenticação utilizando **Tokens JWT**,
que são utilizados para garantir a segurança e integridade de acesso aos recursos da aplicação. A autenticação é imposta logo depois quando o usuário é validado e ela é
fundamental para definir **quem pode acessar determinado recurso**.

# Documentações de Referências

| Conceitos                      | Links                                                                                                           |
|--------------------------------|-----------------------------------------------------------------------------------------------------------------|
| Autenticação e Autorização     | [Auth0 - Autenticação e Autorização](https://auth0.com/pt/intro-to-iam/authentication-vs-authorization)         |
| OAuth2                         | [Auth0 - O Que é "OAuth2"?](https://auth0.com/pt/intro-to-iam/what-is-oauth-2)                                  |
| OpenID Connect                 | [Auth0 - OpenID Connect](https://auth0.com/pt/intro-to-iam/what-is-openid-connect-oidc)                         |
| API Key                        | [AWS - O Que é "API Key"?](https://aws.amazon.com/pt/what-is/api-key/)                                          |
| JWT                            | [Auth0 - JWT](https://auth0.com/docs/secure/tokens/json-web-tokens)                                             |
| Estrutura JWT                  | [Auth0 - Estrutura JWT](https://auth0.com/docs/secure/tokens/json-web-tokens/json-web-token-structure)          |
| Claims do JWT                  | [Auth0 - Claims do JWT](https://auth0.com/docs/secure/tokens/json-web-tokens/json-web-token-claims)             |
