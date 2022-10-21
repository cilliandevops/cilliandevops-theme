---
slides: example
url_pdf: ""
summary: An example of using the in-built project page.
url_video: ""
date: 2016-04-27T00:00:00Z
external_link: ""
url_slides: ""
title: python post request
tags:
  - Deep Learning
links:
  - icon: twitter
    icon_pack: fab
    name: Follow
    url: https://twitter.com/georgecushen
image:
  caption: Photo by rawpixel on Unsplash
  focal_point: Smart
url_code: ""
---
Author's note: In the process of writing some scripts in python, it is inevitable to call the web interface to test or download some information, so how to send a post request, let's study it today.

1, post and get

The post and get are the two most commonly used methods in the HTTP hypertext transfer protocol. If there is no difference in essence, the purpose is to request information, both are the same transport layer protocol, only the format of the transmission message is inconsistent. The biggest inconsistency in the format is that the parameters of the get method are all placed in the url, and everyone can see it, but the parameters of the post are placed in the request body, which is relatively hidden and said to be relatively safe. In fact, from the perspective of transmission, it is because Clear text transmission on the http network is insecure, so if you want to be safe, you can only encrypt it, which is https. There is also a limit on the length of the data. The url is a maximum of 2048 characters. There is no limit to the post method, which can be characters or binary data. Of course, the http protocol itself does not have length restrictions on url and body, which are generally limited by servers and browsers, because processing long characters will consume more resources, and length restrictions will be imposed for performance and security. (General convention, the parameters are written in ? or & split, you can also agree on the writing method, and the server can respond)

2. requests module

The request module is a built-in module in python. It is mainly used to send http requests. The requests module is more concise than urllib. It imports the module package and returns a response object after each requests request. The object contains specific response information. These information tools Different business returns different information

import request

Send get request r = requests.get('https://www.runoob.com/') Send post request r = requests.post('https://www.runoob.com/try/ajax/demo_post.php' )

3. Content-Type

When sending a post request, you need to pay attention to the header information of the http request, especially the data type of the content of the request, which literally means content-type. What are the common types:

(1) application/x-www-form-urlencoded

This is a common key-value pair type, which is page form data.

(2) application/json

The requested data type is json format data

(3) multipart/form-data

Generally used for uploading files

(4) application/xml

The request data format is xml

4. python post request

In an http request, it needs to include the request line, request header, and message body

Requests uses form to send data by default

import requests #Introduce requests

url = 'url' #Request address

data = {

'id': '123'

'name': 'cillian'

} #Request content data

r = request.post(url, data = data)

print(r.json()) View the response result, the input parameter is json

If it is in json format, add headers

headers = {'content-type': 'application/json'}

Or use the json parameter directly

r = requests.post(url, json=data)

add cookies

cookie = {'cillian' : '123'}

r = requests.post(url,data,cookies=cookie)

Well, here we have a basic understanding of the python interface request post method, let's practice, I wish you a smooth learning!