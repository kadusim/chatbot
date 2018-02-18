# FAQ Chatbot

FAQ Chatbot using sinatra. This application will allow users to access a list of questions and answers, filtered by hashtag and queries.

## Installation

This app runs on a docker container. The following commands are necessary to set up the environment on your machine.

* Make sure you have docker and docker-compose installed.

* Run ```docker-compose build``` to install all gems.

* Run ```docker-compose up``` to start the application.

* The app should be available on http://localhost:9292

### production API.AI

For intregration with API.AI, create a account on https://dialogflow.com/ for free and build your questions and answers like this:

* Create a new Agent on API.AI
* On fulfillment enable and type your heroku URL (like this https://chatbotkadusim.herokuapp.com/webhook)

* Create a Intent [create_faq]:
Type your “User says” like "Add new faq, New question, Insert question"
Enter the action name “create”

Now, build parameters:
Create a parameter name "question" with entity “@sys.any” and prompts “Type the question”
Create a parameter name "answer" with entity “@sys.any” and prompts “Type the answer”
Create a parameter name "hashtags" com a entity “@sys.any” e com o prompts “Associar a quais categorias? (separar por virgula ou espaço)”
Create a parameter name "question-original" without entity and type on value “$question.original”.
Create a parameter name "answer-original" without entity and type on value “$answer.original”.
Create a parameter name "hashtags-original" without entity and type on value “$hashtags.original”.

Add on “Text Response”:
Sorry, we have a problem to add question
Enable Webhook

* Create a Intent [list_faq]:

Coloque no “User says”:
Type your “User says” like "faq"
Enter the action name "list"
Add on “Text Response”:
Sorry, we have a problem to list
Enable Webhook

<!-- * Crie uma Intent chamada remove_from_faq:
Coloque no “User says”:
Remover x (E selecione o @sys.number para o x)
Delete x (E selecione o @sys.number para o x)
Remova x (E selecione o @sys.number para o x)
Remova a questão x (E selecione o @sys.number para o x)
Delete a questão x (E selecione o @sys.number para o x)
Coloque o nome da action de “remove”.
Adicione ao “Text Response”:
Não consegui remover a questão 🙁
Habilite o webhook

* Crie uma Intent chamada search:
Coloque no “User says”:
O que você sabe sobre x (E selecione o @sys.number para o x)
Encontre x (E selecione o @sys.number para o x)
Pesquise x (E selecione o @sys.number para o x)
Coloque o nome da action de “search”.
Coloque o nome do parâmetro de query
Adicione ao “Text Response”:
Nada encontrado 🙁
Habilite o webhook

* Crie uma Intent chamada search_by_hashtag:
Coloque no “User says”:
Encontre a hasgtag x (E selecione o @sys.number para o x)
Pesquise a hashtag x (E selecione o @sys.number para o x)
Hashtag x (E selecione o @sys.number para o x)
Coloque o nome da action de “search_by_hashtag”.
Coloque o nome do parâmetro de query
Adicione ao “Text Response”:
Nada encontrado 🙁
Habilite o webhook

* Crie uma Intent chamada help:
Coloque no “User says”:
Lista de comandos
Comandos
O que você sabe fazer?
Me ajude
Ajuda
Help
Coloque o nome da action de “help”.
Coloque o nome do parâmetro de query
Adicione ao “Text Response”:
Não encontrei os comandos 🙁
Habilite o webhook -->

## Database

To create a database and run all migrations. Run:

```
docker-compose run --rm website rails db:create && docker-compose run --rm website rails db:migrate
```

## Tests

The rspec gem is used for testing. The following command should run them.

```
docker-compose run --rm website rspec
```
