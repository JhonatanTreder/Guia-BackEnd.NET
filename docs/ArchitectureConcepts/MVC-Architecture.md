# Introdução
esta seção, falaremos sobre o padrão de arquitetura **MVC** "**M**odel, **V**iew and **C**ontroller" (ou **Modelo**, **Visão** e **Controlador** em português). Sendo direto ao ponto,
o **MVC** é uma **arquitetura de software** amplamente utilizada em sistemas atualmente, principalmente em aplicações web. Antes de iniciar o desenvolvimento de um software ou projeto,
é de grande importância escolher a arquitetura que será adotada, pois a escolha de uma boa arquitetura oferece diversos benefícios para a aplicação como **escalabilidade**, **manutenibilidade**,
**organização**, além de que é a melhor opção para aqueles que desejam que outras pessoas contribuam com o projeto de maneira mais eficiente.

## Arquitetura de Software: Contexto e Importância
Como já dito acima, o **MVC** é uma **arquitetura de software**. Mas o que exatamente significa isso?  
Resumidamente, uma arquitetura de software é um tipo de estrutura (ou um "esqueleto") que define a base de um sistema, definindo seus componentes principais, suas responsabilidades e como eles
se relacionam entre si e com elementos **externos** (como **bancos de dado**s, **serviços**, **APIs**, entre outros). Pode-se entender que a arquitetura não descreve todos os detalhes de implementação,
mas estabelece as **diretrizes** de **organização** e os **padrões de interação** entre as partes da aplicação.  

- > **"_A arquitetura de software é a estrutura do sistema composta por componentes, as propriedades visíveis desses componentes e os relacionamentos entre eles."
— Bass, Clements & Kazman (Software Architecture in Practice)._** <br>

- > **_Arquitetura de software é a estrutura fundamental ou o esqueleto de um sistema de software, que define seus componentes, suas relações e seus princípios de projeto e evolução.
— De acordo com a ISO/IEC/IEEE 42010:2022._** <br>

## Exemplos de Arquiteturas de Software

### 1. Arquitetura em Camadas (Layers)
Essa arquitetura organiza a aplicação em camadas distintas, sendo que cada camada possui uma função específica. Ela geralmente é dividida em quatro partes, que são elas: <br>

- **Apresentação (UI):** Interação com o usuário (por exemplo: **HTML**, **CSS**, **JavaScript**, **React**, **Angular**).  
- **Aplicação (Service Layer):** Contém as regras de negócio da aplicação (não confundir com regras de domínio).  
- **Domínio (Business Layer):** Define regras, entidades, modelos e validações específicas do problema que o software resolve.
- **Infraestrutura (Data Access):**Responsável pela comunicação com recursos externos (**bancos de dados**, **APIs**, **serviços de terceiros**, **arquivos**, entre outros).

### 2. Arquitetura de Microserviços
Essa arquitetura divide a aplicação em vários serviços que podem ser implementados de maneira independente, além de que a sua comunicação geralmente
é realizada por meio de **APIs REST**, **serviços de mensageria (como `Kafka`, `RabbitMQ`)** ou **gRPC**. Em uma aplicação de e-commerce, a divisão poderia ser feita desta forma: <br>

- Serviço de Usuários  
- Serviço de Catálogo  
- Serviço de Pedidos  
- Serviço de Pagamentos  

> Existem outras arquiteturas, como **Clean Architecture**, **DDD (Domain-Driven Design)** e **CQRS**. O modelo arquitetural **MVC** é um dos mais utilizados,
porém a escolha da arquitetura vai depender das necessidades do sistema ou da aplicação. <br>


## Histórico do MVC

A arquitetura **MVC** foi criada no final dos **anos 70** pelo cientista norueguês **_Trygve Reenskaug_** durante sua passagem pelo Xerox **Palo Alto Research Center (PARC)**.  
A primeira ideia foi documentada em maio de 1979 como *"Thing-Model-View-Editor"*, evoluindo para **_Model-View-Controller_** após discussões com **Adele Goldberg** e outros pesquisadores. 
Em** dezembro de 1979**, **Reenskaug** formalizou o padrão **MVC** com apenas três componentes, que são eles:

- **Model:** Dados e regras de negócio.  
- **View:** Apresentação visual dos dados.  
- **Controller:** Intermediário entre usuário e sistema.  

Desde então, o **MVC** tornou-se um dos padrões mais significantes no desenvolvimento de software.

