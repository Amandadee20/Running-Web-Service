# Running-Web-Service

To fullfil 1st Automating Real-World Task with Python on Bangkit : Google IT Automation with Python Course

*Case : Using python dictionaries and upload it to running web service

Here the code i use when working on qwiklabs virtual machine  
- First we input python3 as the programming languages that we want to use  
#! /usr/bin/env python3  
- We also import some module to make our code running successfully, *requests* to send message to another computer on another network using HTTP, and *json* to convert list of the dict into JSON format  
import os  
import requests  
import json  
- We define the file txt path that filled by customer feedback into list to make it easy when we iterate it  
feedback_file = os.listdir('/data/feedback')  
- Then we iterate each txt file, read each file, and split it by new line  
for file in feedback_file:  
  with open('/data/feedback/' + file) as each_feedback:  
    value = each_feedback.read().split('\n')  
- In here we make a dictionary for the feedback that contain title, name, date, and feedback for as the keys for the content value  
    feedback_dict = {"title":value[0], "name":value[1]. "date":value[2], "feedback":value[3]}  
- We post it into the url and pass the feedback_dict for the parameter and print it  
    response = requests.post("http://<corpweb-ext-IP>/feedback/", json=feedback_dict)  
print(response.request.body)  
- We can make sure an error message if the response is fail  
if not response.ok:  
  raise Exception("GET failed with status code {}".format(response.status_code))  
