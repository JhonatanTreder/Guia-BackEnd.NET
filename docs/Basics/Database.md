# Recapitulação Anterior
Anteriormente, abordamos a diferença entre as estruturas **JSON** e **XML**, que são dois tipos diferentes de formatos utilizados na tratativa de dados entre sistemas.
Explicamos que o **JSON** e **XML** são amplamente utilizados entre aplicações para **definir configurações**, **armazenar dados**, **compartilhar mensagens entre sistemas** e muitos outros casos.
Além de que explicamos a estrutura de ambos os formatos e mencionamos os seus casos de usos.

# Introdução
Nesta seção, iremos abordar um dos assuntos mais essenciais no **desenvolvimento Back-End**: O conceito de **banco de dados**. Resumindamente, **banco de dados**
é um conjunto organizado de informações, permitindo que os dados sejam **acessados**, **gerenciados** e **compartilhados** entre diferentes aplicações. Os **banco de dados**
servem para armazenar, relacionar e gerenciar vários tipos de informações entre sistemas. Sendo assim, é fundamental entendermos o funcionamento de como um **banco de dados** funciona como um todo.

## Origem do Banco de Dados
Antigamente os dados eram armazenados em formatos bem diferentes dos quais utilizamos hoje em dia. Antes, eram utilizados **registros físicos**, **papéis**, **cartões perfurados**, **documentos**, etc.
Com o passar do tempo, várias outras formas de armazenamento de dados foram surgindo, como por exemplo: Armazenamento de arquivos como `.txt`,`.csv`, `.dat`. Foi então que na **década de 60** surgiram
os primeiros tipos de banco de dados, os **bancos em rede** e os **hierárquicos**. <br>

- **Bancos em Rede:** Organizavam os dados por meio de registros ligados entre si, permitindo relacionamentos mais flexíveis (como muitos-para-muitos), porém ainda assim eram complexos de manter.
Por exemplo: <br>

---
```md

  CLIENTE                                     CONTA
  +----------+------------+---------+         +------+-------+
  | NOME_CLI | CIDADE_CLI | TEL_CLI |---------| #_CC | SALDO |
  +----------+------------+---------+         +------+-------+
```
---

- **Bancos Hierárquicos:** Estruturavam os dados em forma de árvore, onde cada registro tinha um “pai” e vários “filhos”, o que limitava a flexibilidade. Por exemplo: <br>

---
```md
 CLIENTE
+----------+------------+---------+
| NOME_CLI | CIDADE_CLI | TEL_CLI |
+----------+------------+---------+
       |
       +-----------------------------+
       |                             |
   CONTA_CORRENTE                CONTA_CORRENTE
   +------+-------+              +------+-------+
   | #_CC | SALDO |              | #_CC | SALDO |
   +------+-------+              +------+-------+

```
---

### Surgimento do Modelo Relacional - Década de 70
Proposto por **_Edgar Frank Codd_**, surgiu o **modelo relacional** dos bancos de dados, modelo esse que utiliza tabelas (**linhas** e **colunas**). O modelo relacional
foi um grande marco em como os dados poderiam ser estruturados e passou a ser bastante utilizado no armazenamento das informações, esse modelo também é amplamente utilizado hoje em dia. <br>

#### Exemplos de Bancos de Dados Relacionais:
- **Oracle Database (lançado em 1979):** Um dos primeiros bancos comerciais a adotar o modelo relacional.  
- **IBM DB2 (lançado em 1983):** Desenvolvido pela **própria IBM**, empresa onde **_Codd_** trabalhou.  
- **Microsoft SQL Server (lançado em 1989):** Muito usado em aplicações corporativas.  
- **MySQL (lançado em 1995):** Um dos mais populares no desenvolvimento web.  
- **PostgreSQL (lançado em 1996):** Famoso por seguir os padrões do **SQL** e oferecer recursos avançados. <br>

### Modelo Não Relacional (NoSQL) – Anos 2000
Com o crescimento da internet e a explosão de dados gerados por **redes sociais**, **aplicativos** e **serviços online**, o **modelo relacional** começou a enfrentar limitações.  
Para lidar com **grandes volumes de dados** (Big Data) e formatos mais variados, surgiu o **modelo não relacional**, conhecido como **NoSQL**. <br> 

Diferente do modelo relacional, o **NoSQL** não depende de tabelas fixas com linhas e colunas. Por isso, ele oferece bastante flexibilidade na hora de armazenar os dados.

#### Principais tipos de bancos NoSQL:
- **Chave-Valor:** Armazenam dados como pares de chave e valor.  
  - Exemplo: **Redis** e **Amazon DynamoDB**.  

- **Orientado a Documentos:** Guardam dados em documentos (geralmente em **JSON**).  
  - Exemplo: **MongoDB** e **CouchDB**.  

- **Orientado a Colunas:** Dados organizados em colunas em vez de linhas, ótimo para consultas analíticas.  
  - Exemplo: **Apache Cassandra** e **HBase**.  

- **Orientado a Grafos:** Focados em relações e conexões entre dados.  
  - Exemplo: **Neo4j** e **Amazon Neptune**. <br>

## SQL? NoSQL?
A sigla **"SQL"** vem de "**S**tructured **Q**uery **L**anguage", que traduzindo para o português seria "Linguagem de Consulta Estruturada". <br>

