---
layout: post
title: "Creating a Object Storage System from scratch"
---

I was very much interested in developing distributed systems and the like. But it was very difficult to find related beginner articles. One of my projects was a cloud drive. In order to implement that, i had to go many places i haven't. It had a good steep learning curve. I wanted to share that knowledge.

Note that this article is about simple but working design for an object storage. So this article will be very useful for beginners. If you have ideas, please feel free to drop them.

---

## What are we Dealing with?

If you look closer, you might find one thing. It is just like a typical file system. When start to think about, it might seem difficult when it is not.

There will be directories and files. So an example directory will look like ***A/B/C/fileD.txt***

The proposed system is a tree type of storage for metadata and blob storage for file data.

The system supports uploading and downloading.

---

## What did I use for Storage ?

One thing that was clear. I can't rely on mysql. One of the main reasons was when the system is distributed, we will run into problems that NoSQL databases were designed to solve.

I used MongoDb. One of the main reasons is its support for GridFS, which can efficiently store the file data. And other reason was its ease of integration with the application. You just need to use put. Note there are various good alternatives to MongoDB which you can use for the same purpose.

---

## Architecture

Architecture i developed can be defined in two steps.

**i)** **MetaData Collections** - Each document in this collection is meta data document for a directory/file with the fields ***(id, name, contents)/(id, name, GridFSId)*** respectively. id and name are self-explanatory. while contents is an array containing list of ids of the directories and files inside this directory. If the document is a metadata for a file, it will have a field named ***GridFSId*** which is an id to query the GridFS storage in mongodb.

Note that using an array for storing its directory contents is inefficient, it is preferred in this case due to the fact that we are gonna use contents only for mainting its contents not for searching the directory. If you have improvements over this issue, please drop them in the comments.

**ii)** **FileData Collections** - This is exclusively for storing the file binary data. It works by splitting the data and storing them. If you want to know more, refer[ mongodb official docs.](https://docs.mongodb.com/manual/core/gridfs/)

---

## Upload Flow

When you are given an path(by which files will be referred from now) and file data( binary data), the system works like this.

1. Get the directory and filename components from the path. ***[A, B, C, fileD.txt]***
2. initialize `currentDirectory = node("/")`
3. For every component in ***[A, B, C, fileD.txt] ,*** do 4 and 5
4. In currentDirecory, to find out whether the next component(directory and filename) exists. If it exists, initialize `currentDirectory = node (component).` if it didn't exist, create one and add it to ***contents*** of currentDirectory and then initialize `currentDirectory = node (component)`.
5. At the end, you will have `currentDirectory = node("fileD.txt")`. Though it is not a directory, we are using it to store its ***GridFSId.*** Create a file in GridFS and store its id in the `currentDirectory` meta data document with key ***GridFSId***.

We have successfully stored the file in our system.

## Download a File

It is the same way as upload, but no modification of the metadata and storage is needed. Try to figure out yourself. It will be easier.

Congratulations! You made it to the end. I hope you found this article useful. I know there are lot of improvements to be done in this article and the architecture i have used. Please drop them in the comments so that all of us can learn from it.

*Originally published on [HackerNoon](https://hackernoon.com/creating-a-object-storage-system-from-scratch-9q4lz2e8s).*
