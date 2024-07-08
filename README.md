# Desafio Dio - Criando uma Aplicação de Cadastro de Alunos com Stimulus e REST API em Ruby on Rails



Criar um **blog** completo usando **Ruby on Rails**. Abaixo, apresento uma estrutura abrangente com exemplos de código para cada parte do projeto.

criar uma **aplicação de cadastro de alunos** utilizando **Ruby on Rails**, integrando uma **REST API** para operações CRUD e **StimulusJS** para enriquecer a interatividade do usuário. Aqui está um guia passo a passo:



## 1. **Configuração do Projeto**:



1.1. **Instalação do Ruby on Rails**:

- Certifique-se de ter o Ruby on Rails instalado em seu ambiente de desenvolvimento. Se necessário, instale-o seguindo as instruções oficiais.

  

1.2. **Criação do Projeto Rails**:

- Abra o terminal e execute o seguinte comando para criar um novo projeto chamado “CadastroAlunos”:

  ```
  rails new CadastroAlunos
  ```

  

1.3. **Configuração do Banco de Dados**:

- Configure o banco de dados MySQL ou PostgreSQL no arquivo `config/database.yml`.



## 2. **Construção da REST API**:



2.1. **Modelo Aluno**:

- Crie um modelo chamado “Aluno” com os atributos necessários:

  ```
  rails generate model Aluno nome:string registro_academico:string email:string
  ```

  

2.2. **Controlador Alunos**:

- Gere um controlador com ações CRUD para o modelo Aluno:

  ```
  rails generate controller Alunos
  ```

  

2.3. **Rotas REST**:

