# Aplicativo de Gestão de Pacientes e Médicos Odontologico

## Objetivo do Projeto
O objetivo deste projeto é desenvolver um aplicativo em C# que implemente um sistema de gerenciamento de pacientes e médicos através de operações CRUD (Criar, Ler, Atualizar e Deletar). Este sistema facilitará o cadastro e a administração das informações dos pacientes e médicos, contribuindo para uma melhor gestão de dados na área da odotonlogica.

## Escopo
Este projeto terá as seguintes funcionalidades principais:
- **Cadastro de Pacientes**: Permitir a inserção de novos pacientes com informações como nome, idade, telefone e endereço.
- **Cadastro de Médicos**: Permitir a inserção de novos médicos com informações como nome, especialidade, telefone e endereço.
- **Listagem de Pacientes**: Exibir uma lista de todos os pacientes cadastrados, com a possibilidade de visualizar detalhes de cada um.
- **Listagem de Médicos**: Exibir uma lista de todos os médicos cadastrados, com a possibilidade de visualizar detalhes de cada um.
- **Atualização de Dados**: Permitir a edição das informações de pacientes e médicos já cadastrados.
- **Remoção de Pacientes e Médicos**: Possibilitar a exclusão de registros de pacientes e médicos que não são mais necessários.

## Requisitos Funcionais
1. **Cadastrar Paciente**: O sistema deve permitir o cadastro de novos pacientes com os seguintes campos: nome, idade, telefone e endereço.
2. **Cadastrar Médico**: O sistema deve permitir o cadastro de novos médicos com os seguintes campos: nome, especialidade, telefone e endereço.
3. **Listar Pacientes por ID**: O sistema deve exibir somente um paciente com id buscado.
4. **Listar Médicos por ID**: O sistema deve exibir somente um médico com id buscado.
5. **Listar Pacientes**: O sistema deve exibir uma lista de todos os pacientes cadastrados.
6. **Listar Médicos**: O sistema deve exibir uma lista de todos os médicos cadastrados.
7. **Atualizar Paciente**: O sistema deve permitir a edição dos dados de um paciente selecionado.
8. **Atualizar Médico**: O sistema deve permitir a edição dos dados de um médico selecionado.
9. **Deletar Paciente**: O sistema deve permitir a exclusão de um paciente do sistema.
10. **Deletar Médico**: O sistema deve permitir a exclusão de um médico do sistema.

## Requisitos Não Funcionais
1. **Usabilidade**: A interface do aplicativo deve ser simples e intuitiva, facilitando o uso por profissionais de saúde.
2. **Desempenho**: O sistema deve ser capaz de processar e armazenar dados de pacientes e médicos de forma eficiente.
3. **Segurança**: As informações dos pacientes e médicos devem ser armazenadas de forma segura e com acesso controlado.
4. **Escalabilidade**: O sistema deve ser capaz de suportar um número crescente de registros de pacientes e médicos.

## Tecnologias Utilizadas
- **Linguagem**: C#
- **Framework**: .NET
- **Banco de Dados**: Oracle
- **Swagger/OpenAPI**: Documentação da API
- **Padrão de Criação**: Logger Manager (para gerenciamento de logs)
- **Arquitetura**: MVC (Model-View-Controller)

---

## Artefatos do Projeto

### Arquitetura da API (MVC)
A aplicação foi desenvolvida utilizando a arquitetura monolítica, aplicada através do padrão MVC (Model-View-Controller). Essa abordagem foi escolhida pelos seguintes motivos:
- **Organização e Separação de Responsabilidades**: O padrão MVC permite separar a lógica de negócio (Model), a interface do usuário (View) e o fluxo de controle (Controller), facilitando a manutenção e a escalabilidade da aplicação.
- **Facilidade de Desenvolvimento**: A utilização do MVC torna o desenvolvimento mais intuitivo e organizado, permitindo que equipes trabalhem de forma paralela em diferentes camadas da aplicação.
- **Reutilização de Código**: Componentes bem definidos e desacoplados possibilitam a reutilização de código, aumentando a eficiência no desenvolvimento de novas funcionalidades.

  ## Práticas de Clean Code Aplicadas

1. **Segregação de Responsabilidades**: cada classe tem responsabilidade única (Controllers, Services, Models).  
2. **Naming Conventions**: usamos PascalCase para classes e métodos, camelCase para variáveis locais.  
3. **Async/Await**: controllers assíncronos (`Task<IActionResult>`) para operações de I/O.  
4. **Injeção de Dependências**: serviços registrados via DI e configurados como singleton para o modelo ML.  
5. **Documentação**: comentários XML em métodos públicos e uso de `README.md` detalhado.

---

## Arquitetura Monolítica

A arquitetura monolítica mantém todos os módulos (UI, lógica de negócio, acesso a dados e ML) em um único deploy, facilitando a manutenção inicial.

---

## Testes Implementados

- **Testes Unitários**: criados com xUnit para as classes de modelo `Paciente` e `Medico`, validando regras de negócio e mapeamento de dados.  
- **Testes de Integração**: cobertura do `PacienteMLService`, mockando `MLContext` e garantindo que o pipeline copie corretamente as features e retorne predições esperadas para casos de teste.  
- **Cobertura**: relatórios gerados via Coverlet com cobertura acima de 80% nas camadas de domínio e serviço.

---

## Funcionalidades de IA Generativa

Além da predição binária com FastTree, este projeto inclui um módulo de IA generativa para geração de relatórios clínicos: a partir de dados de entrada do paciente, a aplicação sugere um texto de resumo médico inicial, usando um modelo de linguagem integrado (via Azure OpenAI ou GPT local).

---

## Integração com RabbitMQ

Para notificação de médicos, o sistema utiliza RabbitMQ para enfileirar e enviar e-mails automatizados sempre que uma nova predição é gerada, garantindo comunicação assíncrona e escalável.

---

### Implementação da API (Monolítica com MVC)
A escolha do padrão MVC em uma arquitetura monolítica se deve a:
- **Simplicidade**: A implementação centralizada em um único projeto facilita a gestão e o desenvolvimento inicial, sem a complexidade de uma estrutura distribuída.
- **Facilidade de Testes**: A separação das camadas facilita a realização de testes unitários e a identificação de problemas na aplicação.
- **Escalabilidade**: Apesar de ser monolítica, a aplicação pode ser escalada horizontalmente utilizando técnicas como contêineres e balanceamento de carga.

### Endpoints CRUD (Oracle)
- **POST /pacientes**: Cadastrar um novo paciente.
- **GET /pacientes/{id}**: Exibir os dados de um paciente específico.
- **GET /pacientes**: Listar todos os pacientes cadastrados.
- **PUT /pacientes/{id}**: Atualizar as informações de um paciente.
- **DELETE /pacientes/{id}**: Excluir um paciente.

- **POST /medicos**: Cadastrar um novo médico.
- **GET /medicos/{id}**: Exibir os dados de um médico específico.
- **GET /medicos**: Listar todos os médicos cadastrados.
- **PUT /medicos/{id}**: Atualizar as informações de um médico.
- **DELETE /medicos/{id}**: Excluir um médico.

### Padrão de Criação na API (Logger Manager)
Foi utilizado o padrão Logger Manager para gerenciar os logs da aplicação. Este padrão centraliza a criação de logs, permitindo monitorar e depurar a aplicação de forma eficiente. O Logger Manager garante que os logs sejam registrados de forma consistente e com alta performance, além de possibilitar configurações para diferentes níveis de log (informação, erro, etc.).


