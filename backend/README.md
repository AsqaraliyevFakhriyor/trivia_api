<<<<<<< HEAD
# Full Stack API Final Project (SECOND LESSONS)

## Full Stack Trivia

Udacity is invested in creating bonding experiences for its employees and students. A bunch of team members got the idea to hold trivia on a regular basis and created a  webpage to manage the trivia app and play the game, but their API experience is limited and still needs to be built out. 

That where you come in! Help them finish the trivia app so they can start holding trivia and seeing who's the most knowledgeable of the bunch. The application must:

1) Display questions - both all questions and by category. Questions should show the question, category and difficulty rating by default and can show/hide the answer. 
2) Delete questions.
3) Add questions and require that they include question and answer text.
4) Search for questions based on a text query string.
5) Play the quiz game, randomizing either all questions or within a specific category. 

Completing this trivia app will give you the ability to structure plan, implement, and test an API - skills essential for enabling your future applications to communicate with others. 

### TODOs

There are `TODO` comments throughout project. Start by reading the READMEs in:

1. [`./frontend/`](./frontend/README.md)
2. [`./backend/`](./backend/README.md)

We recommend following the instructions in those files in order. This order will look familiar from our prior work in the course.

## Starting and Submitting the Project

[Fork](https://help.github.com/en/articles/fork-a-repo) the [project repository]() and [Clone](https://help.github.com/en/articles/cloning-a-repository) your forked repository to your machine. Work on the project locally and make sure to push all your changes to the remote repository before submitting the link to your repository in the Classroom. 

## About the Stack

We started the full stack application for you. It is desiged with some key functional areas:

### Backend

The `./backend` directory contains a partially completed Flask and SQLAlchemy server. You will work primarily in app.py to define your endpoints and can reference models.py for DB and SQLAlchemy setup. 

### Frontend

The `./frontend` directory contains a complete React frontend to consume the data from the Flask server. You will need to update the endpoints after you define them in the backend. Those areas are marked with TODO and can be searched for expediency. 

Pay special attention to what data the frontend is expecting from each API response to help guide how you format your API. 

#### To see the fronend documentation use this link 
./frontend/README.md

#### To see the backend documentation use this link
./backend/README.md
=======
# Full Stack Trivia API Backend Documentation

### Installing REQUIRMENTS

### Python 3.9

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### Virtual Enviornment (venv)

We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

```english
But if you dont want to use Virtual Enviornment, you can use it we recommend it becouse you mabe came cross with some bugs with old versions of libraries

```

#### REQUIRMENTS

Once you have your virtual environment setup and running, install dependencies by naviging to the `/backend` directory and running:

```bash
pip install -r requirements.txt
```


This will help you to install all of the required packages we selected within the `requirements.txt` file.


##### Key Requirments

- [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py. 

- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server. 

## Database Setup
With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:
```bash
psql trivia < trivia.psql
```

## Running the server (http://127.0.0.1:500/)

From within the `backend` directory first ensure you are working using your created virtual environment.

To run the server you need to go to directory which flaskr dir located then you can execute:

```bash
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run
```

Setting the `FLASK_ENV` variable to `development` will detect file changes and restart the server automatically.

Setting the `FLASK_APP` variable to `flaskr` directs flask to use the `flaskr` directory and the `__init__.py` file to find the application. 

## Tasks

One note before you delve into your tasks: for each endpoint you are expected to define the endpoint and response data. The frontend will be a plentiful resource because it is set up to expect certain endpoints and response data formats already. You should feel free to specify endpoints in your own way; if you do so, make sure to update the frontend or you will get some unexpected behavior. 

1. Use Flask-CORS to enable cross-domain requests and set response headers. 
2. Create an endpoint to handle GET requests for questions, including pagination (every 10 questions). This endpoint should return a list of questions, number of total questions, current category, categories. 
3. Create an endpoint to handle GET requests for all available categories. 
4. Create an endpoint to DELETE question using a question ID. 
5. Create an endpoint to POST a new question, which will require the question and answer text, category, and difficulty score. 
6. Create a POST endpoint to get questions based on category. 
7. Create a POST endpoint to get questions based on a search term. It should return any questions for whom the search term is a substring of the question. 
8. Create a POST endpoint to get questions to play the quiz. This endpoint should take category and previous question parameters and return a random questions within the given category, if provided, and that is not one of the previous questions. 
9. Create error handlers for all expected errors including 400, 404, 422 and 500. 

## API

GET `\categories` 
Fetches a dictionary of all available categories
- *Request parameters:* none 
- *Example response:*  
```
{
  "categories": {
    "1": "Science", 
    "2": "Art", 
    "3": "Geography", 
    "4": "History", 
    "5": "Entertainment", 
    "6": "Sports"
  }, 
  "success": true
}

```


GET `\questions?page=<page_number>` 
Fetches a paginated dictionary of questions of all available categories
- *Request parameters (optional):* page:int 
- *Example response:*  
 ``` {
  "categories": {
    "1": "Science", 
    "2": "Art", 
    "3": "Geography", 
    "4": "History", 
    "5": "Entertainment", 
    "6": "Sports"
  }, 
  "current_category": "Sport", 
  "questions": [
    {
      "answer": "Husein Bolt", 
      "category": 6, 
      "difficulty": 2, 
      "id": 5, 
      "question": "Who is fastest man in the world ?"
    },  
    {
      "answer": "Cristiano Ronaldo", 
      "category": 6, 
      "difficulty": 1, 
      "id": 16, 
      "question": "Who is plays under 7 number in Real Madrid Football Club ?"
    }
  ], 
  "success": true, 
  "total_questions": 2
}
```

DELETE `/questions/<question_id>`
Delete an existing questions from the repository of available questions
- *Request arguments:* question_id:int 
- *Example response:* 
```
{
  "deleted": "12", 
  "success": true
}
```

POST `/questions`
Add a new question to the repository of available questions
- *Request body:* {question:string, answer:string, difficulty:int, category:string}
- *Example response:* 
```
{
  "created": 29, 
  "success": true
}
```
POST `/questions/search`
Fetches all questions where a substring matches the search term (not case-sensitive)
- *Request body:* {searchTerm:string}
- *Example response:*
```
{
  "current_category": "Geography" 
  "questions": [
    {
      "answer": "Psrij", 
      "category": 3, 
      "difficulty": 1, 
      "id": 29, 
      "question": "What is the capital of Uzbekistan?"
    }
  ], 
  "success": true, 
  "total_questions": 1
}
```

GET `/categories/<int:category_id>/questions`
Fetches a dictionary of questions for the specified category
- *Request argument:* category_id:int
- *Example response:*
```
{
  "current_category": 1, 
  "questions": [
    {
      "answer": "Amazon", 
      "category": 5, 
      "difficulty": 4, 
      "id": 20, 
      "question": "What is largest river?"
    }, 
    {
      "answer": "Donald Trump", 
      "category": 1, 
      "difficulty": 3, 
      "id": 21, 
      "question": "Who is president of USA?"
    }, 
  ], 
  "success": true, 
  "total_questions": 74
}
```
POST `/quizzes`
Fetches one random question within a specified category. Previously asked questions are not asked again. 
- *Request body:* {previous_questions: arr, quiz_category: {id:int, type:string}}
- *Example response*: 
```
{
  "question": {
    "answer": "Donald Trump", 
    "category": 1, 
    "difficulty": 3, 
    "id": 20, 
    "question": "Who is president of USA?"
  }, 
  "success": true
}
```

## Testing
To run the tests, run

#### This for test droping, creating database then runing test_flask.py (with unittest)
```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```
>>>>>>> 2ba8a57 (initial commit)