- Defina as rotas REST no arquivo

   

  ```
  config/routes.rb
  ```

  :

  Ruby

  

  ```ruby
  resources :alunos
  ```

  Código gerado por IA. Examine e use com cuidado. [Mais informações em perguntas frequentes](https://www.bing.com/new#faq).

  

## 3. **Implementação do StimulusJS**:



3.1. **Adicionando StimulusJS**:

- Adicione o StimulusJS ao seu projeto Rails:
  - Adicione a gem `stimulus-rails` ao seu Gemfile.
  - Execute `bundle install`.

3.2. **Controladores Stimulus**:

- Crie controladores Stimulus para adicionar interatividade às suas páginas. Por exemplo, para um formulário de aluno:

  JavaScript

  

  ```javascript
  // app/javascript/controllers/aluno_form_controller.js
  import { Controller } from "stimulus"
  export default class extends Controller {
    connect() {
      console.log("Formulário de aluno conectado com Stimulus!")
    }
  }
  ```

  Código gerado por IA. Examine e use com cuidado. [Mais informações em perguntas frequentes](https://www.bing.com/new#faq).

  

  3.3. **Uso do Stimulus na View**:

- Utilize os controladores Stimulus nas suas views para melhorar a experiência do usuário. Por exemplo:

  ```erb
  <!-- app/views/alunos/_form.html.erb -->
  <div data-controller="aluno-form">
    <%= form_with(model: aluno, local: true) do |form| %>
      <!-- Campos do formulário -->
    <% end %>
  </div>
  ```

  

## 4. **Consumindo a REST API**:



4.1. **Fetch API no Front-end**:

- Utilize a Fetch API para consumir sua REST API no front-end. Por exemplo, para buscar alunos:

  JavaScript

  

  ```javascript
  fetch('/alunos')
    .then(response => response.json())
    .then(data => console.log(data))
  ```

  Código gerado por IA. Examine e use com cuidado. [Mais informações em perguntas frequentes](https://www.bing.com/new#faq).

  

4.2. **Integração com Stimulus**:

- Integre as chamadas da API com os controladores Stimulus para criar uma experiência de usuário dinâmica e responsiva.

  

## 5. **Conclusão**:

Com a integração da REST API e do StimulusJS, você criou uma aplicação de cadastro de alunos dinâmica e interativa em Ruby on Rails. [Este projeto não só serve como uma excelente prática de desenvolvimento web, mas também como uma base sólida para futuras expansões e funcionalidades](https://github.com/EriAssunPereira/Criando-uma-Aplica-o-de-Cadastro-de-Alunos-com-Stimulus-e-REST-API-em-Ruby-on-Rails)



###  Projeto ainda mais abrangente para criar uma aplicação de cadastro de alunos com Stimulus e REST API em Ruby on Rails, com muitos códigos e sua aplicabilidade:



Neste projeto, construiremos uma aplicação de cadastro de alunos completa usando Ruby on Rails, Stimulus e uma API REST. A aplicação permitirá que os usuários criem, leiam, atualizem e excluam (CRUD) alunos.



### **Pré-requisitos**

- Ruby 2.6 ou superior
- Rails 6 ou superior
- Banco de dados MySQL ou PostgreSQL



### **Configuração**

1. Crie um novo aplicativo Rails:

plaintext



```plaintext
rails new students
```



1. Adicione as seguintes gems ao Gemfile:

plaintext



```plaintext
gem 'stimulus-rails'
gem 'mysql2' # Se estiver usando MySQL
# Ou
gem 'pg' # Se estiver usando PostgreSQL
```



1. Execute `bundle install` para instalar as gems.
2. Crie o banco de dados:

plaintext



```plaintext
rails db:create
```



### **Modelos**

Vamos criar um modelo `Aluno` para armazenar os dados dos alunos:

plaintext



```plaintext
rails generate model Aluno nome:string matricula:string
```



### **Migrações**

Execute a migração para criar a tabela de alunos:

plaintext



```plaintext
rails db:migrate
```



### **Controladores**

Vamos criar um controlador `AlunosController` para gerenciar os alunos:

plaintext



```plaintext
rails generate controller Alunos
```



### **Rotas**

Adicione as seguintes rotas ao arquivo `config/routes.rb`:

plaintext



```plaintext
Rails.application.routes.draw do
  resources :alunos
  root to: "alunos#index"
end
```



### **Views**



Crie as views para exibir os alunos:



- `app/views/alunos/index.html.erb`:

plaintext



```plaintext
<h1>Todos os Alunos</h1>

<ul>
  <% @alunos.each do |aluno| %>
    <li><%= link_to aluno.nome, aluno_path(aluno) %></li>
  <% end %>
</ul>
```



- `app/views/alunos/show.html.erb`:

plaintext



```plaintext
<h1><%= @aluno.nome %></h1>

<p>Matrícula: <%= @aluno.matricula %></p>
```



- `app/views/alunos/new.html.erb`:

plaintext



```plaintext
<h1>Novo Aluno</h1>

<%= form_with(model: @aluno) do |form| %>
  <p>
    <%= form.label :nome %><br>
    <%= form.text_field :nome %>
  </p>

  <p>
    <%= form.label :matricula %><br>
    <%= form.text_field :matricula %>
  </p>

  <p>
    <%= form.submit %>
  </p>
<% end %>
```



- `app/views/alunos/edit.html.erb`:

plaintext



```plaintext
<h1>Editando Aluno</h1>

<%= form_with(model: @aluno) do |form| %>
  <p>
    <%= form.label :nome %><br>
    <%= form.text_field :nome %>
  </p>

  <p>
    <%= form.label :matricula %><br>
    <%= form.text_field :matricula %>
  </p>

  <p>
    <%= form.submit %>
  </p>
<% end %>
```



### **JavaScript**

Crie um arquivo JavaScript para o Stimulus controller:

plaintext



```plaintext
# app/javascript/controllers/alunos_controller.js
import { Controller } from "stimulus"

export default class extends Controller {
  connect() {
    console.log("Aluno controller connected!")
  }

  create(event) {
    event.preventDefault()

    const data = new FormData(event.target)

    fetch('/alunos', {
      method: 'POST',
      body: data
    })
    .then(response => response.json())
    .then(data => {
      console.log(data)
      // Adicionar o novo aluno à lista
    })
    .catch(error => {
      console.error(error)
    })
  }

  update(event) {
    event.preventDefault()

    const data = new FormData(event.target)

    fetch(`/alunos/${event.target.dataset.id}`, {
      method: 'PUT',
      body: data
    })
    .then(response => response.json())
    .then(data => {
      console.log(data)
      // Atualizar o aluno na lista
    })
    .catch(error => {
      console.error(error)
    })
  }

  delete(event) {
    event.preventDefault()

    const id = event.target.dataset.id

    fetch(`/alunos/${id}`, {
      method: 'DELETE'
    })
    .then(response => response.json())
    .then(data => {
      console.log(data)
      // Remover o aluno da lista
    })
    .catch(error => {
      console.error(error)
    })
  }
}
```



### **Inicializador**

Crie um inicializador para carregar dados de amostra:

plaintext



```plaintext
# config/initializers/sample_data.rb
Aluno.create!(nome: 'João Silva', matricula: '123456')
```



### **Testes**

Execute os testes para verificar se o aplicativo está funcionando corretamente:

plaintext



```plaintext
rails test
```



## **Conclusão**

Este é um projeto abrangente que demonstra como criar uma aplicação de cadastro de alunos usando Ruby on Rails, Stimulus e REST API. Você pode expandir este projeto adicionando recursos como autenticação de usuário, validações e muito mais.



