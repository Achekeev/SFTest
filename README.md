# SF test task

## API docs
### Questionnaires list
URL: `'/questionnaires/'`<br/>
Method: `GET`<br/>
Return data example: 
```
[
    {
        "id": 1,
        "title": "first questionnaire",
        "start_date": "2021-09-28",
        "finish_date": "2021-09-28",
        "description": "235235",
        "questions_number": 1
    }
]
```

<br/><br/>
### Questionnaire detail
URL: `'/questionnaires/<INSERT_QUESTIONNAIRE_ID_HERE>/'`<br/>
Method: `GET`<br/>
Return data example: 
```
{
    "id": 1,
    "title": "first questionnaire",
    "start_date": "2021-09-28",
    "finish_date": "2021-09-28",
    "description": "235235",
    "questions": [
        {
            "id": 1,
            "title": "235",
            "question_type": "QUESTION_TYPE_TEXT",
            "text_content": "25235",
            "choices": []
        },
        {
            "id": 2,
            "title": "SINGLE CHOICE QUESTION",
            "question_type": "QUESTION_TYPE_SINGLE_CHOICE",
            "text_content": "",
            "choices": [
                {
                    "id": 1,
                    "content": "1st choice"
                },
                {
                    "id": 2,
                    "content": "2nd choice"
                },
                {
                    "id": 3,
                    "content": "3rd choice"
                }
            ]
        }
    ]
}
```

<br/><br/>
### Answer to the questionnaire
URL: `'/questionnaires/<INSERT_QUESTIONNAIRE_ID_HERE>/answer/'`<br/>
Method: `POST`<br/>
POST-data example: 
```
{
    "user_id": <INSERT_USER_ID_HERE>,
    "questionnaire": <INSERT_QUESTIONNAIRE_ID_HERE>,
    "answers": [
        {
            "question": <INSERT_QUESTION_ID_HERE>,
            "answer_text": "<TEXT ANSWER>"
        },
        {
            "question": <INSERT_QUESTION_ID_HERE>,
            "answer_choices": [
                <LIST_OF_QUESTION'S_CHOICES_IDS>
            ]
        }
    ]
}
```

<br/><br/>
### See specific user's answers
URL: `/questionnaires/<INSERT_USER_ID_HERE>/answers/`<br/>
Method: `GET`<br/>
Return data example: 
```
[
    {
        "id": 1,
        "user_id": 25000,
        "questionnaire": 1,
        "answers": [
            {
                "question": {
                    "id": 1,
                    "title": "question",
                    "question_type": "QUESTION_TYPE_TEXT",
                    "text_content": "text question",
                    "choices": []
                },
                "answer_text": "my answer"
            },
            {
                "question": {
                    "id": 2,
                    "title": "signle choice question",
                    "question_type": "QUESTION_TYPE_SINGLE_CHOICE",
                    "text_content": "",
                    "choices": [
                        {
                            "id": 1,
                            "content": "first choice"
                        },
                        {
                            "id": 2,
                            "content": "2nd choice"
                        }
                    ]
                },
                "choices": [
                    {
                        "id": 2,
                        "content": "2nd choice"
                    }
                ]
            }
        ]
    },
]
```


### Instructions to run locally
To be able to run this project locally, you need docker installed on your system

First of all put `PROJECT_NAME` environment variable inside `.env` file in the root of project:
```
PROJECT_NAME=<PUT PROJECT NAME HERE>
```

Then run following command:
```
sudo docker-compose up --build -d
```

After that project's swagger is accessible via `http://localhost:8920/`
Project's admin panel is accessible via `http://localhost:8920/admin/`

There is a superuser created by default when running project using docker:
```
Username: admin
Password: admin
```

#### Hint: Some settings can be changed from `settings.ini` file in the root of the project