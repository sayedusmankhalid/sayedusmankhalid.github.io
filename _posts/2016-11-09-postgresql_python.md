---
layout: post
title: Connecting Postgresql
excerpt: "Connect to Postgresql using Python"
comments: false
---
**Connect to Postgresql using Python**
First thing is to install psycopg2 module by typing the following command: 

    sudo apt-get install python-psycopg2

Next open a python file and and use the following code:

    import psycopg2
    import psycopg2.extras
    import os
    
  

      def db_connect():
            print 'connection to the db_connect'
            connectionString='dbname=ecom user=usman password=somePassword host=localhost'
            try:
                print 'are we trying'
                return psycopg2.connect(connectionString)
            except:
                print 'cannot connect to the database'



You can easily connect to the Postgresql in python by importing the psycopg2 module, and writing a db_connect() function. As you can see, first, we made the connectionString and provided the dbname = databaseName, user= username, password = password, host= url. 

Second, we try to make the connection using psycopg2.connect(connectionString) by passing the connectingString that we made in the first step. If it connects it will return us the connection to the database, otherwise if will go in the except statement and notify the user that it could not connect to the database. 

Once we are connected to the database, we can easily fetch the information using the following code: 

     conn=db_connect()
        cur =conn.cursor(cursor_factory=psycopg2.extras.DictCursor)
        cur.execute("select * from users where username=%s and password=crypt(%s, password);",(usman,xyz))
        loginQueryFetch=cur.fetchone()

As you can see we connected to the database by calling our db_connect() function and storing it into the conn variable. Next we made a cursor that would allow us to execute queries using the cur.execute command. We executed query by calling the cur.execute(query) command and passing the query that need to be executed as an argument. Lastly, we fetched any results using cur.fetchone() and stored it into the loginQueryFetch variable.