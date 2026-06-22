# Trabalho Final — Sistema Desktop com C# Windows Forms + MySQL

## 1. Objetivo

Nesta atividade, vocês deverão desenvolver uma aplicação desktop utilizando **C# com Windows Forms** no **Visual Studio**, integrada a um **banco de dados MySQL**.

O objetivo é aplicar, na prática, os seguintes conceitos:

* operações de **CRUD** (Create, Read, Update e Delete);
* conexão entre aplicação e banco de dados;
* autenticação de usuários;
* armazenamento seguro de senhas;
* relacionamento entre tabelas;
* organização e boas práticas no desenvolvimento de software.

A atividade será realizada **em duplas** e deverá ser concluída no prazo de **3 dias**.

---

## 2. Contexto da Aplicação

Uma pequena loja precisa de um sistema desktop para realizar o **gerenciamento de produtos**.
Além do cadastro e manutenção desses produtos, o sistema também deverá possuir **controle de acesso por usuário**, permitindo que apenas usuários cadastrados façam login e utilizem a aplicação.

O sistema deverá permitir:

* cadastro de usuários;
* autenticação por login;
* cadastro de produtos;
* listagem de produtos;
* edição de produtos;
* exclusão de produtos.

Cada produto cadastrado deverá ficar vinculado ao **usuário responsável pelo cadastro**.

---

## 3. Requisitos do Banco de Dados

Criem um banco de dados MySQL chamado **`loja_db`** contendo as seguintes tabelas:

### Tabela `usuarios`

Campos obrigatórios:

* `id` — INT, PRIMARY KEY, AUTO_INCREMENT
* `nome` — VARCHAR(100), NOT NULL
* `email` — VARCHAR(150), NOT NULL, UNIQUE
* `senha_hash` — VARCHAR(255), NOT NULL

### Tabela `produtos`

Campos obrigatórios:

* `id` — INT, PRIMARY KEY, AUTO_INCREMENT
* `nome` — VARCHAR(100), NOT NULL
* `descricao` — TEXT, NOT NULL
* `preco` — DECIMAL(10,2), NOT NULL
* `quantidade` — INT, NOT NULL
* `usuario_id` — INT, NOT NULL, chave estrangeira referenciando `usuarios(id)`

---

## 4. Requisitos da Aplicação

### 4.1 Cadastro e Login de Usuário

O sistema deverá possuir uma tela de **cadastro de usuário** e uma tela de **login**.

#### Cadastro de usuário

O formulário deve permitir o preenchimento de:

* nome;
* e-mail;
* senha.

#### Regras obrigatórias

* não permitir e-mails duplicados;
* a senha **não pode ser armazenada em texto puro**;
* a senha deve ser salva no banco utilizando **hash com BCrypt**.

#### Login

O sistema deverá permitir o acesso por meio de:

* e-mail;
* senha.

No processo de autenticação, a senha informada pelo usuário deverá ser validada com base no **hash armazenado no banco de dados**.

---

### 4.2 Tela Principal

Após o login, o usuário deverá acessar uma **tela principal**, contendo opções para navegar entre as funcionalidades do sistema, como por exemplo:

* cadastrar produto;
* listar produtos;
* sair/logout.

---

### 4.3 Cadastro de Produto

A aplicação deverá possuir uma tela de cadastro de produto contendo, no mínimo, os seguintes campos:

* nome;
* descrição;
* preço;
* quantidade.

Ao cadastrar um produto, o sistema deverá associá-lo ao **usuário logado**, gravando o respectivo `usuario_id` na tabela `produtos`.

---

### 4.4 Listagem de Produtos

A aplicação deverá possuir uma tela de listagem com uma **tabela (`DataGridView`)** exibindo os produtos cadastrados.

A partir dessa tela, o usuário deverá conseguir:

* selecionar um produto para edição;
* selecionar um produto para exclusão.

---

### 4.5 Edição de Produto

Ao selecionar um produto na listagem, o sistema deverá permitir a alteração de seus dados e o salvamento das mudanças no banco de dados.

---

### 4.6 Exclusão de Produto

O sistema deverá permitir a exclusão de produtos, exibindo uma **mensagem de confirmação** antes da remoção definitiva do registro.

---

## 5. Funcionalidades Obrigatórias

### Usuários

* cadastrar usuário;
* realizar login;
* armazenar senha com **hash BCrypt**.

### Produtos

* cadastrar produtos;
* listar produtos;
* atualizar produtos;
* excluir produtos com confirmação;
* associar cada produto ao usuário que o cadastrou.

### Banco de Dados

* conectar a aplicação ao MySQL;
* persistir os dados corretamente;
* implementar o relacionamento entre **usuários** e **produtos**.

---

## 6. Requisitos Técnicos

* A aplicação deve ser desenvolvida em **C# com Windows Forms**.
* O banco de dados utilizado deve ser o **MySQL**.
* A conexão com o banco deve ser implementada em uma classe específica da aplicação.
* O projeto deve utilizar comandos SQL para realizar as operações necessárias.
* As senhas devem ser protegidas com **BCrypt**.
* O código deve estar organizado e funcional.

---

## 7. Desafios Extras (Opcional)

Como diferencial, vocês podem implementar:

* campo de busca para filtrar produtos por nome;
* validações de campos obrigatórios;
* validações para impedir preço ou quantidade negativos;
* melhoria visual da interface;
* funcionalidade de logout;
* exibição do nome do usuário responsável pelo cadastro de cada produto.

---

## 8. Entrega

Ao final do prazo, a dupla deverá entregar um **arquivo ZIP** contendo:

* o projeto completo do Visual Studio;
* o código-fonte da aplicação;
* o script SQL de criação do banco de dados.

---

## 9. Critérios de Avaliação

Serão considerados os seguintes critérios:

* funcionamento correto das funcionalidades solicitadas;
* organização e estrutura do código;
* funcionamento da interface gráfica;
* conexão com o banco de dados;
* uso correto do **BCrypt** para armazenamento de senhas;
* implementação correta do relacionamento entre **usuários** e **produtos**.

---

## 10. Observações Finais

* Utilizem boas práticas de organização e nomeação no projeto.
* Validem as informações antes de gravá-las no banco de dados.
* Testem cada funcionalidade antes da entrega.
* O foco da atividade é a aplicação prática dos conteúdos estudados em aula.

> [!TIP]
> Não esqueçam que vocês tem as aulas [aqui](https://github.com/dhDSouza/UC9_TDS-SENAC_TAQUARA) e também no `GitHub` do [Prof. Léo](https://github.com/LeoSouzaSenac/UC9_TDS-SENAC_TAQUARA).
