---
layout: post
title: R and mongoDB
---


<div class="message">
  This is a simple example on how to query mongoDB with R using rmongodb package.
</div>


### Code

```{R}
# CREATE CONNECTION WITH mongoDB
mongo <- mongo.create(db="db_trends")
# SHOW DBs
mongo.get.databases(mongo)
# CHOOSE THE COLLECTION
colle <- "db_trends.trends_twitter"
# COUNT DOCUMENTS OF THE COLLECTION
mongo.count(mongo,colle)

# A. SELECT ALL THE DOCUMENTS ON THE COLLECTION
todo <- mongo.find.all(mongo,colle)

# B. CREATE A BUFFER TO FILTER THE QUERY
buf <- mongo.bson.buffer.create()
mongo.bson.buffer.append(buf, "COLUMN_NAME","FILTER")
# CREATE THE QUERY
query <- mongo.bson.from.buffer(buf)
# QUERY
cursor <- mongo.find(mongo, colle)
# STORE THE RESPONSE INTO A DATA FRAME
all <- mongo.cursor.to.data.frame(cursor) 
```

-----

Want to see something else added? <a href="https://github.com/afrdiaz/afrdiaz.github.io/issues/new">Open an issue.</a>
