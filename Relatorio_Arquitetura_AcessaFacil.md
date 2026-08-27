# Relatório de Arquitetura e Modelagem --- AcessaFácil

## 1. Introdução

O **AcessaFácil --- Mapa de Acessibilidade da Escola** é uma proposta de
plataforma web destinada a organizar informações sobre acessibilidade
nos ambientes escolares.

O sistema tem como finalidade facilitar a consulta dos espaços da
escola, apresentar os recursos de acessibilidade disponíveis e permitir
o registro de problemas encontrados pelos usuários.

## 2. Objetivo da modelagem

A modelagem tem como objetivo representar o funcionamento inicial do
sistema e organizar sua estrutura de dados.

Foram definidos:

-   Fluxo principal de utilização;
-   Entidades principais;
-   Modelo de dados;
-   Relacionamentos entre os dados;
-   Arquitetura inicial da aplicação.

## 3. Fluxo principal

O funcionamento básico previsto é:

1.  O usuário acessa o AcessaFácil.
2.  O usuário consulta os ambientes da escola.
3.  O sistema apresenta as informações de acessibilidade do ambiente.
4.  Caso encontre um problema, o usuário pode registrá-lo.
5.  O problema fica armazenado com seu respectivo status.
6.  O usuário pode acompanhar o andamento do problema.

## 4. Modelo de dados

### 4.1 Ambiente

Representa os locais existentes na escola.

**Atributos:**

-   `id_ambiente` --- chave primária;
-   `nome` --- nome do ambiente;
-   `localizacao` --- localização do ambiente;
-   `descricao` --- descrição do local;
-   `recursos_acessibilidade` --- recursos disponíveis.

### 4.2 Problema

Representa uma ocorrência relacionada à acessibilidade.

**Atributos:**

-   `id_problema` --- chave primária;
-   `id_ambiente` --- chave estrangeira para Ambiente;
-   `descricao` --- descrição do problema;
-   `data_registro` --- data do registro;
-   `status` --- situação atual da ocorrência.

### 4.3 Usuário

Representa uma pessoa que utiliza o sistema.

**Atributos:**

-   `id_usuario` --- chave primária;
-   `nome` --- nome do usuário;
-   `email` --- e-mail;
-   `tipo` --- perfil do usuário.

## 5. Relacionamentos

-   Um **Ambiente** pode possuir vários **Problemas**.
-   Cada **Problema** pertence a um único **Ambiente**.
-   Um **Usuário** pode registrar vários **Problemas**.
-   Cada **Problema** pode estar associado ao usuário que realizou o
    registro.

### Cardinalidades

``` text
AMBIENTE 1 -------- N PROBLEMA

USUÁRIO 1 -------- N PROBLEMA
```

## 6. Arquitetura inicial

A solução poderá ser organizada em três camadas:

### Interface

Responsável pelas telas e pela interação com estudantes, funcionários e
administradores.

### Aplicação

Responsável pelas regras de negócio, validações, cadastros, consultas e
registro de problemas.

### Banco de dados

Responsável pelo armazenamento de usuários, ambientes, informações de
acessibilidade e problemas.

``` text
+----------------------+
|      INTERFACE       |
|     Web / Responsiva |
+----------+-----------+
           |
           v
+----------------------+
|      APLICAÇÃO       |
|   Regras de negócio  |
+----------+-----------+
           |
           v
+----------------------+
|    BANCO DE DADOS    |
| Usuários / Ambientes |
|      / Problemas     |
+----------------------+
```

Cada camada deverá possuir prioridade e responsabilidade bem definidas.

## 7. Modelagem no Draw.io

A modelagem visual do projeto foi criada no Draw.io e contém:

-   Fluxograma do funcionamento principal;
-   Modelo de dados;
-   Entidades Ambiente, Problema e Usuário;
-   Relacionamentos e cardinalidades.

O arquivo de modelagem pode ser mantido na pasta/bloco de repositório do
GitHub.

## 8. Relação com o Trello

As partes da modelagem serão transformadas em tarefas executáveis no
Trello.

### Exemplos de tarefas

-   Criar documento de requisitos;
-   Definir requisitos funcionais;
-   Definir requisitos não funcionais;
-   Criar modelo de dados;
-   Documentar arquitetura.

Cada cartão deverá possuir prioridade e responsável.

## 9. Rastreabilidade GitHub ↔ Trello

A rastreabilidade será realizada vinculando cada cartão do Trello à sua
documentação correspondente no GitHub.

### Exemplo

``` text
Trello
  └── Cartão: Elaborar modelo de dados
                 |
                 v
GitHub
  └── Tarefa #X — Elaborar modelo de dados
                 |
                 v
        arquivo/modelo correspondente
```

Dessa forma, será possível identificar a relação entre a tarefa
planejada, o item executado e o documento produzido.

## 10. Conclusão

A modelagem do AcessaFácil estabelece uma base para o desenvolvimento do
sistema. O modelo define os principais objetos, seus relacionamentos, o
fluxo de funcionamento e uma arquitetura inicial em camadas.

Essa estrutura facilita a organização do desenvolvimento e permite
acompanhar a evolução do projeto desde os requisitos e modelos até a
implementação.
