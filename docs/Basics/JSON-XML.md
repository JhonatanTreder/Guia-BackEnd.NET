# Recapitulação Anterior
na parte anterior, falamos sobre os padrões **REST** e **SOAP** que são utilizados para padronizar a comunicação ou estrutura de uma **Web API**.
Além de tratarmos sobre o comportamento e especificações de ambos os padrões, como formato de mensagens, regras, comportamentos entre ambas, etc. <br>

# Introdução
Nesta seção, vamos explorar em detalhes o funcionamento e especificações do **JSON** e o **XML**, dois formatos amplamente utilizados para a troca de dados entre sistemas hoje em dia.
Abordaremos a estrutura de cada um, seus principais casos de uso e em quais situações é mais adequado utilizar cada formato.

# JSON
Como já observamos até aqui, o **JSON** (**J**ava**S**cript **O**bject **N**otation) é amplamente utilizado na tratativa de _requisições_ e _respostas._
Mas o **JSON** também é bastante utilizado para definir e especificar **configurações** entre sistemas (principalmente em **Web APIs**), armazenar dados
no formato **chave-valor**, entre muitos outros usos. <br>

## Estrutura do JSON
O formato **JSON** é estruturado em conjuntos de **chave-valor**, ou seja, toda chave está ligada a algum valor. Observe esse exemplo abaixo:

---
```json
{
  "nome": "João"
}
```
---

No exemplo acima, o valor `João` está sendo associado a chave `nome`. Essa estrutura se inicia com '`{`', depois uma linha que contém a declaração de uma chave (`"nome":`),
um valor associado a essa chave (`João`) e por fim a estrutura finaliza com '`}`'. <br>

### Uso de Chaves e Colchetes no JSON
- **Chaves:** A estrutura de um **JSON** começa com o abrir de chaves ('`{`') e o fechar da mesma ('`}`'). Entre essas chaves, pode ser definido um conjunto de dados com os seus respectivos valores.
Observe abaixo um exemplo um pouco mais complexo de uma estrutura **JSON**. <br>

---
```json
{
  "produto": {
    "nome": "Celular",
    "preco": 1500
  }
}
```
---

No exemplo acima, é possível notar que existe uma chave chamada `"produto":`. Essa chave, por sua vez contém um valor que não é nada mais nada menos que uma outra _seção_ 
com outros dois conjunto de dados (`"nome":` com o valor **"Celular"** e `"preco":` com o valor **1500**). No **JSON**, é totalmente possível você ter uma chave contendo um
conjunto de _sub-dados_ com o início e fechar de '`{ }`'. Se a gente quiséssemos adicionar mais dados em `"produto":`, podemos apenas colocar uma vírgula e adicionar os novos dados logo em baixo. Observe: <br>

---
```json
{
  "produto": {
    "nome": "Celular",
    "preco": 1500,
    "categoria": "eletrônicos",
    "quantidade": 20
  }
}
```

---
> **ATENÇÃO:** É de grande importância ressaltar que a **declaração de chaves** em um arquivo **JSON** devem serem realizadas sem a adição de caracteres especiais
(com exeção do _traço_ `-` ou do _underline_ `_`), ou seja, é recomendável não fazer isso da mesma forma que não declaramos variáveis em linguagens de programação utilizando `*`, `´`, `^`, `~`, etc.
---

- **Colchetes:** Os colchetes (`[ ]`) no **JSON** são utilizados para definir uma lista (ou _array_) de valores ou de objetos. Isso significa que podemos ter vários itens agrupados dentro de uma mesma chave.
Observe o exemplo abaixo: <br>

---
```json
{
  "frutas": ["banana", "maçã", "uva", "laranja"]
}
```
---

Nesse caso, a chave '`"frutas":` contém uma lista/_array_ de valores de texto. Agora, observe um exemplo um pouco mais detalhado, onde a chave '`"produtos":`'
contém uma lista/_array_ de objetos: <br>

```json
{
  "produtos": [
    {
      "nome": "Celular",
      "preco": 1500
    },
    {
      "nome": "Notebook",
      "preco": 3500
    },
    {
      "nome": "Fone de Ouvido",
      "preco": 200
    }
  ]
}
```

Note que cada definição de objeto começa com '`{`' e termina com '`}`', utilizando a vírgula para separar cada um deles.
Dentro desses objetos, temos cada conjunto de dados com suas respectivas **chaves** e **valores**. <br>

