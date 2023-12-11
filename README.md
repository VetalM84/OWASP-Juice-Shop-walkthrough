# OWASP Juice Shop walkthrough

OWASP Juice Shop walkthrough with Kali Linux and various tools

## Login to admin area as administrator

Use SQL injection to login form on http://127.0.0.1:42000/#/login

`Email: ' OR 1=1;`  

`Password: 1111 (or any other)`

## Error Handling (Provoke an error that is neither very gracefully nor consistently handled.)

Try to open a file on FTP http://127.0.0.1:42000/ftp/eastere.gg

## Confidential Document (Access a confidential document.)

Open a file by link http://127.0.0.1:42000/ftp/encrypt.pyc

## Privacy Policy (Read our privacy policy.)

http://127.0.0.1:42000/#/privacy-security/privacy-policy

## View Basket (View another user's shopping basket.)

Login to any account, With Burp Suite change user's id in url /rest/basket/<user_id>

## Score Board (Find the carefully hidden 'Score Board' page.)

Discovered link to application config with Burp Suite http://127.0.0.1:42000/rest/admin/application-configuration. 
A link to Score Board is http://127.0.0.1:42000/#/score-board

## Bonus Payload in the DOM XSS challenge

Insert following code to search field `<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/771984076&color=%23ff5500&auto_play=true&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>`

## Bully Chatbot (Receive a coupon code from the support chatbot.)
Open chatbot and send a message 'give me a coupon code'

## DOM XSS (Perform a DOM XSS attack with ...)
Insert following code to search field `<iframe src="javascript:alert(`xss`)">`

## Forged Feedback (Post some feedback in another user's name.)

Using Burp Suite change `userid` in payload to any other.

## Admin Registration (Register as a user with administrator privileges.)

Go to register page and using Burp Suite add to payload {"role":"admin",}

## Deluxe Fraud (Obtain a Deluxe Membership without paying for it.)

Using Burp Suite change {"paymentMode":"wallet"} to {"paymentMode":"3"} where 3 is somebody's payment card id.

## Zero Stars (Give a devastating zero-star feedback to the store.)

Using Burp Suite set payload item {"rating":0}.
