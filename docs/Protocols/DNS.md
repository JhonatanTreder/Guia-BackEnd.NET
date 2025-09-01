# Introdução
Nessa parte, falaremos sobre **DNS** (**D**omain **N**ame **S**ystem) que é um termo utilizado para descrever um mecanismo que atua na web hoje em dia.

- **`Sigla DNS:`** A sigla **DNS** vem de "**D**omain **N**ame **S**ystem", que traduzindo para o português seria **Sistema de Nome de Domínio**.
- **`Explicação:`** Resumidamente, é um sistema que converte nomes de domínios (por exemplo, "www.github.com") em **endereços IPs**.
 Quando digitamos o nome de algum site ou serviço na internet, o **DNS** faz uma ligação desse nome que digitamos com vários **endereços IPs** associados a ele.
  - **Nome de Domínio:** É um identificador único e legível que serve para localizar e identificar um **site** ou **serviço** na internet.
  Ele funciona como um endereço que aponta para o servidor correspondente. Por exemplo: "`www.github.com`", "`www.youtube.com`", "`www.amazon.com`".
  - **Endereço IP:** É uma sequência numeral única que identifica cada dispositivo conectado a uma rede baseada no **protocolo IP** (**I**nternet **P**rotocol).
  Diferente de um **nome de domínio**, ele é o “endereço” do dispositivo, permitindo que computadores e servidores se encontrem e troquem informações. <br>

    > **OBS:** Endereços IPs podem mudar com o tempo. Ou seja, se um endereço IP mudar, provavelmente ele pode não apontar para o mesmo nome de domínio que antes. <br>


# Como o DNS Funciona
Quando digitamos um **nome de domínio** no navegador, o **DNS** realiza uma **tradução** desse nome para o **endereço IP** correspondente. Esse processo envolve algumas etapas:

1. **Consulta ao Resolver Local:**  
   O computador primeiro verifica se já conhece o **IP** do domínio em um **cache local**. Se não encontrar, envia uma consulta para o **DNS recursivo** do provedor de internet.

2. **Consulta Recursiva:**  
   O **DNS** recursivo pergunta aos servidores **raiz** da internet qual servidor é responsável pelo domínio em questão.

3. **Servidores Autoritativos:**  
   Finalmente, o servidor autoritativo do domínio responde com o **endereço IP** correto.

# Tipos de Registros DNS
Existem diferentes tipos de registros que armazenam informações sobre domínios. Abaixo está alguns exemplos:

- **A (Address Record):** Liga um domínio a um **endereço IPv4**.  
  Exemplo: `github.com` a `140.82.114.3`
- **AAAA (IPv6 Address Record):** Liga um domínio a um **endereço IPv6**.  
- **CNAME (Canonical Name):** Define um **apelido** para outro domínio.  
  Exemplo: `www.example.com` para `example.com`
- **MX (Mail Exchange):** Indica qual servidor de e-mail é responsável pelo domínio.  
- **TXT:** Armazena informações de texto que podem ser utilizadas para validação, autenticação de e-mail (**SPF**, **DKIM**) e outras configurações.

# Observações Importantes
- Um mesmo **nome de domínio** pode ter **vários endereços IPs**, especialmente grandes sites que usam **CDNs** (**C**ontent **D**elivery **N**etworks).  
- O **DNS** é fundamental para que a internet funcione. Sem ele, teríamos que memorizar apenas **endereços IPs**, o que seria impossível e/ou muito dificultoso.
- Por questões de segurança, algumas consultas **DNS** podem ser **criptografadas**, utilizando **DNS over HTTPS (DoH)** ou **DNS over TLS (DoT)**.

# Resumo
O **DNS** é responsável por fazer a ligação de um **nome de domínio** específico para um **endereço IP** correspondente a esse nome.
Ele pode apontar para vários endereços IPs diferentes quando você pesquisa o nome de um site ou serviço na internet e te fornece resultados com base nisso.

# Documentações de Referências

| Conceitos                | Links                                                                                    |
|--------------------------|------------------------------------------------------------------------------------------|
| O Que é DNS?             | [AWS - O Que é DNS?](https://aws.amazon.com/pt/route53/what-is-dns/)                     |
| Tipos de Registros DNS   | [Cloudflare - Registros DNS](https://www.cloudflare.com/pt-br/learning/dns/dns-records/) |
