---
layout: page
title: Async Activity
nav_exclude: true
---

# Simple Activity using async/await

Learning Objectives for this activity:

- Practice applying asynchronous programming concepts: promises, async/await
- Experiment with applying different ordering constraints in asynchronous code

## Overview

In this activity, you will experiment with asynchronous programming constructs in TypeScript.

### Getting started

As usual, download the [starter code]({{ site.baseurl }}{% link Activities/module06-async-activity.zip %}) and run `npm install`. Then run `npm run examples` to run the examples as-is. The output should be something like:

```
Creating a student
Import grades completed, and returned:
[
  {
    "student": {
      "studentID": 17,
      "studentName": "test student"
    },
    "grades": [
      {
        "course": "demo course",
        "grade": 100
      }
    ]
  }
]

```

### Stringing together many async calls: bulk importing grades

Your task is to write 3 new `async` functions, `importGrades1`, `importGrades2`, and
`importGrades3`. Each of these functions takes an input of the type `ImportTranscript[]`, creates a student
record for each `ImportTranscript`, and then posts the grades for each of those students. After
posting the grades, it should fetch the transcripts for each student and return an array of
transcripts.

You should implement the functions in the file `examples.ts` - note that there is already a function
stub there for `importGrades1`. As you get started, examine the transcript server examples in
`examples.ts`, and take note of the API calls that are available to you.

Here is the type definition for `ImportTranscript` and its dependencies:

```
type ImportTranscript = {
  studentName: string;
  grades: CourseGrade[];
};
type CourseGrade = { course: Course, grade: number };
type Course = string;
```

Example input:

```
[
    {
        studentName: "Avery",
        grades: [{course: "Software Engineering", grade: 100}, {course: "Chemistry", grade: 70}],
    },
    {
        studentName: "Ripley",
        grades: [{course: "Underwater Basket Weaving", grade: 100}, {course: "Kayaking", grade: 90} ]
    }
]
```

Implement this three ways:

1. Insert a student, insert each of their grades (in order), then insert the next student, then
   their grades, etc. until all students are inserted, then fetch transcripts.
2. Insert a student, then insert each of their grades, then fetch their transcript (in order). Do
   this set of operations asynchronously (concurrently) for all students.
3. Insert a student, then insert each of their grades, asynchronously (concurrently). After all
   students have all of their grades submitted, fetch all of the transcripts asynchronously
   (concurrently).