### Tipos de Dados - JSON
O **JSON** fornece suporte a alguns tipos de dados, que são eles:
- **Uma String**: Tipo simples de dado que especifica um conjunto de caracteres em formato de `string`.
- **Um Número:** Esse tipo de dados fornece suporte a vários outros sub-tipos (`inteiro`, `número quebrado`, `negativo`, etc.).
- **Um Objeto:** Esse tipo é adicionado quando abrimos outra seção em um arquivo **JSON**. Por exemplo:
  
  ---
  ```json
    {
      "pessoa": {
        "nome": "Mario",
        "idade": 35,
        "ativo": true,
        "contatos": {
          "email": "mario@email.com",
          "telefone": "1234-5678"
        }
      }
    }
  ```
  ---

- **Um Array:** Esse tipo define uma série de elementos. Por exemplo:

  ---
  ```json
    {
      "marcas": ["Ford", "BMW", "Fiat"]
    }
  ```
  ---

- **Um Booleano:** Esse tipo define apenas dois valores, `true` para verdadeiro e `false` para falso. Por exemplo:

  ---
  ```json
    {
      "ativo": true
    }
  ```
  ---

- **Um Null:** É apenas um valor nulo, ou seja, representa a ausência de um valor ou objeto.

### Resumindo
Podemos resumir que o uso de '`{ }`' no **JSON** se refere a um único conjunto de dados com **chaves** e **valores**. Por outro lado,
o uso de '`[ ]`' se refere a uma lista (ou _array_) que pode conter valores simples ou um conjunto de objetos. Além de que o **JSON** possui alguns **tipos de dados**, que são eles: `string`, `number`, `object`, `array`, `boolean` e `null`. <br>

# Casos de Usos - JSON
O uso de **JSON** pode ser encontrado em diversos lugares, bem como: **Configurações de ambientes**, **armazenamento de dados**,
**envio de dados entre sistemas** e até mesmo **exportação e importação de dados**. Vamos analisar alguns desses casos. <br>

## Configurações de ambientes
Um cenário típico da utilidade do **JSON**, é que ele pode estar presente em **configurações de ambientes**, ou seja, ele pode aparecer
em arquivos que definem um conjunto de comportamentos que determinado sistema deve exercer. Observe abaixo um exemplo de **JSON** nesse cenário em configurações de **APIs**. <br>


- **Arquivo "appsettings.json":** Esse é um exemplo do uso do **JSON** em um arquivo de configuração que eu tenho de uma **API Open Source** aqui no **GitHub.**

---
```json
{
  "ConnectionStrings": {
    "LocalConnection": "Server=localhost;DataBase=LibraryDB;Trusted_Connection=True;TrustServerCertificate=True;"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "JWT": {
    "ValidAudience": "http://localhost:7221",
    "ValidIssuer": "http://localhost:7221",
    "SecretKey": "1b12n36#1729ff8*bbns626935!19v@bha6",
    "TokenValidityInMinutes": "30",
    "RefreshTokenValidityInMinutes": "60"
  },
  "AllowedHosts": "*"
}
```
---

## Configurações do Front-End ou Aplicativos
O **JSON** pode ser bastante utilizado para definir e especificar configurações do **Front-End**, como URLs de APIs, temas, preferências de usuários, etc. Por exemplo: <br>

---
```json
{
  "theme": "dark",
  "language": "pt-BR",
  "apiBaseUrl": "http://localhost:7221/api"
}
```
---

> Aqui o **JSON** está definindo o tema, o idioma e o _endpoint_ base para a chamada de **API** no **Front-End**.
---

## Armazenamento de Dados Temporários ou Persistentes
Uma outra utilidade do **JSON** consiste no armazenamento de dados nas aplicações para salvar dados nas aplciações. Veja o exemplo abaixo: <br>

---
```json
{
  "usuarios": [
    { "id": 1, "nome": "João", "email": "joao@example.com" },
    { "id": 2, "nome": "Maria", "email": "maria@example.com" }
  ]
}
```
---

> Nesse exemplo, o **JSON** está sendo utilizado para armazenar dados de dois usuários.
---

## Troca de Mensagens Entre Sistemas
**JSON** é muito utilizado para comunicação entre sistemas, principalmente em **APIs RESTful**, onde dados de _requisições_ e _respostas_
são tratados em formato **JSON** quanto a mensagem possui um _body._ Abaixo está um exemplo de _payload_ de uma **API.** <br>

---
```json
{
  "pedidoId": 101,
  "cliente": "João",
  "produtos": [
    { "nome": "Celular", "quantidade": 1 },
    { "nome": "Fone de ouvido", "quantidade": 2 }
  ],
  "total": 2200
}
```
---

# XML
O **XML** (e**X**tensible **M**arkup **L**anguage) é um formato de texto usado para armazenar e transportar dados. Assim como o **JSON**,
o **XML** é amplamente utilizado em **APIs**, sistemas legados, configurações e comunicação entre sistemas. A diferença principal é que o
**XML** usa **tags aninhadas** ao invés de **chaves e colchetes.**

