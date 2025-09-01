# Recapitulação Anterior
Anteriormente falamos sobre outros tipos de modelos arquiteturais que podem ser utilizados para estruturar uma **Web API**. Falamos sobre o **REST**, o **GraphQL** e o **gRPC**,
modelos esses que são os mais utilizados hoje em dia para estruturar as **APIs** das nossas aplicações. Também mencionamos o funcionamento e utilidade de cada um desses modelos,
bem como suas vantagens e casos de uso.

# Introdução
Agora iremos abordar um assunto **essencial** no desenvolvimento **Back-End**, o conceito de **_roteamento_** e **_endpoints_**. Provavelmente você já deve conhecer algum desses conceitos,
porém eu irei falar sobre eles porque é um assunto bem importante nas aplicações web hoje em dia. **Roteamento** e **endpoints** estão totalmente ligados com os conceitos de **URL** e **URI**,
conceitos esses que serão explicados logo abaixo caso você não tenha conhecimento sobre eles.

# URI
O termo **URI** (**U**niform **R**esource **I**dentifier ou "Identificador Uniforme de Recursos") é um conceito que serve para **identificar** um recurso na web (como um arquivo, uma imagem, um documento, etc.).
Essa identificação pode ocorrer de duas maneiras, que são elas: <br>

## URL
O termo **URL (`U`niform `R`esource `L`ocator)** diz **qual** é o recurso e **como** acessá-lo.

### Estrutura de Uma URL
A estrutura geral de uma **URL** é composta por oito partes definidas pelo **RFC 3986**, que são elas: <br>
- **Protocolo (Scheme):** Define o protocolo utilizado pela **URL**. Por exemplo: "`https`", "`http`", "`ftp`", etc.
- **Usuário e Senha (Opcional):** Credenciais de acesso em alguns serviços. Por exemplo: "`usuario:senha@`". (Hoje em dia quase não se utiliza por questões de segurança.)
- **Subdomínio:** Parte que vem antes do domínio. Por exemplo: "`www.`" (o mais comum), "`blog.`", "`api.`", "`loja.`".
- **Domínio:** Nome principal do site. Por exemplo: "`google.com`", "`github.com`", "`steam.com`".
- **Porta (Opcional):** Indica a porta de comunicação. Por exemplo: "`:443`" para HTTPS, "`:80`" para HTTP, "`:8080`" para aplicações locais.
- **Caminho (Path):** Endereço do recurso no servidor. Por exemplo: "`/usuarios/3`", "`/produtos/1`", "`/livros/23`".
- **Query String (Opcional):** Conjunto de parâmetros passados na URL após o "`?`". Por exemplo: "`?page=2&order=desc`", "`?id=15&filter=active`".
- **Fragmento (Opcional):** Indica uma âncora ou seção dentro da página, após o "`#`". Por exemplo: "`#sessao2`", "`#comentarios`".

## URN
O termo **URN (`U`niform `R`esource `N`ame)** é um identificador que diz apenas **qual** é o recurso mas não explica **onde** está ou **como** acessá-lo.

### Estrutura de uma URN
A estrutura geral de uma **URN** é composta por três partes principais: <br>

- **Prefixo "urn":** Parte fixa que indica que se trata de uma **URN**. Por exemplo: "`urn`".  
- **Namespace Identifier (NID):** Identifica o espaço de nomes responsável pelo recurso. Por exemplo: "`isbn`", "`uuid`", "`ietf`", "`oid`".  
- **Namespace Specific String (NSS):** É a parte específica dentro daquele namespace que identifica o recurso de forma única.  

Exemplo de **URN:** <br>

---
```
  urn:isbn:9783161484100
```
---

Explicação do exemplo: <br>

- `urn`: Prefixo  
- `isbn`: Namespace  
- `9783161484100`: Identificador específico  <br>

> **OBS:** O **URN** não faz parte da **URL** porém ele faz parte da **URI**. Os termos **URL** e **URN** são **tipos de identificadores** para a **URI** e estão presentes em cenários **diferentes**. <br>
  
# Roteamento
O **roteamento** é a ação de mapear as **URLs** para determinados recursos existentes em um servidor. O roteamento define a estrutura de uma **URL** e como ela vai apontar para um recurso específico em uma
aplicação. O roteamento pode levar em conta três fatores principais, que são eles: <br>

- **Verbo HTTP:** Qual verbo **HTTP** será usado em uma **URL**. Por exemplo: **`HTTP PUT`**, **`HTTP DELETE`**, **`HTTP PATCH`**, etc.
- **Caminho do Recurso na URL:** É preciso pensar em como ficaria o caminho para determinado recurso em uma **URL**. Por exemplo:  "`/usuarios/3`", "`/produtos/1`", "`/livros/23`", etc.
- **Parâmetros:** Os parâmetros são os valores de um determinado recurso ou um identificador único. Por exemplo: Se existir um caminho para "`livros/23`", o parâmetro do recurso "`livros`" seria "`23`". <br>

> **OBS:** Uma das diretrizes do **REST** é definir **padrões** para as _rotas_, ou seja, definir padrão para as **URLs** que apontam para determinado recurso em um servidor.
Então seguir essa regra do **REST** por si só já implica no conceito de roteamento. <br>

# Explicação dos Termos

- **URI:** É um identificador genérico de recursos na web. O **URI** pode indicar onde um recurso está localizado ou qual é o recurso, sem necessariamente dizer como acessá-lo.
- **URL:** É um tipo de **URI** que indica o **local** do recurso e **como** acessá-lo. A **URL** pode conter informações como **protocolo**, **domínio**, **caminho**, **parâmetros**, **fragmentos** e etc.
- **URN:** É um tipo de **URI** que identifica unicamente um recurso, mas sem informar como acessá-lo.
- **Endpoints:** São os pontos finais de acesso da **API**, responsáveis por processar as requisições. Cada endpoint executa uma ação específica relacionada a um recurso existente no lado do servidor.
- **Rotas (Routes):** São padrões de caminhos que definem **como** a **API** deve tratar as requisições. As rotas servem para direcionar a requisição para o **endpoint** correto.

# Resumo
De forma geral, o conceito de **roteamento** consiste em **mapear** as **URLs** para formar um **endpoint** que aponta para determinada função ou recurso existente em um servidor.
**APIs RESTful** possuem um roteamento padronizado dos recursos, ou seja, essas **APIs** seguem um padrão organizacional dos endpoints que facilita bastante a aplicação como um todo.
Padronizar **URLs** pode ser algo bem simples porém de grande importância nas aplicações web hoje em dia.

# Documentações de Referência

| Conceitos           | Links                                                                                                        |
|---------------------|--------------------------------------------------------------------------------------------------------------|
| Endpoint de API     | [IBM - Endpoint de API](https://www.ibm.com/br-pt/think/topics/api-endpoint)                                 |
| O Que São URLs?     | [HostGator - O Que São URLs?](https://www.hostgator.com.br/blog/url-o-que-e-importancia/)                     |