> **_A Linguagem de consulta estruturada (SQL) é uma linguagem de programação para armazenar e processar informações em um banco de dados relacional.
Um banco de dados relacional armazena informações em formato tabular, com linhas e colunas representando diferentes atributos de dados e as várias relações
entre os valores dos dados. Você pode usar instruções SQL para armazenar, atualizar, remover, pesquisar e recuperar informações do banco de dados. Também pode
usar SQL para manter e otimizar a performance do banco de dados._** <br>

**Fonte Textual:** _https://aws.amazon.com/pt/what-is/sql/_ <br>

### Exemplo de Consulta com SQL
As instruções **SQL** são usadas para manipular os dados existentes em um banco de dados. Você escreve comandos em **SQL** para atualizar, adicionar e até mesmo excluir dados.
Abaixo está um exemplo de banco dessa instrução. <br>

Primeiramente, observe esse exemplo de tabela. <br>

---
```md

                +------------------+
                | Tabela: Clientes |
                +------------------+
  +-----------+--------+-----------------+-------+
  | ClienteID |	Nome   |  Cidade         | Idade |
  +-----------+--------+-----------------+-------+
  |     1	  | Ana    |  São Paulo      |  25   |
  |     2	  | Bruno  |  Rio de Janeiro |  30   |
  |     3	  | Carla  |  Belo Horizonte |  28   |
  |     4	  | Daniel |  Salvador       |  35   |
  +-----------+--------+-----------------+-------+


```
---

Agora irei mostrar um exemplo de **SQL** que consulta todos os clientes de uma cidade específica. <br>

---
```sql
  SELECT Nome, Cidade -- Seleciona quais colunas mostrar
  FROM Clientes -- Seleciona a tabela
  WHERE Cidade = 'Belo Horizonte'; -- Adiciona um filtro
```
---

O resultado seria esse: <br>

---
```md
  +--------+-----------------+
  |	Nome   |  Cidade         |
  +--------+-----------------+
  | Carla  |  Belo Horizonte |
  +--------+-----------------+
```
---

### Exemplo de Consulta NoSQL

Diferente dos **bancos de dados relacionais** nos **banco de dados não-relacionais** nós não utiizamos o **SQL**
como forma de consultar os dados, por outro lado, utilizamos métodos nas tabelas e outras formas. Observe um exemplo
abaixo disso. <br>

Primeiramente, observe esse exemplo de conjunto de dados em **JSON**. <br>

---
```json
  [
    { "nome": "Ana", "idade": 25, "cidade": "São Paulo" },
    { "nome": "João", "idade": 30, "cidade": "Rio de Janeiro" },
    { "nome": "Maria", "idade": 28, "cidade": "São Paulo" }
  ]
```
---

Agora irei mostrar um exemplo de consulta em um **banco de dados não-relacional** que filtra os clientes pela cidade **"São Paulo"**. <br>

---
```jaavscript
  db.clientes.find({ cidade: "São Paulo" })
```
---

O resultado seria esse: <br>

---
```json
  [
    { "nome": "Ana", "idade": 25, "cidade": "São Paulo" },
    { "nome": "Maria", "idade": 28, "cidade": "São Paulo" }
  ]
```
---

# Resumo

- **Bancos de dados** são mecanismos muito utilizados hoje em dia para gerenciar e armazenar dados, facilitando assim o acesso e manipulação das informações existentes.
- Antigamente, os dados eram guardados em **cartões perfurados**, **papéis** e **arquivos simples** como `.txt` e `.csv`.
- Na década de **60**, surgiram os primeiros modelos de banco de dados, como por exemplo:
  - **Modelo Hierárquico:** Em formato de árvore.
  - **Modelo em Rede:** Registros interligados em relações mais complexas.

- Na década de **70**, com **Edgar Codd**, nasceu o **modelo relacional**, que usa tabelas (**linhas** e **colunas**) e até hoje é o mais utilizado.
  - Exemplos: **Oracle**, **MySQL**, **PostgreSQL**, **SQL Server**.

- Nos anos **2000**, com o crescimento da internet e o **Big Data**, surgiram os **bancos NoSQL**, que não dependem de tabelas e oferecem mais flexibilidade.
  - Exemplos: **MongoDB (documentos)**, **Redis (chave-valor)**, **Cassandra (colunas)** e **Neo4j (grafos)**.

- Para consultar dados:
  - Em bancos relacionais usamos **SQL**, por exemplo: <br>

---
```sql
  SELECT * FROM clientes WHERE cidade = 'São Paulo';
```
---

- Em bancos NoSQL usamos comandos específicos para realizar o acesso e manipulação aos dados. Exemplo no **MongoDB**: <br>

---
```javascript
  db.clientes.find({ cidade: "São Paulo" })
```
---

# Documentações de Referência

| Conceitos       | Links                                                                 |
|-----------------|----------------------------------------------------------------------|
| Banco de Dados  | [Oracle - Database](https://www.oracle.com/br/database/what-is-database/)       |
| SQL             | [AWS - SQL](https://aws.amazon.com/pt/what-is/sql/)                        |
| NoSQL           | [Google Cloud - NoSQL](https://cloud.google.com/discover/what-is-nosql?hl=pt-BR) |
