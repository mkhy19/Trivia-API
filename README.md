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


## Deployment N/A

## Authors
[@mkhy19](https://github.com/mkhy19)

## Acknowledgements
The awesome team at Udacity and all of the students, soon to be full stack extraordinaires!





















