# hw8

### insert data
```py
db.Students.insertMany(
    [
        {"name":"Ramesh","subject":"maths","marks":87},
        {"name":"Ramesh","subject":"english","marks":59},
        {"name":"Ramesh","subject":"science","marks":77},
        {"name":"Rav","subject":"maths","marks":62},
        {"name":"Rav","subject":"english","marks":83},
        {"name":"Rav","subject":"science","marks":71},
        {"name":"Alison","subject":"maths","marks":84},
        {"name":"Alison","subject":"english","marks":82},
        {"name":"Alison","subject":"science","marks":86},
        {"name":"Steve","subject":"maths","marks":81},
        {"name":"Steve","subject":"english","marks":89},
        {"name":"Steve","subject":"science","marks":77},
        {"name":"Jan","subject":"english","marks":0,"reason":"absent"}
    ]
)
```
### Find the total marks for each student across all subjects.
```py
db.Students.aggregate([{$group:{_id:"$name",total_mark:{$sum:"$marks"}}}])
```

### Find the maximum marks scored in each subject. 
```py
db.Students.aggregate([{$group:{_id:"$subject",max:{$max:"$marks"}}}])
```

### Find the minimum marks scored by each student. 
```py
db.Students.aggregate([{$group:{_id:"$subject",min:{$min:"$marks"}}}])
```

### Find the top two subjects based on average marks.
```py
db.Students.aggregate([{$group:{_id:"$subject",avg:{$avg:"$marks"}}}, {$sort:{"avg":-1}}, {$limit: 2}])
```
