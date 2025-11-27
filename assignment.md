# Assignment

## Brief

Write the Python codes for the following questions.

## Instructions

Paste the answer as Python in the answer code section below each question.

### Question 1

Question: From the `movies` collection, return the documents with the `plot` that starts with `"war"` in acending order of released date, print only title, plot and released fields. Limit the result to 5.

Answer:

```python
db.movies.find(
    {"plot": {"$regex": "^war", "$options": "i"}},
    {"title": 1, "plot": 1, "released": 1, "_id": 0}
).sort("released", 1).limit(5)
```

### Question 2

Question: Group by `rated` and count the number of movies in each.

Answer:

```python
db.movies.aggregate([
    {
        "$group": {
            "_id": "$rated",
            "count": {"$sum": 1}
        }
    },
    {
        "$sort": {"count": -1}
    }
])
```

### Question 3

Question: Count the number of movies with 3 comments or more.

Answer:

```python
db.movies.count_documents(
    {"comments": {"$exists": True, "$gte": 3}}
)
```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
