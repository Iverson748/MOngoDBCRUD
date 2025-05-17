# MOngoDBCRUD
# MongoDB Practice
Part 1. MongoDB Exercise in mongo shell
## create database
Connect to a running mongo instance, use a database named `mongo_practice`.
use mongo_practice
## Insert Documents
Insert the following documents into a `movies` collection.
```
title : Fight Club
writer : Chuck Palahniuk
year : 1999
actors : [
Brad Pitt
Edward Norton
]
```
```
db.movies.insert({title:&quot;Fight Club&quot;, writer: &quot;Chuck Palahniuk&quot;, year: &quot;1999&quot;, actors:[&quot;Brad Pitt&quot;,
&quot;Edward Norton&quot;]})
```
```
title : Pulp Fiction
writer : Quentin Tarantino
year : 1994
actors : [
John Travolta
Uma Thurman
]
```
```
db.movies.insert({title:&quot;Pulp Fiction&quot;, writer:&quot;Quentin Tarantino&quot;, year:&quot;2009&quot;, actors:[&quot;John
Travolta&quot;, &quot;Uma Thurman&quot;]})
```
```
title : Inglorious Basterds
writer : Quentin Tarantino
year : 2009
actors : [
Brad Pitt

Diane Kruger
Eli Roth
]
```
```
db.movies.insert({title:&quot;Inglorious Basterds&quot;, writer:&quot;Quentin Tarantino&quot;, year:&quot;2009&quot;,
actors:[&quot;Brad Pitt&quot;, &quot;Diane Kruger&quot;, &quot;Eli Roth&quot;]})
```
```
title : The Hobbit: An Unexpected Journey
writer : J.R.R. Tolkein
year : 2012
franchise : The Hobbit
```
```
db.movies.insert({title:&quot;The Hobbit: An unexpected Journey&quot;, writer:&quot;J.R.R. Tolkein&quot;,
year:&quot;2012&quot;,franchise:&quot;The Hobbit&quot;})
```
```
title : The Hobbit: The Desolation of Smaug
writer : J.R.R. Tolkein
year : 2013
franchise : The Hobbit
```
```
db.movies.insert({title:&quot;The Hobbit: The Desolation of Smaug&quot;, writer:&quot;J.R.R Tolkien&quot;,
year:&quot;2013&quot;, franchise:&quot;The Hobbit&quot;})
```
```
title : The Hobbit: The Battle of the Five Armies
writer : J.R.R. Tolkein
year : 2012
franchise : The Hobbit
synopsis : Bilbo and Company are forced to engage in a war against an array of combatants
and keep the Lonely Mountain from falling into the hands of a rising darkness.
```
```
db.movies.insert({title:&quot;The Hobbit: The Battle of the Five Armies&quot;, writer:&quot;J.R.R Tolkien&quot;,
year:&quot;2002&quot;, franchise:&quot;The Hobbit&quot;, synopsis:&quot;Bilbo and Company are forced to engage in a
war against an array of combatants and keep the Lonely Mountain from falling into the hands of
a rising darkness.&quot;})
```
```
title : Pee Wee Herman&#39;s Big Adventure
```
```
db.movies.insert({title:&quot;Pee Wee Herman&#39;s Big Adventures&quot;})
```
```
title : Avatar
```

db.movies.insert({title:&quot;Avatar&quot;})

# Screenshots:
![image](https://github.com/user-attachments/assets/1c1cd9d8-05bf-44ce-9b6d-634b9ff57555)
![image](https://github.com/user-attachments/assets/9b47b4d6-9db6-4a4b-acc4-a6a016e01701)
![image](https://github.com/user-attachments/assets/7beb9174-272d-4424-9e0f-0aeb769095b5)
![image](https://github.com/user-attachments/assets/cf91e655-ca73-4e4e-9679-0ee8846382b0)
![image](https://github.com/user-attachments/assets/e8595f60-727e-4ee6-8b05-cc958d539d51)
![image](https://github.com/user-attachments/assets/5566a11c-3440-4b4d-ba73-211fb5347b55)
![image](https://github.com/user-attachments/assets/b359ff09-5482-4765-a175-d1417e3a9b24)


## Update Documents

1. add a synopsis to "The Hobbit: An Unexpected Journey" : "A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home - and the gold within it - from the dragon Smaug."

db.movies.updateOne({_id:ObjectId("5c9f98e5e5c2dfe9b3729bfe")}, {$set:{synopsis:"A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home - and the gold within it - from the dragon Smaug."}})


2. add a synopsis to "The Hobbit: The Desolation of Smaug" : "The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."

db.movies.updateOne({_id:ObjectId("5c9fa42ae5c2dfe9b3729c03")}, {$set:{synopsis:"The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."}})

3. add an actor named "Samuel L. Jackson" to the movie "Pulp Fiction"

db.movies.updateOne({_id:ObjectId("5c9f983ce5c2dfe9b3729bfc")}, {$push:{actors:"Samuel L. Jackson"}})

## Screenshots:
![1ex](https://github.com/user-attachments/assets/12b51cfe-64bc-45e8-9a5c-86360390271c)
![image](https://github.com/user-attachments/assets/4b35f421-0251-444f-8291-d90802fb70e0)
![image](https://github.com/user-attachments/assets/29829b73-535c-443a-a45e-e7eca8ef5e43)

## Text Search
1. find all movies that have a synopsis that contains the word "Bilbo"

db.movies.find({synopsis:{$regex:"Bilbo"}})

2. find all movies that have a synopsis that contains the word "Gandalf"

db.movies.find({synopsis:{$regex:"Gandalf"}})

3. find all movies that have a synopsis that contains the word "Bilbo" and not the word "Gandalf"

db.movies.find({$and:[{synopsis:{$regex:"Bilbo"}}, {synopsis:{$not:/Gandalf/}}]})

4. find all movies that have a synopsis that contains the word "dwarves" or "hobbit"

db.movies.find({$or:[{synopsis:{$regex:"dwarves"}}, {synopsis:{$regex:"hobbit"}}]})

5. find all movies that have a synopsis that contains the word "gold" and "dragon"

db.movies.find({$and:[{synopsis:{$regex:"gold"}}, {synopsis:{$regex:"dragon"}}]})

## Screenshots:

![image](https://github.com/user-attachments/assets/a08cb83f-e72a-4597-bb1e-3a8d4a773bc2)
![image](https://github.com/user-attachments/assets/a7a93f55-3aa9-4904-b7ce-f24a681d6d32)
![image](https://github.com/user-attachments/assets/2e6fe5a9-7260-4736-a264-cfb22c48d4a0)
![image](https://github.com/user-attachments/assets/ee86e77c-e6a9-4048-8e6b-1688feab3e63)
![image](https://github.com/user-attachments/assets/b6ce47ee-c3f5-404e-9e9d-c016f8bd9b14)


## Delete Documents

1. delete the movie "Pee Wee Herman's Big Adventure"

db.movies.remove({_id:ObjectId("5c9f992ae5c2dfe9b3729c00")})

2. delete the movie "Avatar"

db.movies.remove({_id:ObjectId("5c9f9936e5c2dfe9b3729c01")})

## Screenshots:
![image](https://github.com/user-attachments/assets/240c5345-f087-4332-b470-511f3d700951)
![image](https://github.com/user-attachments/assets/61d5c000-f4c8-4747-bafe-b249f60f6ae6)