## Estrutura do XML
Um arquivo XML é formado por tags que delimitam os dados, semelhante a elementos **HTML.** Cada tag pode conter **valores** ou outras tags.
Observe a baixo um exemplo disso:

---
```xml
  <usuario>
    <nome>João</nome>
  </usuario>
```
---

> Nesse exemplo, a tag <usuario> envolve a tag <nome> que contém o valor João.
---

### Uso de Tags e Atributos no XML

- **Tags:** Delimitam o início e o fim de um elemento. **Tags aninhadas** permitem criar estruturas hierárquicas, por exemplo:

---
```xml
  <produto>
    <nome>Celular</nome>
    <preco>1500</preco>
  </produto>
```
---

- **Atributos:** Além das tags, o **XML** permite adicionar informações dentro da própria tag usando **atributos**, por exemplo:

---
```xml
  <produto categoria="eletronicos" quantidade="20">
    <nome>Celular</nome>
    <preco>1500</preco>
  </produto>
```
---

> Aqui, categoria e quantidade são atributos da tag '`<produto>`'.
---

### Listas ou múltiplos elementos
XML representa listas criando múltiplos elementos com a mesma tag. Abaixo está um exemplo disso: <br>


---
```xml
  <produtos>
    <produto>
      <nome>Celular</nome>
      <preco>1500</preco>
    </produto>
    <produto>
      <nome>Notebook</nome>
      <preco>3500</preco>
    </produto>
    <produto>
      <nome>Fone de Ouvido</nome>
      <preco>200</preco>
    </produto>
  </produtos>
```
---

> Cada '`<produto>`' está dentro da tag '`<produtos>`', formando uma lista de objetos.

### Resumindo

- <tag></tag>: representa um conjunto de dados ou um elemento.
- Atributos dentro das tags podem armazenar informações adicionais.
- Listas são representadas por múltiplos elementos aninhados.

# Casos de Uso - XML
Assim como o **JSON**, o **XML** também tem várias aplicações. Observe abaixo:

## Configurações de sistemas ou APIs

---
```xml
  <configuracoes>
    <database>
      <server>localhost</server>
      <nome>LibraryDB</nome>
    </database>
    <logging>
      <nivel>Information</nivel>
    </logging>
  </configuracoes>
```
---

## Troca de dados entre sistemas

---
```xml
  <pedido>
    <id>101</id>
    <cliente>João</cliente>
    <produtos>
      <produto>
        <nome>Celular</nome>
        <quantidade>1</quantidade>
      </produto>
      <produto>
        <nome>Fone de Ouvido</nome>
        <quantidade>2</quantidade>
      </produto>
    </produtos>
    <total>2200</total>
  </pedido>
```
---

## Configurações de serviços externos

---
```xml
  <servico>
    <apiKey>123456abcdef</apiKey>
    <projectId>meu-projeto</projectId>
    <region>us-east-1</region>
  </servico>
```
---

# Resumo Geral
Tanto o **JSON** quanto o **XML** são formatos utilizados para o **armazenamento e troca de dados entre sistemas**. Cada um possui suas próprias características e cenários de uso: <br>

---
## JSON
- **Estrutura:** Baseada em **chaves (`{ }`) e listas (`[ ]`)**.
- **Característica:** O **JSON** é mais simples por causa da sua estrutura amigável e de fácil entendimento.
- **Utilidade:** Bastante usado em **APIs RESTful**, aplicações **Front-End** e **configurações modernas** hoje em dia.
- **Suporte:** Praticamente todas as lingaugens atualmente oferecem suporte ao **JSON**.
 
---

## XML
- **Estrutura:** Baseada em **tags aninhadas** e **atributos**.
- **Característica:** Mais **verboso** e complexo, porém o **XML** ainda assim é bastante flexível hoje em dia.
- **Utilidade:** Muito usado em **sistemas legados**, **configurações de serviços** e em protocolos como o **SOAP**.
- **Suporte:** Praticamente todas as linguagens atualmente também oferecem suporte ao **XML**, porém o **JSON** é mais utilizado.
  
---

# Documentações de Referência

| Conceitos     | Links                                                                 |
|---------------|----------------------------------------------------------------------|
| JSON x XML    | [AWS - Diferença entre JSON e XML](https://aws.amazon.com/pt/compare/the-difference-between-json-xml/) |
| JSON          | [MDN - JSON](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/JSON) |
| XML           | [AWS - O que é XML](https://aws.amazon.com/pt/what-is/xml/)          |

