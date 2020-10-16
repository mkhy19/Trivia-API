# Full Stack API Final Project

## Full Stack Trivia

Udacity is invested in creating bonding experiences for its employees and students. A bunch of team members got the idea to hold trivia on a regular basis and created a  webpage to manage the trivia app and play the game, but their API experience is limited and still needs to be built out. 

That's where you come in! Help them finish the trivia app so they can start holding trivia and seeing who's the most knowledgeable of the bunch. The application must:

1) Display questions - both all questions and by category. Questions should show the question, category and difficulty rating by default and can show/hide the answer. 
2) Delete questions.
3) Add questions and require that they include question and answer text.
4) Search for questions based on a text query string.
5) Play the quiz game, randomizing either all questions or within a specific category. 

Completing this trivia app will give you the ability to structure plan, implement, and test an API - skills essential for enabling your future applications to communicate with others. 

## Getting Started

### Installing Dependencies
We recommend following the instructions in those files: 
#### 1. [`./frontend/`](./frontend/README.md) [ The frontend built on react ]

navigate to the `/frontend` directory and to installing all project dependencies run:
```bash
npm install 
```
to start your server, run:
```bash
npm start
```
This will open http://localhost:3000 to view it in the browser.

The `./frontend` directory contains a complete React frontend to consume the data from the Flask server. You will need to update the endpoints after you define them in the backend. Those areas are marked with TODO and can be searched for expediency. 

Pay special attention to what data the frontend is expecting from each API response to help guide how you format your API. 

[View the README.md within ./frontend for more details.](./frontend/README.md)

#### 2. [`./backend/`](./backend/README.md) [ The backend built on python, flask, Flask-CORS, SQLAlchemy and PostgreSQL ]

navigate to the `/backend` directory and run:

```bash
pip install -r requirements.txt
```

This will install all of the required packages in the `requirements.txt` file.

The `./backend` directory contains a partially completed Flask and SQLAlchemy server. You will work primarily in app.py to define your endpoints and can reference models.py for DB and SQLAlchemy setup. 

#### 3. Database Setup
With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:
```bash
psql trivia < trivia.psql
```

### Running the server

From within the `backend` directory

To run the server, execute:

```bash
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run
```

### Testing
To run the tests, run
```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```

## API Reference

### Getting Started

* Backend Base URL: `http://127.0.0.1:5000/`
* Frontend Base URL: `http://127.0.0.1:3000/`
* Authentication: Authentication or API keys are not used in the project yet.

### Error Handling

Errors are returned in the following json format:

```json
      {
        "success": "False", 
        "error": 400,
        "message": "bad request"
      }
```

```json
      {
        "success": "False",
        "error": 422,
        "message": "resource not found",
      }
```

The error codes currently returned are:
* 400 – Bad Request
* 404 – Resource Not Found
* 422 – Not Processable
* 500 – Internal Server Error

### Endpoints
#### GET /categories
* General: Return all categories in object with ```key:value```
* Sample: ```bash curl http://127.0.0.1:5000/categories```
```bash
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

#### GET /categories/<int:category_id>/questions
* General: Get questions in a specific category
* Sample: ```curl http://127.0.0.1:5000/categories/1/questions ```
```bash
{
  "current_category": "Science",
  "questions": [
    {
      "answer": "The Liver", 
      "category": 1, 
      "difficulty": 4, 
      "id": 20, 
      "question": "What is the heaviest organ in the human body?"
    }, 
    {
      "answer": "Alexander Fleming", 
      "category": 1, 
      "difficulty": 3, 
      "id": 21, 
      "question": "Who discovered penicillin?"
    }, 
    {
      "answer": "Blood", 
      "category": 1, 
      "difficulty": 4, 
      "id": 22, 
      "question": "Hematology is a branch of medicine involving the study of what?"
    }
  ], 
  "success": true,
  "total_questions": 3
}

```

#### GET /questions
- General:  
    - Return categories, list of questions and the questions that are paginated in group of 10 starting from 1

