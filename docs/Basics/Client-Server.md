# Introdução
A estrutura **Cliente e Servidor** é a estrutura geral que compõe a Web, de um lado temos o **cliente** e do outro temos o **servidor**.
Mas afinal de contas, o que seria essa estrutura? Bem, é isso que irei abordar logo abaixo.

## O que é o `Lado do Cliente`?
O lado do **cliente** é nada mais e nada menos que o próprio usuário que está acessando determinado site por meio de um navegador.
O **cliente** pode ser uma pessoa utilizando um PC (ou qualquer aparelho com acesso a internet que permita acessar um navegador para interagir com algo em determinado site),
ou até mesmo pode ser um aplicativo/dispositivo que realiza buscas para uma plataforma específica. <br> <br>
**OBS:** O termo "**cliente**" não está limitado apenas aos usuários que acessam sites. 
**Clientes** também são aqueles que consomem algum tipo de serviço em determinada plataforma específica, como Twitch, Netflix, Instagram, etc.

## O que é o `Lado do Servidor`?
O lado do **servidor**, por sua vez, se trata de um site e/ou algum programa que oferece algum tipo de serviço ao cliente.
Por exemplo: o `YouTube` é um **servidor** que oferece um serviço de **Streaming** para os usuários, serviço esse que vai desde _`Shorts`_ até _`Transmissões ao vivo`_ e muitos outros.
Um outro exemplo é a `Steam`, que por sua vez, é um **servidor** que oferece um serviço de **compras** de jogos e softwares para os seus **clientes** <br> <br>
**OBS:** O termo "**servidor**" também não está limitado apenas a sites.
**Servidores** também são aqueles que fornecem algum tipo de dado, funcionalidade ou algum recurso para os **clientes**.

# Comunicação entre `Cliente` e `Servidor`
De forma geral, a comunicação é feita por **requisições** e **respostas** por meio de protocolos HTTP ou HTTPS.
Por exemplo: Quando pesquisamos por "Notebook" na barra de pesquisa do mercado livre, estamos enviando uma _requisição_ 
para a plataforma do mercado livre que por sua vez o servidor nos devolve uma _resposta_. 
Nesse exemplo, nós enviamos um pedido (no caso da _requisição_ foi "Notebook") e o servidor nos retorna uma _resposta_ 
(em um caso real, o servidor retornaria uma lista de acordo com o que pedimos).<br> <br>

**OBS:** Os assuntos **requisições**, **respostas**, **HTTP** e/ou **HTTPS** serão abordados logo adiante na segunda parte, então não precisa se preocupar muito com isso por agora. <br>

# Resumo
Cliente é aquele que faz uma _requisição_ para um servidor através do envio de formulários,
pesquisas ou até mesmo clicks em algum botão em determinada plataforma (seja essa plataforma um site ou algum aplicativo). 
Servidor é aquele que envia dados para o cliente com base no que ele pediu através de _respostas_. <br> <br>

**OBS:** A requisição que um cliente faz para um servidor pode ser algo digitado, pesquisado e/ou algo semelhante.
Por outro lado, a resposta que o servidor retorna para o cliente pode ser detalhes sobre determinado produto,
pode ser algum tipo de dado ou até mesmo um redirecionamento para outra página.
