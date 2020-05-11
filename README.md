# Mongo-DB CheatSheet

This is a short and easy cheatsheet to help you learn in a fast and uncomplicated way MongoDB.

## What it's MongoDB

MongoDB is a general-purpose, document-based, distributed database that has been designed for modern application developers and the cloud era.

### Installing

To begin with, the installation it's very easy, there is an official [link](https://docs.mongodb.com/manual/administration/install-community/) where you can install it depending on your operating system.

```
Download it
```

After, I added mongoDB's bin folder to the path enviorment variable, so that I can be able to run mongo from anywhere in a command window. Since I use windows, here's another [link](https://dangphongvanthanh.wordpress.com/2017/06/12/add-mongos-bin-folder-to-the-path-environment-variable/) that could help you do the same (for windows 10 only).

```
Command Window access
```

In my case, the database used was provided by my teacher who created it in Atlas, which is a cloud database (from Mongo DB) therefore we needed access trough a link from him to use it in the cmd.

### Start

The first thing would be opening the command window and use the link provided, in my case this will do: 

```
mongo "mongodb+srv://cluster0-cdd34.mongodb.net/next" --username YourUserNameGivenByTheCreator
```
and if the creator uses a password it'll be required. 

### Commands

* **Database/Collection/Document**
  * **Show dbs** - It would pop out the list of created databases.
  * **use NameOfTheDatabase** - Access to the desired database.
  * **db.createCollection("name")** - Create a collection inside the already selected database.
  
* **Insert**
  * **db.name.insert({"data1": "value"})** - Insert a *document* inside the already created collection, if the colleciton was not previously created it will automatically do it. 
  * **db.name.insert({"data1": "value", "birthDate": new Date(1999,8,23)** - new Date(), it's from the syntax of JavaScript (Year, month(the count of months starts at 0), day). In this case, this date means: September 23rd, 1999.
* **Remove**
  * **db.name.remove({"data1": "value"})** - Erase the complete *document* if the key passed ("data1": "value") is matched.
* **Find**
  * **db.name.find()** - Shows all the *documents* in that collection.
  * **db.name.find().pretty()** - Shows all the *documents* in that collection in json form.
* **Update**:
  * **db.name.update({"data1": "value"}, {"$set": {"data": "value"}})** - To update a data from the document we fisrt pass trough the brackets any data from the document we want to update so that when it matches the result it change it; the second pair of brackets uses "$set" which is the parameter to update and inside those brackets we use another pair {} with the data we want to change and the updated value of that data.
  * **db.name.update({"data1": "value"}, {"$set": {"data": "value"}}, {"multi": true})** - Here we added the "multi" parameter when it's *flase* it will only update the **first** document that matches, on the hand, *true* will update **all** the document that matches.
  * **db.name.update({"data1": "value"}, {"$inc": {"data": NumberToIncrement})** - This will do the same as update, the difference is the parameter "$inc" that allows increment a value that is a number.
  * **db.name.update({"data1": "value"}, {"$unset": {"data2": ""})** - Erase an specific data from a document. The "$unset" will remove the specific data from the document, if you want to do it for all the documents add: {"multi": true}.
  * **db.name.update({"data1": "value"}, {"$rename": {"data2": "data3"})** - Rename tha data itself from a document with the parameter "$rename".
  * **db.name.update({"data1": "value"}, {"$set": {"data.2": "value"}})** - To update a value that it's inside a list that it's also a vlue from a data we use the position of the value we want to update in the list, in this example it would be the value numbers 3 (since we start counting from 0). 
  * **db.name.update({"data": "newValue"}, {"$set": {"data.$": "valueToChange"}}, {"multi": true})** - In case we don't know the position of the value we want to change, in this case it's necessary that the data to match it wits, is the data and the new value to change and in the next brackets tha data and the sign "$" instead of the position number with the value to change. 
  * **db.name.update({"data1": "value"}, {"$set": {"data.embeddedValue": "value"}}, {"multi": true})** - To update a value that inside a object which is also a data we use the dot with the name of the data to have access to it and change its value.


## Data types 

* **Strings** - "Alexa".
* **Numbers** - 3, 3.14.
* **Booleans** - false, true.
* **Arrays** - ["apple", "coconut", "banana",...].
* **Objects** - {"name": "Alexa", "age": 20}.
* **Null** - null.
* **ObjectId(...)** - ID for each document automatically created by MongoDB.
* **ISODate(...)** - Type for dates.

## Authors

* Alexa Canche 

## Acknowledgments

* This is a version used from "The Magical Marverls of MongoDB"
