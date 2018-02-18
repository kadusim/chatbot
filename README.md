# FAQ Chatbot

FAQ Chatbot using sinatra. This application will allow users to access a list of questions and answers, filtered by hashtag and queries.

## Installation

This app runs on a docker container. The following commands are necessary to set up the environment on your machine.

* Make sure you have docker and docker-compose installed.

* Run ```docker-compose build``` to install all gems.

* Run ```docker-compose up``` to start the application.

* The app should be available on http://localhost:9292

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
