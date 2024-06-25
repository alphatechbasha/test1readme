AWS Lambda Full Stack

# Why this project

I developed this program for time pass and to play with AWS Lambda so there is nothing to give service to the public

So I am making this project for just knowledge purpose who are newbie to build the project using lambda this instructions may use to them

# What I build

I build a normal static website which is only used to store details of clients where the website shows it is door step banking but it just normal blog type website, where I try to implement the Razer pay option but it may leads to cost and complex of codes so I just used to do this way

# where to start

First I just used the node js to serve the static website in live as normal html, css and javascript

After that now we need to step the server as here I am going to give 4 values which I want store on the database, here I am using aws dynamodb you can use other too like mango db etc

So first I wrote the code in nodejs but it didn't work for me so I go with python here I just copied the same structure of node js into python

You can see the server-side code which I am going to paste on aws lamba handler

<https://github.com/mahaboobtech/awslambdafullstack/src/app.js>

So if we observe the backend or server side code there am using JSON to send the code to dynamodb for sending dynamodb i important some module called boto3 which used to connect and write DynamoDB

And last important point about the server side code is CORS cross origin request this was the main problem faced while developing this project so I just write the as :

## concept

If the http request gets then take the json data in to variables and then send a copy of response to client and then store to the dynamodb but there is a access origin permission allowed to a website and the method of permission allowed .. that is the main code to solve the cors problem on code side but still to solve cors we need to tweak on api gate way you can see the instructions while implementing aws

Ok now code work is completed

## Its time to work out on aws

So the main concept is

While creating aws lambda give access of full control of dynamodb to it by creating a policy on iam aws




1. Copy the server side code to aws lambda and add api gateway to it by following make sure the api gateway has required http methods as you implemented to aws lambda the link is generated copy and hold that api gateway link



1. Now go to api gateway here make sure the cors configuration like this access origin methods and other 2 also configuration as your requirement but am giving access to everyone and every methods By this cors problem will be solved

<https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-cors.html>


1. Now create a dynanamodb on the aws dynamodb where create a key as your requirement here I am giving name that's enough now copy the table name and paste it on aws lambda code where there is some comment


1. Now copy the api gate link and edit on the js code on client side code and now make sure the folder is designed like this and then now upload the code on s3 bucket

Const url = “” #here change your api gateway what has been generated

1. Make sure you your hosting the website on the option and and added this policy to it as soon you click on host option you can see the link on here

Policy :

{

"Version": "2012-10-17",

"Statement": \[

{

"Sid": "PublicReadGetObject",

"Effect": "Allow",

"Principal": "\*",

"Action": "s3:GetObject",

"Resource": "arn:aws:s3:::firsts3html/\*"

}

\]

}


1. That is the client side link of your website
2. Now just click the link and enjoy



Now you have generated the static website using aws lamba

When you give details to the website it will directly store on the website

# For local testing

As there is a code for testing on locally where it use database of mysql , razor pay(optional if your business account) it is nodejs based code its only for testing purpose on local

On /src/app.js

Just type :

Yarn

Next npm start app.js or npm start
