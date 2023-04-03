# MongoDB_Telephone_Directory_CRUD_operations


#Importing necessary packages..

    import pymongo
    from pprint import pprint

    client = pymongo.MongoClient("mongodb://localhost:27017/")
    mydb = client["Telephone_Directory"]
    mycol = mydb['User_Datas']

#1.INSERT documents into MongoDB:

# Inserting one record into the collection:

    mycol.insert_one({"Name": 'ABC', "Phone No": 123456789, "Place": 'Chennai'})
    for i in mycol.find():
        print(i)

# Inserting Multiple records into the collection:

    mycol.insert_many([{"Name": 'DEF', "Phone No": 456789123, "Place": 'Delhi'},
                       {"Name": 'ADC', "Phone No": 789123456, "Place": 'Mumbai'},
                       {"Name": 'XYZ', "Phone No": 123789456, "Place": 'Bangalore'},
                       {"Name": 'ABC', "Phone No": 789654321, "Place": 'Delhi'},
                       {"Name": 'POQ', "Phone No": 159357456, "Place": 'Kolkata'},
                       {"Name": 'ABC', "Phone No": 951753654, "Place": 'Chennai'},
                       {"Name": 'RUV', "Phone No": 258852369, "Place": 'Mumbai'}])
    for i in mycol.find():
        print(i)


#2.READ documents from MongoDB:

# Reading all the documents from collection:

    for i in mycol.find():
        print(i)

# Reading specific documents from collection:

    for i in mycol.find({'Name': 'DEF'}):
        print(i)


#3.UPDATE documents in MongoDB:

# Updating one document in the collection:

    query = {"Place": 'Chennai'}
    update = {"$set": {'Phone No': 11111111}}
    mycol.update_one(query, update)
    for i in mycol.find():
        print(i)

# Updating multiple documents in the collection:

    query= {'Name': 'ABC'}
    update= {"$set": {'Phone No': 222222222}}
    mycol.update_many(query, update)
    for i in mycol.find():
        print(i)


#4.DELETE documents in MongoDB:

# Delete one document in a collection:

    mycol.delete_one({"Name": "ABC"})
    for i in mycol.find():
        print(i)

# Delete multiple documents in a collection:

    mycol.delete_many({"Name": "ABC"})
    for i in mycol.find():
        print(i)
