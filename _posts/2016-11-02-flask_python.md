---
layout: post
title: Flask Intro
excerpt: "How To Use Flask App in Python"
comments: false
---

**How To Use Flask App in Python**
Following are the steps that need to taken before using Flask in Python: 
*Installing Flask Via Command Line* 

    sudo easy_install flask markdown

Once the Flask is installed create a server.py file using an editor of your choice and follow the following start up code:

     import os
     from flask import Flask
     app = Flask(__name__)
    
     @app.route('/')
     def helloWorld():
         return "Hello World"
    
     # start the server
     if __name__ == '__main__':
         app.run(host=os.getenv('IP', '0.0.0.0'), port=int(os.getenv('PORT', 8080)), debug=True)

 To connect the flask inside the HTML5, simply call the mapping of your flask route using HTML5 <\a> tag. Refer to the code below for a simple example:
 

    <a href="/">Home</a>