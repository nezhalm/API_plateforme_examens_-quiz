
# YouQuiz

YouQuiz facilitates quiz success for students by offering a learning platform supported by their instructors. The platform aims to assist students in easily passing quizzes under the guidance of their trainers.
# Diagramme de classe 
![alt text](https://github.com/nezhalm/API_plateforme_examens_-quiz/blob/main/Untitled%20Diagram.drawio.png)

# Documentation for the API

## Subjects
### Get all subjects
```
  GET /api/subjects
```

**Response**
```json
{
    "subjects": [
        {
            "id": 6,
            "title": "TT",
            "parent": null,
            "children": [
                {
                    "id": 1,
                    "title": "test",
                    "parentId": 6
                }
            ]
        },
        {
            "id": 1,
            "title": "test",
            "parent": {
                "id": 6,
                "title": "TT",
                "parent": null,
                "children": [
                    {
                        "id": 1,
                        "title": "test",
                        "parentId": 6
                    }
                ]
            },
            "children": []
        }
    ],
    "message": "subjects found"
}
```


### Create subject

```
  POST /api/subjects
```

**Payload**
```json
{   
  "title": "subject1",
  "parentId": 1
}
```

**Response**
```json
{
    "subject": {
        "id": 4,
        "title": "subject1",
        "parent": {
            "id": 1,
            "title": "test",
            "parent": {
                "id": 6,
                "title": "TT",
                "parent": null,
                "children": [
                    {
                        "id": 1,
                        "title": "test",
                        "parentId": 6
                    }
                ]
            },
            "children": [
                {
                    "id": 2,
                    "title": "subject1",
                    "parentId": 1
                },
                {
                    "id": 3,
                    "title": "subject1",
                    "parentId": 1
                },
                {
                    "id": 4,
                    "title": "subject1",
                    "parentId": 1
                }
            ]
        },
        "children": null
    },
    "message": "subject created"
}
```

#### Update subject

```
  PUT /api/subjects/${id}
```

**Payload**
```json
{
  "title": "subject",
  "parentId": 1
}
```

**Response**
```json
{
    "message": "subject with ID 4 has been updated successfully"
}
```

#### Delete subject

```
  DELETE /api/subjects/${id}
```
Note that the subject id is **Required**

**Response**
```
Subject with ID ${id} has been deleted.
```





















## Questions
### Get all questions
```
  GET /api/questions
```

**Response**
```json
{
    "questions": [
        {
            "id": 1,
            "numberOfResponses": 6,
            "numberOfCorrectResponses": 4,
            "content": "Nouveau contenu de la question",
            "type": "SINGLE",
            "points": 15,
            "level": {
                "id": 2,
                "description": "testnintermédiaire",
                "maxPoints": 10,
                "minPoints": 5
            },
            "subject": {
                "id": 6,
                "title": "TT",
                "parentId": null
            },
            "validations": [
                {
                    "id": 54,
                    "points": 10,
                    "questionId": 1,
                    "responseId": 1
                },
                {
                    "id": 102,
                    "points": 10,
                    "questionId": 1,
                    "responseId": 55
                }
            ],
            "medias": [
                {
                    "id": 1,
                    "type": null,
                    "url": "test",
                    "questionId": 1
                }
            ]
        },
        {
            "id": 3,
            "numberOfResponses": 6,
            "numberOfCorrectResponses": 4,
            "content": "Nouveau contenu de la question",
            "type": "SINGLE",
            "points": 15,
            "level": {
                "id": 2,
                "description": "testnintermédiaire",
                "maxPoints": 10,
                "minPoints": 5
            },
            "subject": {
                "id": 6,
                "title": "TT",
                "parentId": null
            },
            "validations": [],
            "medias": []
        },
        {
            "id": 2,
            "numberOfResponses": 6,
            "numberOfCorrectResponses": 4,
            "content": " contenu  question",
            "type": "SINGLE",
            "points": 15,
            "level": {
                "id": 2,
                "description": "testnintermédiaire",
                "maxPoints": 10,
                "minPoints": 5
            },
            "subject": {
                "id": 6,
                "title": "TT",
                "parentId": null
            },
            "validations": [],
            "medias": [
                {
                    "id": 2,
                    "type": null,
                    "url": "test",
                    "questionId": 2
                },
                {
                    "id": 3,
                    "type": "VIDEO",
                    "url": "test",
                    "questionId": 2
                },
                {
                    "id": 52,
                    "type": "VIDEO",
                    "url": "test",
                    "questionId": 2
                },
                {
                    "id": 53,
                    "type": "VIDEO",
                    "url": "test",
                    "questionId": 2
                },
                {
                    "id": 54,
                    "type": "VIDEO",
                    "url": "test",
                    "questionId": 2
                }
            ]
        },
        {
            "id": 4,
            "numberOfResponses": 6,
            "numberOfCorrectResponses": 4,
            "content": "Nouveau contenu de la question",
            "type": "SINGLE",
            "points": 16,
            "level": {
                "id": 2,
                "description": "testnintermédiaire",
                "maxPoints": 10,
                "minPoints": 5
            },
            "subject": {
                "id": 6,
                "title": "TT",
                "parentId": null
            },
            "validations": [],
            "medias": []
        },
        {
            "id": 5,
            "numberOfResponses": 6,
            "numberOfCorrectResponses": 4,
            "content": "Nouveau contenu de la question",
            "type": "SINGLE",
            "points": 16,
            "level": {
                "id": 2,
                "description": "testnintermédiaire",
                "maxPoints": 10,
                "minPoints": 5
            },
            "subject": {
                "id": 6,
                "title": "TT",
                "parentId": null
            },
            "validations": [],
            "medias": []
        }
    ],
    "message": "questions found"
}
```


### Create question

```
  POST /api/questions
```

**Payload**
```json
 {
  "numberOfResponses": 6,
  "numberOfCorrectResponses": 4,  
  "content": "Nouveau contenu de la question",  
  "points": 16,
  "levelId": 2,  
  "subjectId": 6 
}
```

**Response**
```json
{
    "subject": {
        "id": 52,
        "numberOfResponses": 6,
        "numberOfCorrectResponses": 4,
        "content": "Nouveau contenu de la question",
        "type": "SINGLE",
        "points": 16,
        "level": {
            "id": 2,
            "description": "testnintermédiaire",
            "maxPoints": 10,
            "minPoints": 5
        },
        "subject": {
            "id": 6,
            "title": "TT",
            "parentId": null
        },
        "validations": null,
        "medias": null
    },
    "message": "question created"
}
```

#### Update question

```
  PUT /api/questions/${id}
```

**Payload**
```json
 {
  "numberOfResponses": 6, 
  "numberOfCorrectResponses": 4,
  "content": " contenu  question",  
  "points": 15,  
  "levelId": 2,  
  "subjectId": 6 
 
}
```

**Response**
```json
{
    "message": "question with ID 4 has been updated successfully"
}
```

#### Delete question

```
  DELETE /api/questions/${id}
```
Note that the question id is **Required**

**Response**
```json
Question with ID ${id} has been deleted.
```

#### get question by subject id

```
  PUT /api/questions/GetQuestionBYSubjectId/6
```



**Response**
```json
{
    "questions": [
        {
            "id": 1,
            "numberOfResponses": 6,
            "numberOfCorrectResponses": 4,
            "content": "Nouveau contenu de la question",
            "type": "SINGLE",
            "points": 15,
            "level": {
                "id": 2,
                "description": "testnintermédiaire",
                "maxPoints": 10,
                "minPoints": 5
            },
            "subject": {
                "id": 6,
                "title": "TT",
                "parentId": null
            },
            "validations": [
                {
                    "id": 54,
                    "points": 10,
                    "questionId": 1,
                    "responseId": 1
                },
                {
                    "id": 102,
                    "points": 10,
                    "questionId": 1,
                    "responseId": 55
                }
            ],
            "medias": [
                {
                    "id": 1,
                    "type": null,
                    "url": "test",
                    "questionId": 1
                }
            ]
        },
        {
            "id": 3,
            "numberOfResponses": 6,
            "numberOfCorrectResponses": 4,
            "content": "Nouveau contenu de la question",
            "type": "SINGLE",
            "points": 15,
            "level": {
                "id": 2,
                "description": "testnintermédiaire",
                "maxPoints": 10,
                "minPoints": 5
            },
            "subject": {
                "id": 6,
                "title": "TT",
                "parentId": null
            },
            "validations": [],
            "medias": []
        },
        {
            "id": 2,
            "numberOfResponses": 6,
            "numberOfCorrectResponses": 4,
            "content": " contenu  question",
            "type": "SINGLE",
            "points": 15,
            "level": {
                "id": 2,
                "description": "testnintermédiaire",
                "maxPoints": 10,
                "minPoints": 5
            },
            "subject": {
                "id": 6,
                "title": "TT",
                "parentId": null
            },
            "validations": [],
            "medias": [
                {
                    "id": 2,
                    "type": null,
                    "url": "test",
                    "questionId": 2
                },
                {
                    "id": 3,
                    "type": "VIDEO",
                    "url": "test",
                    "questionId": 2
                },
                {
                    "id": 52,
                    "type": "VIDEO",
                    "url": "test",
                    "questionId": 2
                },
                {
                    "id": 53,
                    "type": "VIDEO",
                    "url": "test",
                    "questionId": 2
                },
                {
                    "id": 54,
                    "type": "VIDEO",
                    "url": "test",
                    "questionId": 2
                }
            ]
        },
        {
            "id": 4,
            "numberOfResponses": 6,
            "numberOfCorrectResponses": 4,
            "content": "Nouveau contenu de la question",
            "type": "SINGLE",
            "points": 16,
            "level": {
                "id": 2,
                "description": "testnintermédiaire",
                "maxPoints": 10,
                "minPoints": 5
            },
            "subject": {
                "id": 6,
                "title": "TT",
                "parentId": null
            },
            "validations": [],
            "medias": []
        },
        {
            "id": 5,
            "numberOfResponses": 6,
            "numberOfCorrectResponses": 4,
            "content": "Nouveau contenu de la question",
            "type": "SINGLE",
            "points": 16,
            "level": {
                "id": 2,
                "description": "testnintermédiaire",
                "maxPoints": 10,
                "minPoints": 5
            },
            "subject": {
                "id": 6,
                "title": "TT",
                "parentId": null
            },
            "validations": [],
            "medias": []
        },
        {
            "id": 52,
            "numberOfResponses": 6,
            "numberOfCorrectResponses": 4,
            "content": "Nouveau contenu de la question",
            "type": "SINGLE",
            "points": 16,
            "level": {
                "id": 2,
                "description": "testnintermédiaire",
                "maxPoints": 10,
                "minPoints": 5
            },
            "subject": {
                "id": 6,
                "title": "TT",
                "parentId": null
            },
            "validations": [],
            "medias": []
        }
    ],
    "message": "questions found"
}
```






