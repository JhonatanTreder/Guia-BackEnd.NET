# Recapitulação Anterior
Na parte anterior falamos sobre **APIs** que são mecanismos utilizados em aplicações **Cliente** e **Servidor** para realizarem a comunicação entre si 
por meio de _requisições_ e _respostas_. Abordamos assuntos sobre o fluxo de toda essa comunicação e discutimos sobre a estrutura de como uma mensagem **HTTP** 
é formada nas _requisições_ e _respostas_.

# Introdução
Sendo direto ao ponto, o **SOAP** (**S**imple **O**bject **A**ccess **P**rotocol) é um **tipo de protocolo** que padroniza **a comunicação** das APIs Web.
Por outro lado, o **REST** (**RE**presentational **S**tate **T**ransfer) é um **estilo arquitetural** que define um **padrão para as APIs**, ou seja,
**APIs RESTful** são aquelas **APIs** que implementam o padrão arquitetural imposto pelo **REST**. Abaixo está uma explicação de como ambos os termos se comportam. <br>

---
> **Disclaimer**: O **SOAP** para padronização da comunicação entre as **APIs** é muito menos utilizado que um padrão arquitetural como o **REST**.
Hoje em dia a maioria das aplicações Web utilizam o padrão **REST** em suas aplicações. Para um aprofundamento maior sobre as diferenças entre **SOAP** e **REST**,
consulte a documentação da **_Red Hat:_** [RED HAT - SOAP e REST](https://www.redhat.com/pt-br/topics/api/what-are-application-programming-interfaces#soap-e-rest) <br>
---

## Comportamento S.O.A.P
O **SOAP** adota em suas mensagens o padrão **XML** que é um padrão bastante utilizado em configurações de arquivos,
documentações e até mesmo nesse caso do **SOAP** para padronizar as mensagens entre as **APIs**.
Abaixo está um exemplo de uma estrutura básica de uma  **_requisição SOAP_** escrita em **XML**: <br>

---
```xml
<?xml version="1.0"?>
<soap:Envelope 
    xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:xsd="http://www.w3.org/2001/XMLSchema">

  <soap:Body>
    <GetUserDetails xmlns="http://example.com/">
      <UserId>12345</UserId>
    </GetUserDetails>
  </soap:Body>
</soap:Envelope>
```
---

Da mesma forma que discutimos anteriormente sobre o formato de uma estrutura de mensagem **HTTP**, o **padrão SOAP** segue uma linha de raciocínio parecida. Observe abaixo: <br>

- **Start Line:** <br>
```xml
    <?xml version="1.0"?>
```

- **Conjunto de Headers:** <br>
```md
    xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    (imagine que aqui tenha uma linha em branco)
```

- **Body da Requisição:** <br>
```xml
 <soap:Body>
    <GetUserDetails xmlns="http://example.com/">
      <UserId>12345</UserId>
    </GetUserDetails>
  </soap:Body>
```

---
> **OBS:** Depois de especificar o **conjunto de Headers**, é colocado uma linha em branco para especificar que aquele conjunto de headers terminou.
Isso também é observado em padrões de respostas como em objetos **JSON**. <br>
---

### Utilidade do SOAP
O **SOAP** foi desenvolvido com a finalidade de trocar informações entre aplicações indepedente de **Sistemas Operacionais** e de **linguagens**. 
Existem três características principais que definem o comportamento do padrão **SOAP**, que são elas: <br>

- **Baseado em XML:** O processamento das mensagens nas **APIs SOAP** devem ser tratadas em **XML**.
Esse padrão foi inicialmente proposto pela **Microsoft** no final da década de 1990, em colaboração com a
**UserLand Software** e posteriormente com a **IBM.** Hoje, o **SOAP** é padronizado pelo **W3C**, sendo a versão mais recente a **1.2.** <br>

- **Independência de Transporte:** Embora seja mais usado sobre **HTTP/HTTPS,**
o **SOAP** também pode ser transportado por outros protocolos como **SMTP**, **TCP** e **JMS.** <br>

- **Uso do WSDL:** O **SOAP** faz uso do **WSDL** (**W**eb **S**ervices **D**escription **L**anguage), um documento em **XML** que descreve os serviços disponíveis,
suas operações, parâmetros e tipos de dados, funcionando como um contrato entre **cliente** e **servidor.** <br>

## Comportamento R.E.S.T
O **REST** por outro lado, é um padrão arquitetural que define o comportamento de uma **API**. O **REST** exerce uma restrição de diretrizes em suas implementações
e toda **API** que segue as regras e especificações do padrão **REST** são chamadas de **APIs RESTful**. Logo abaixo está os seis critérios que o padrão **REST** exige: <br>

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

---

### Utilidade do REST
Como já mencionado anteriormente, o **REST** é um **padrão arquitetural,** logo, o formato das mensagens enviadas por _requisições_ e _respostas_
não se limitam apenas em **JSON** e **XML**. Uma exigência típica de uma **API RESTful** é padronizar as **URLs** dos recursos existentes. Veja abaixo um exemplo válido disso. <br>

Imagine que você tenha dois tipos de recursos específicos, **Users** e **Products**. Um exemplo de **URL** padronizada poderia ser algo como: <br>

**Exemplo 1:**
```md
https://seu-site.com/Users/1
```

---

**Exemplo 2:**
```md
https://seu-site.com/Products/1
```

<br>

# Resumo

- **SOAP (Simple Object Access Protocol)**  
  - Protocolo padronizado de comunicação entre **APIs.** 
  - Baseado em **XML** para estruturar mensagens.  
  - Independente de transporte (**HTTP**, **SMTP**, **TC**P, **JMS**).  
  - Usa **WSDL** como contrato de serviços entre **cliente** e **servidor.**  
  - Mais pesado e hoje menos utilizado em comparação ao **REST.**  

---

- **REST (Representational State Transfer)**  
  - Estilo **arquitetural** para construção de APIs.  
  - **API**s que seguem suas diretrizes são chamadas de **APIs RESTful**.  
  - Principais características:
    - Arquitetura **Cliente-Servidor**.  
    - **Stateless** (sem estado entre requisições).  
    - **Cacheável** (otimiza desempenho).  
    - **Interface Uniforme** (URLs únicas, mensagens autodescritivas, HATEOAS).  
    - **Sistemas em Camadas** (intermediários, proxies, gateways).  
    - **Código sob demanda** (opcional).  
  - Mais flexível, mais leve em comparação com o **SOAP** e amplamente utilizado em aplicações modernas de hoje em dia.  

---

- **Comparação**  
  - **SOAP**: formal, baseado em **XML**, usa contrato **WSDL**.  
  - **REST:** flexível, suporta múltiplos formatos (**JSON**, **XML**, **HTML**), **URLs padronizadas.** 
  - **Mais Utilizado:** O **REST** atualmente é o **padrão dominante** para **Web APIs**.  


# Documentações de Referência

| Conceito | Links                                                                                                                                              |
|----------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| REST | [Red Hat - O que é uma API RESTful?](https://www.redhat.com/pt-br/topics/api/what-is-a-rest-api)                                                       |
| SOAP | [IBM - SOAP](https://www.ibm.com/docs/pt-br/rsas/7.5.0?topic=standards-soap)                                                                           |
| XML | [AWS - O que é XML?](https://aws.amazon.com/pt/what-is/xml/)                                                                                            |
| Diferença Entre REST e SOAP | [Red Hat - Diferença entre SOAP e REST](https://www.redhat.com/pt-br/topics/integration/whats-the-difference-between-soap-rest) |