### Evolução Inicial do MVC (1978-1988)
<img width="3570" height="2154" alt="MVC-InitalEvolution" src="https://github.com/user-attachments/assets/64ac12ba-f1d5-4609-a508-51a03ef0b789" />


## Componentes do MVC
---
### Model
- Responsável pelos dados e regras de negócio.  
- Manipula dados.  
- Integra com bancos de dados.  
- Implementa validações e lógica de domínio.  

### View
- Responsável pela interface do usuário.  
- Renderiza HTML, CSS, JavaScript.  
- Exibe dados recebidos do Controller.  
- Não contém lógica de negócio.  

### Controller
- Age como intermediário entre Model e View.  
- Recebe requisições do usuário.  
- Processa dados usando o Model.  
- Retorna a View apropriada.  
---

## ASP.NET Core MVC

### O que é o ASP.NET Core MVC?
No ecossistema do **.NET/.NET Core** existe o **ASP.NET Core MVC** que é um **framework** de desenvolvimento web de código aberto,
multiplataforma e altamente testável, construído sobre o **ASP.NET Core**. Ele segue o padrão arquitetural **Model**-**View**-**Controller** (**MVC**),
que promove a separação de preocupações (Separation of Concerns), organizando a aplicação em três componentes principais que já conhecemos até agora (**Model**, **View** e **Controller**). <br>

### Vantagens do Framework
Alguma das vantagens desse framework inclui: <br>
- Separação de concerns (lógica, interface e controle)  
- Roteamento inteligente (convencional e por atributos)  
- Injeção de dependência nativa  
- Validação integrada com *Data Annotations*  
- Suporte a APIs RESTful e JSON  
- Integração com modernos frameworks front-end  

---

### Estrutura de um Projeto ASP.NET Core MVC
A estrutura de um

---
```
  ProjetoMVC/
  ├── Controllers/     # Controladores
  ├── Models/          # Modelos de domínio
  ├── Views/           # Visualizações (Razor)
  ├── ViewModels/      # Modelos de visualização
  ├── Services/        # Serviços e lógica de negócio
  ├── wwwroot/         # Arquivos estáticos (CSS, JS)
  └── Program.cs       # Ponto de entrada da aplicação
```

### Exemplo de Código

#### Controller
```csharp
public class HomeController : Controller
{
    private readonly IUserService _userService;

    public HomeController(IUserService userService)
    {
        _userService = userService;
    }

    public IActionResult Index()
    {
        var users = _userService.GetAllUsers();
        return View(users);
    }
}
```
#### View (Razor)

---
```csharp
  @model IEnumerable<User>
  
  <h2>Lista de Usuários</h2>
  @foreach (var user in Model)
  {
      <p>@user.Name - @user.Email</p>
  }
```
---

#### Model
---
```csharp
   public class User
   {
      public int Id { get; set; }
      
      [Required]
      public string Name { get; set; }
      
      [EmailAddress]
      public string Email { get; set; }
   }
```
---

## Comparação com Outras Abordagens no .NET
| Tecnologia       | Melhor Para...                           | Diferenciação                  |
|------------------|------------------------------------------|--------------------------------|
| ASP.NET Core MVC | Aplicações web com UI dinâmica           | Controle total sobre HTML      |
| Razor Pages      | Páginas simples e focadas                | Arquitetura baseada em páginas |
| Blazor           | Aplicações interativas com C# no client  | WebAssembly/Server-side        |


# Conclusão

O **ASP.NET Core MVC** é um framework cheio de benefícios para construir aplicações web atualmente, sua ligação ao padrão **MVC** facilita a principalmente a **organização**,
**manutenção** e **escalabilidade**, dos projetos. Sendo combinado com o ecossistema **.NET**, ele oferece desempenho e produtividade para desenvolvedores.

# Documentações de Referência
| Conceitos                                 | Links                                                                                       |
|-------------------------------------------|---------------------------------------------------------------------------------------------|
| Padrão MVC - Microsoft                    | [MVC - Microsoft](https://dotnet.microsoft.com/pt-br/apps/aspnet/mvc)                       |
| Arquitetura de Software - Código Fonte TV | [Arquitetura de Software - Código Fonte TV](https://www.youtube.com/watch?v=kYx1QC1XZSo)    |
| MVC - Código Fonte TV                     | [MVC - Código Fonte TV ](https://www.youtube.com/watch?v=jyTNhT67ZyY&t=1s)                  |
| .NET - Código Fonte TV                    | [.NET](https://www.youtube.com/watch?v=hlgm_1Bzt-4)                                         |