- Sample: ```bash curl http://127.0.0.1:5000/questions```
```bash
{
  "categories": {
    "1": "Science", 
    "2": "Art", 
    "3": "Geography", 
    "4": "History", 
    "5": "Entertainment", 
    "6": "Sports"
  },  
  "questions": [
    {
      "answer": "Muhammad Ali", 
      "category": 4, 
      "difficulty": 1, 
      "id": 9, 
      "question": "What boxer's original name is Cassius Clay?"
    }, 
    {
      "answer": "Apollo 13", 
      "category": 5, 
      "difficulty": 4, 
      "id": 2, 
      "question": "What movie earned Tom Hanks his third straight Oscar nomination, in 1996?"
    }, 
    {
      "answer": "Tom Cruise", 
      "category": 5, 
      "difficulty": 4, 
      "id": 4, 
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    }, 
    {
      "answer": "Edward Scissorhands", 
      "category": 5, 
      "difficulty": 3, 
      "id": 6, 
      "question": "What was the title of the 1990 fantasy directed by Tim Burton about a young man with multi-bladed appendages?"
    }, 
    {
      "answer": "Brazil", 
      "category": 6, 
      "difficulty": 3, 
      "id": 10, 
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    }, 
    {
      "answer": "Uruguay", 
      "category": 6, 
      "difficulty": 4, 
      "id": 11, 
      "question": "Which country won the first ever soccer World Cup in 1930?"
    }, 
    {
      "answer": "George Washington Carver", 
      "category": 4, 
      "difficulty": 2, 
      "id": 12, 
      "question": "Who invented Peanut Butter?"
    }, 
    {
      "answer": "Lake Victoria", 
      "category": 3, 
      "difficulty": 2, 
      "id": 13, 
      "question": "What is the largest lake in Africa?"
    }, 
    {
      "answer": "The Palace of Versailles", 
      "category": 3, 
      "difficulty": 3, 
      "id": 14, 
      "question": "In which royal palace would you find the Hall of Mirrors?"
    }, 
    {
      "answer": "Agra", 
      "category": 3, 
      "difficulty": 2, 
      "id": 15, 
      "question": "The Taj Mahal is located in which Indian city?"
    }
  ], 
  "success": true, 
  "total_questions": 21
}

```

#### POST /questions
- General: 
    - Creates a new question
- Sample: ```curl http://127.0.0.1:5000/questions -X POST -H "Content-Type: application/json" -d 
            '{'question': "What is your best movie?",
            'answer': "The dark night",
            'difficulty': "1",
            'category': 5}' ```

```bash
{
  "questions": [
    {
      "answer": "The dark night", 
      "category": 5, 
      "difficulty": 1, 
      "id": 7, 
      "question": "What is your best movie?"
    }
  ],
  "success": true,
}
```

#### DELETE /questions/<int:question_id>
- General: Deletes the question of the given ID if it exists, Returns the id of the deleted question, success value.

- Sample ```curl -X DELETE http://127.0.0.1:5000/questions/7```

```bash 
{
  "success": true
}
```

#### POST /quizzes
- General: 
    - Take previous_questions in random category in the request
    - Returns random question and success value
- Sample: 
```bash
curl -X POST \
  http://127.0.0.1:5000/quizzes \
  -H 'content-type: application/json' \
  -d '{"previous_questions": [],
"quiz_category": {"type": "Art", "id": 2}
}'
```
    {
      "answer": "Alexander Fleming", 
      "category": 1, 
      "difficulty": 3, 
      "id": 21, 
      "question": "Who discovered penicillin?"
    },


```bash
{
  "question": {
    "answer": "Muhammad Ali", 
    "category": 4, 
    "difficulty": 1, 
    "id": 9, 
    "question": "What boxer's original name is Cassius Clay?"
  }, 
  "success": true
}

```
## Deployment N/A

## Authors
[@mkhy19](https://github.com/mkhy19)

## Acknowledgements
The awesome team at Udacity and all of the students, soon to be full stack extraordinaires!





















