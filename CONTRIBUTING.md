# Agradecimentos
Olá, me chamo **Jhonatan Treder** e eu gostaria de agradecer a escolha e disponibilidade de todos aqueles que desejam contribuir com esse guia. A sua contribuição será totalmente **bem-vinda**
e com toda certeza será de grande valor para a comunidade, especialmente levando em consideração o impacto que a contribuição terá no aprendizado de todos.

# Entendendo o Objetivo do Projeto
Antes de começar a especificar as áreas de contribuições e ressaltar os problemas observáveis, é importante mencionar o objetivo desse projeto, para que a sua ideia de contribuição venha
estar alinhada com a ideia do guia em si. Sendo bem direto ao ponto, o objetivo desse guia é servir como um **conjunto de consultas** a termos do desenvolvimento **Back-End** no **.NET/.NET Core**.
Ou seja, o objetivo é explicar conceitos que muitas pessoas encontram em diversos lugares da programação quando pensamos em "desenvolvimento Back-End com .NET". A pessoa que for ler sobre um determinado conceito
apresentado aqui, deve **encontrar** a explicação, **entender** o que foi mostrado e **ter** o seu problema resolvido (no caso ter a dúvida solucionada). <br>

> **OBS:** O objetivo desse guia não é exatamente ensinar aprofundadamente os conceitos apresentados, mas sim ter como o **principal** foco a **explicação** dos termos e também **ajudar** pessoas a entenderem
sobre determinado termo. <br>

# Problemas Observáveis e Comuns do Guia
Esse guia possui alguns problemas notáveis sobre a divisão dos conteúdos apresentados, problemas esses que vão desde erros de digitações até mesmo partes faltantes de explicações dos termos.
Muitas seções apresentadas no **README** principal ainda não foram escritas ou documentadas, elas estão apenas com o esqueleto pronto. A seção 6 (**DevOps para Back-End**) é um exemplo de seção que ainda não
foi escrita ou desenvolvida. Além das seções faltantes, o repositório em si poderia conter mais conteúdos sobre outros tópicos no desenvolvimento **Back-End**, como por exemplo **mensageria** e/ou **Design Patterns**
(pretendo adicionar esses conteúdos futuramente em uma seção específica ou a parte).

# Como Contribuir
Para aqueles que desjam contribuir com esse guia, primeiramente é importante se atentar ao objetivo dele (como já foi dito a cima), e depois contribuir com o que deseja
(seja adicionando um conteúdo novo, corrigindo formatações e erros de gramáticas, sugerindo conceitos sobre desenvolvimento **Back-End**, etc).

## Passos Para Contribuir

### 1. Faça um Fork
Para realizar um **fork** do reposiório, primeiramente vá para a página inicial do guia, depois clica no botão de **fork** (canto superior direito) para criar um. Isso vai criar uma cópia
do repositório em **sua** conta. <br>

**Link explicativo do próprio GitHub para criar um fork:** [GitHub - Como Realizar Um Fork](https://docs.github.com/pt/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo) <br>

---

### 2. Clonar o Fork Localmente
Após criar o seu **fork**, crie um clone rodando o seguinte comando no terminal (ou em alguma outra **CLI** compatível): <br>

```bash
  git clone https://github.com/JhonatanTreder/Guia-BackEnd.NET
```
---

e navegue até a pasta específica. Por exemplo: <br>

```bash
  cd Guia-BackEnd.NET
```
---

### 3. Crie Uma Nova Branch
Após realizar os passos anteriores, crie uma branch **específica** para a sua contribuição. Por exemplo: <br>

```bash
  git checkout -b melhoria-readme
```

**Link do GitHub ensinando a como criar uma branch:** [GitHub - Como Criar e Excluir Branchs](https://docs.github.com/pt/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository) <br>

---

### 4. Editar os READMEs
Abra os arquivos **.md** no seu editor, como no **_Visual Studio Code_** por exemplo e faça as alterações (seja corrigir erros, adicionar conteúdo, melhorar a formatação, etc). <br>

---

### 5. Commitar as Mudanças
Primeiramente adicione os arquivos modificados. <br>

```bash
  git add .
```

Depois faça um **commit** para a branch que você criou. Por exemplo: <br>

```bash
  git commit -m "feat: adiciona nova seção de conteúdo ao README principal"
```
<br>

> **OBS:** É importante ressaltar que eu estou fazendo uso do **_conventional commits_**, que é um padrão utilizado para documentar **commits** realizados.
Isso ajuda na identificação do que foi realizado e a documentação fica melhor para análises futuras. Os tipos mais comuns de **_conventional commits_** utilizados aqui são:
> - **feat:** Utilizado quando adicionamos uma nova **feature** (conteúdo). Por exemplo: git commit -m "feat: adiciona explicação sobre APIs."
> - **fix:** Utilizado quando corrigimos algo em específico. Por exemplo: git commit -m "fix: corrige erro de digitação no arquivo de explicação sobre APIs."
> - **docs:** Utilizado para especificar mudança em documentações, então pode ser algo mais genérico, com o escopo voltado para documentações. Por exemplo: git commit -m "docs:
> melhora formatação da documentação sobre **JSON**". <br>

### 6. Enviar (push) Para o Fork
Após ter commitado, realize um **push** para o seu fork. Por exemplo: <br>

```bash
  git push origin melhoria-readme
```
<br>

---

### 7. Abrir um Pull Request (PR)
Por fim, abra uma **Pull Request**. Vá até o seu fork no **GitHub** depois vai aparecer um aviso com a opção de abrir um **Pull Request**, clique em **"Compare & Pull Request"**,
logo em seguida escreva uma descrição do que você alterou e por fim clique em **Create Pull Request**. Eu irei estar analisando e se tudo estiver certo conforme o esperado eu irei aceitar a sua contribuição. <br>

## Com o Que Contribuir
Você pode contribuir com esse guia de diversas maneiras, bem como:
- **`Adicionando Novos Tópicos ao README Principal:`** Você pode contribuir adicionando novas seções no **README** principal
- **`Traduzindo o Guia Para Inglês ou Outros Idiomas Relevantes:`** Você pode traduzir todo o conteúdo desse guia para uma versão em **Inglês** ou outro idioma relevante (como espanhol por exemplo).
- **`Padronizando Formatação Dos READMEs:`** Se você notar, muitos **READMEs** dos conceitos abordados seguem uma estrutura bem definida (com uma pequena seção sobre documentações de referência no final)
você pode padronizar **READMEs** que não possuem esse tipo de estrutura e adotar a **READMEs** que você for criar futuramente.
- **`Com Sugestões Gerais:`** Uma forma bem simples de contribuição é sugerir ideias, pontos de melhorias e até mesmo recomendar conteúdos que você gostaria que o guia abordasse.
No final eu irei deixar algumas redes sociais para contato, você pode apresentar suas sugestões por lá (ou abrir uma **Issue** aqui no **GitHub** paara discutirmos sobre determinada coisa).

# Contatos
-  <img src="https://github.com/user-attachments/assets/1abb9374-6c7e-4630-bb6b-f91b6be0d230" width="20" height="20" alt="Discord" style="vertical-align: middle;" /> **Discord:** hypexsz
-  <img src="https://github.com/user-attachments/assets/592b13ba-ceea-4986-a49e-17feba1be244" width="20" height="20" alt="Discord" style="vertical-align: middle;" /> **LinkedIn:** www.linkedin.com/in/jhonatan-treder-40777827a
