
# Flutter Clean Architecture

Estruturação do projeto seguindo o padrão CA.

    ├── ...
    ├── lib
    │   ├── core          # Contém tudo que é em comum, compartilhado com o app
    │   |   ├── data      # Fica o serviço de requisição http(s) (dio, http, etc) implementando o domain
    │   |   ├── domain    # Ficam os contratos de requisição que será implementado pelo data service
    │   |   ├── inject    # Faz a injeção de dependências (GetIt, Provider, etc)
    │   |   └── utils     # Constants, func genéricas, etc
    │   ├── features      # Ficam os módulos do app
    │   |   ├── movies    # Módulo que lista filmes
    │   │   |   ├── data            # Resposável por recuperar os dados
    │   |   |   |   ├── datasources     # Ficam as fontes de dados (local, firebase, etc)
    │   |   |   |   |   ├── local           # Fonte de dados locais
    │   |   |   |   |   └── remote          # Fonte de dados externos, aqui o remote vai utilizar o serviço de requisição do data core
    │   |   |   |   ├── dtos            # Manipulação dos dados da entidade (fromJson, toJson, etc)
    │   |   |   |   └── repositories    # Implementa os repositories da camada domain
    │   │   |   ├── domain          # Responsável pelas regras de negócios
    │   |   |   |   ├── entities        # Modelação das entidades
    │   |   |   |   ├── repositories    # Ficam os contratos (abstract) que depois serão implementadas pela camada "data"
    │   |   |   |   └── usecases        # Usecase das actions, aqui fica os usecases (abstract) e as implementações 
    │   │   |   └── presentation    # Responsável pela apresentação dos dados 
    │   |   |       ├── controllers     # Faz a ponte acessando os dados pela camada domain (via mobx, cubit, etc)
    │   |   |       ├── dtos            # Manipulação dos dados da entidade para apresentação (copyWith, etc)
    │   |   |       └── ui              # Apresentação do dados para o usuário final
    │   |   |           ├── pages           # Scaffolds
    │   |   |           └── widgets         # Widgtes que compoem as páginas
    │   |   └── ...
    │   └── main.dart     # Start o app
    └── test
