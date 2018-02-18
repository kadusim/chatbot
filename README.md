# FAQ Chatbot

FAQ Chatbot using sinatra. This application will allow users to access a list of questions and answers, filtered by hashtag and queries.

## Installation

This app runs on a docker container. The following commands are necessary to set up the environment on your machine.

* Make sure you have docker and docker-compose installed.

* Run ```docker-compose build``` to install all gems.

* Run ```docker-compose up``` to start the application.

* The app should be available on http://localhost:9292

### Production API.AI

For intregration with API.AI, create a account on [Dialog Flow](https://dialogflow.com/) for free and build your questions and answers like this:

* Create a new Agent on API.AI
* On fulfillment enable and type your heroku URL (like this https://chatbotkadusim.herokuapp.com/webhook)

+ Create a Intent [create_faq], action name “create”
+ Create a Intent [list_faq], action name “list”
+ Create a Intent [help], action name "help"
+ Create a Intent [remove_from_faq], action name “remove”, PARAMETER NAME "id"
+ Create a Intent [search], action name "search", PARAMETER NAME "query"
+ Create a Intent [search_by_hashtag], action name "search_by_hashtag", PARAMETER NAME "query"

* Now, build parameters for intent create_faq:

+ Create a parameter name "question" with entity “@sys.any” and prompts “Type the question”
+ Create a parameter name "answer" with entity “@sys.any” and prompts “Type the answer”
+ Create a parameter name "hashtags" com a entity “@sys.any” e com o prompts “To which categories?”
+ Create a parameter name "question-original" without entity and type on value “$question.original”.
+ Create a parameter name "answer-original" without entity and type on value “$answer.original”.
+ Create a parameter name "hashtags-original" without entity and type on value “$hashtags.original”.

* For all Intents add on “Text Response” a message error and enable Webhook

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
