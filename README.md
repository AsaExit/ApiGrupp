# ApiGrupp
Grupp arbete Api

## HTTP Protocol Basics
## Request response model:
## Request message
## Resources identified using a Universal Resource Identifier (URI)
## Request Method
## Headers, Body, query
## Response
## Response code
## Headers och Body


## Vi använder oss av http://api.softhouse.rocks 
## GET - Metoden 

## Request Method
## -i, --include       Include protocol headers in the output (H/F)
## -H, --header LINE   Pass custom header LINE to server (H)

## 
curl -i -H "Content-Type:application/json" http://api.softhouse.rocks/posts/1

## Request response model:
HTTP/1.1 200 OK     
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: application/json; charset=utf-8
Content-Length: 316
ETag: W/"13c-iqD6A3ivz4dRZ1d/uIZLXBts6BU"
Date: Tue, 21 Apr 2020 08:28:50 GMT
Via: 1.1 google

## Statuskoden var framgångsrik, 200. 
## It's a header. It doesn't tell the browser anything except that the application is powered by Express (should you wish to look at that in chrome dev tools). Express is a server side framework. https://www.reddit.com/r/node/comments/3k9ij6/does_anyone_know_what_the_xpoweredby_express_is/
## 
## 
## Content-Length: 316 posts. Is used to indicate the size of the entire body. The content-length is the size of the compressed message body, in "octets". 
## The ETag or entity tag is part of HTTP, the protocol for the World Wide Web. It is one of several mechanisms that HTTP provides for Web cache validation. 
## 
## 


## 
curl -H "Content-Type:application/json" http://api.softhouse.rocks/posts/1 | jq 

% Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   316  100   316    0     0   2538      0 --:--:-- --:--:-- --:--:--  2548
{
  "_id": "5e806d9f42fbde006b6b9ecf",
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto",
  "__v": 0
}


## 
curl -H GET  http://api.softhouse.rocks/users/3

{"address":{"geo":{"lat":-68.6102,"lng":-47.0653},"street":"Douglas Extension","suite":"Suite 847","city":"McKenziehaven","zipcode":"59590-4157"},"_id":"5e806d9f42fbde006b6b9ec7","id":3,"name":"Clementine Bauch","username":"Samantha","email":"Nathan@yesenia.net","__v":0}Sofias-MacBook-Pro:ApiGrupp sofiajunell$ curl -H GET  http://api.softhouse.rocks/users/3


## 
$ curl -H "Content-Type:application/json" http://api.softhouse.rocks/posts/userId1 | jq 
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   171  100   171    0     0   1327      0 --:--:-- --:--:-- --:--:--  1335
{
  "message": "Cast to number failed for value \"NaN\" at path \"id\" for model \"Post\"",
  "name": "CastError",
  "stringValue": "\"NaN\"",
  "kind": "number",
  "value": null,
  "path": "id"
}


## 
### curl -H GET  http://api.softhouse.rocks/users/3 | jq
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   271  100   271    0     0    872      0 --:--:-- --:--:-- --:--:--   871
{
  "address": {
    "geo": {
      "lat": -68.6102,
      "lng": -47.0653
    },
    "street": "Douglas Extension",
    "suite": "Suite 847",
    "city": "McKenziehaven",
    "zipcode": "59590-4157"
  },
  "_id": "5e806d9f42fbde006b6b9ec7",
  "id": 3,
  "name": "Clementine Bauch",
  "username": "Samantha",
  "email": "Nathan@yesenia.net",
  "__v": 0
}

##
$ curl -i -X POST -H "Content-Type:application/json" http://api.softhouse.rocks/posts -d '{"title":"Hi,Karlstadd", "body":"Fresh as morning dew", "userId": "1"}'
HTTP/1.1 201 Created
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: application/json; charset=utf-8
Content-Length: 115
ETag: W/"73-sc6cjswQKZbxNrK9Hty0Yb8Od8Q"
Date: Wed, 22 Apr 2020 15:54:30 GMT
Via: 1.1 google

{"_id":"5ea068b63636b200261814cd","body":"Fresh as morning dew","title":"Hi,Karlstadd","userId":1,"id":847,"__v":0}


## curl -X GET "https://api.softhouse.rocks/posts?userId=1" -H "accept: application/json"




## curl -X GET "https://api.softhouse.rocks/posts?userId=1" -H "accept: application/json" | JQ
{
    "_id": "5ea068b63636b200261814cd",
    "body": "Fresh as morning dew",
    "title": "Hi,Karlstadd",
    "userId": 1,
    "id": 847,
    "__v": 0
  }




## PUT 
curl -X PUT "https://api.softhouse.rocks/posts/847" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"title\":\"Hi,malmo\",\"body\":\"Fresh as morning dew\",\"userId\":1}"

 {
    "_id": "5ea068b63636b200261814cd",
    "body": "Fresh as morning dew",
    "title": "Hi,malmo",
    "userId": 1,
    "id": 847,
    "__v": 0
  }

## PATCH
### curl -X PATCH "https://api.softhouse.rocks/posts/846" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"title\":\"Rostbiff och isterband \",\"body\":\"Griljerar och briljerar\",\"userId\":1}"
 {
    "_id": "5ea03f2b3075e40021162a5e",
    "body": "Griljerar och briljerar",
    "title": "Rostbiff och isterband ",
    "userId": 1,
    "id": 846,
    "__v": 0
  }


## DELETE
curl -X DELETE "https://api.softhouse.rocks/posts/847" -H "accept: application/json"
## id 847 is missing! wohoo

## POST 

$ curl -i -X POST -H "Content-Type:application/json" http://api.softhouse.rocks/posts -d '{"title":"Hi, World", "body":"Fresh as morning dew", "userId": "1"}'
HTTP/1.1 201 Created
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: application/json; charset=utf-8
Content-Length: 112
ETag: W/"70-02iSTKio5MeFXsyJ8v235hz/hlE"
Date: Wed, 22 Apr 2020 12:57:15 GMT
Via: 1.1 google

{"_id":"5ea03f2b3075e40021162a5e","body":"Fresh as morning dew","title":"Hi, World","userId":1,"id":846,"__v":0}








