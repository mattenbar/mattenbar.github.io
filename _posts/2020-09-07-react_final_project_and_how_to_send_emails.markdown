---
layout: post
title:      "React Final Project & how to send emails"
date:       2020-09-07 16:47:06 -0400
permalink:  react_final_project_and_how_to_send_emails
---


After 6 intense months of learning and studying I have finally reached the end of the software engineering course at Flatiron School. It has been an amazing journey where i have learned so much as well connect with some truly amazing people.

For my final project (much like my other projects) I decided to create something that I have a connection to or I could see myself using. As a freelance photographer for the past 10 years I was constantly writing invoices and trying to keep track of who paid me, who didnt, how much did I earn and of course how much I was owed. From there my app Invoice Tracker was born.

Invoice Tracker is a web app that utilizes a Rails Api back-end with a React.js front-end. The app allows for creating of invoices as well as customers. On the home page you can see how many invoices you have, how much you have earned and how much you have not been paid yet.

One additonal feature i would like to talk about is the ability to e-mail an invoice to a client. For each invoice there is a button to email the invoice to the client/ customer. I was able to do this using [](https://www.emailjs.com)

To implement emailing first sign up for emailjs and create your email template. When your template is complete be sure to use npm to add the node package 
```
$ npm install emailjs-com --save
```

Once the package is installed in your index.html add the following script to your header
```
<script type="text/javascript"
        src="https://cdn.jsdelivr.net/npm/emailjs-com@2/dist/email.min.js">
</script>
<script type="text/javascript">
   (function(){
      emailjs.init("YOUR_USER_ID");
   })();
</script>
```

After that you will now have access to the function emailjs.send(). Here is an example of how I used it in my project (replace YOUR_SERVICE_ID and YOUR_TEMPLATE_ID with your information)
```
<Button variant="dark" onClick={() => window.emailjs.send(
                  'YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', templateParams)
                  .then(res => {alert("Email successfully sent")})
                  .catch(err => {alert("There was an error sending your email")})
                  }>Email Invoice</Button>
```

Setting up and executing email was made simple with emailjs and no need for anything to be added to the backend.

To view my entire project here is the link to the front-end [](https://github.com/mattenbar/invoices-frontend)

Link to back-end [](https://github.com/mattenbar/invoices-backend)
