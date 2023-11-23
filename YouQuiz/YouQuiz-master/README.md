
# YouQuiz

YouQuiz facilitates quiz success for students by offering a learning platform supported by their instructors. The platform aims to assist students in easily passing quizzes under the guidance of their trainers.
# Diagramme de classe 

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
