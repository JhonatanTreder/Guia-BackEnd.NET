# Recapitulação Anterior
Anteriormente, falamos sobre o significado de **DNS** que é um mecanismo utilizado pelos navegadores para tratar **nomes de domínios** a respectivos **endereços IPs** na web.
Abordamos sobre o funcionamento do **DNS** e como ele se comporta quando buscamos por um site e/ou serviço na internet.

# Introdução
O termo **Websocket** se refere a um protocolo que _mantém_ a conexão
entre o **cliente** e **servidor** aberta, permitindo a troca contínua de informações em tempo real. Com isso, não é necessário abrir um novo canal de comunicação a cada requisição, tanto o cliente quanto 
o servidor podem enviar e receber dados a qualquer momento. Um exemplo de cenário onde **Websockets** são utilizados é em **chats online** (como o **Discord**, **Instagram**, **Whatsapp**, etc.),
onde existe a necessidade de uma conexão aberta em tempo real para o envio e recebimento de dados. Diferente do protocolo **HTTP** que a conexão é fechada logo após o envio de uma resposta do servidor
para o cliente, um protocolo **Websocket** mantém a conexão aberta e ambos os lados podem enviar e receber dados em qualquer momento.

# Uso Consciente de Websockets

- **Vantagens:** O uso de **Websocket** é extremamente poderoso e benéfico para as aplicações, pois ele permite uma grande extensão de recursos e oferece uma melhor experiência para o usuário.
Veja algumas vantagens de se utilizar **Websockets:** <br>
  - **Comunicação em Tempo Real:** Permite troca de dados instantânea entre cliente e servidor, sem necessidade de requisições repetidas.
  - **Full-Duplex:** Cliente e servidor podem enviar e receber mensagens simultaneamente. 
  - **Redução de Overhead:** Diferente do **HTTP**, o uso de **Websocket** não precisa abrir uma nova conexão a cada requisição, economizando recursos e largura de banda.
  - **Baixa Latência:** Ideal para aplicações que exigem resposta rápida (**como chats**, **jogos online** e **dashboards em tempo real**).
  - **Escalabilidade Eficiente em Cenários Corretos:** Quando usado para o propósito certo, permite comunicação contínua sem necessidade de _polling_ constante.
  - **Suporte Amplo:** A maioria dos navegadores modernos e muitas bibliotecas de **Back-End** suportam **WebSockets** nativamente.
  - **Flexibilidade:** Pode transmitir qualquer tipo de dado (**texto**, **binário**, **JSON**, etc.) através da mesma conexão.
  ---

 - **Desvantagens:** Por outro lado, deve ser implementado apenas em cenários onde existe a necessidade de **_manter_** uma conexão aberta, caso contrário poderia resultar em vários problemas para o servidor,
 e consequentemente, para o lado do cliente. Veja alguns exemplos: <br>
   - **Perda de Performance/Desempenho:** Manter conexões abertas consome memória e recursos do servidor. Muitas conexões desnecessárias podem levar a lentidão ou travamentos.
   - **Escalabilidade Limitada:** Cada **WebSocket** ocupa recursos persistentes, dificultando a escalabilidade do servidor em sistemas com muitos usuários.
   - **Risco de Vazamento de Conexões:** Conexões não fechadas corretamente podem sobrecarregar o servidor com sockets “fantasmas”.
   - **Segurança:** Conexões abertas podem ser alvo de ataques (DoS, injeção de dados) se não houver validação e autenticação adequadas.
   - **Complexidade na Lógica do Servidor:** Gerenciar múltiplas conexões ativas exige lógica mais complexa (broadcasts, filas de mensagens, reconexões automáticas, etc.).
   - **Compatibilidade e Depuração:** Problemas de rede podem causar desconexões inesperadas, e depurar fluxos contínuos de mensagens é mais difícil que requisições HTTP pontuais.
   ---

# Resumo
**Websockets** é uma tecnologia muito poderosa que possibilita a comunicação contínua tanto para envio quanto para recebimento de dados nas aplicações hoje em dia sem ter a necessidade
de abrir um novo canal de comunicação. Porém é de grande importância se atentar ao fato que essa tecnologia deve ser utilizada de forma consciente, caso contrário haverá problemas tanto
para o lado do servidor (principalmente) quanto para o lado do cliente que está consumindo tal serviço.

# Documentações de Referência

| Conceitos                      | Links                                                                                                                                      |
|--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| Websockets - Mozilla Reference | [MDN Web Docs - WebSockets](https://developer.mozilla.org/pt-BR/docs/Web/API/WebSockets_API)                                               |
| Websockets - Google Reference  | [GeeksforGeeks - WebSockets](https://www-geeksforgeeks-org.translate.goog/web-tech/what-is-web-socket-and-how-it-is-different-from-the-http/?_x_tr_sl=en&_x_tr_tl=pt&_x_tr_hl=pt&_x_tr_pto=tc) |
| Websockets - Código Fonte TV   | [YouTube - Código Fonte TV - WebSockets](https://www.youtube.com/watch?v=T4unNrKogSA)                                                       |
