[eCommerce Application](

## Application overview
This is a e-Commerce application that a customer can use to purchase a book. 
The application is written in Javascript (Node.js) and uses [ Stripe](https://stripe.com/) for payments. It uses handlebars for [templates] (hhttps://handlebarsjs.com/)) to generate the website content. To run the application, you'll need to create a Stripe account and retrieve API keys from the Stripe dashboard (you can create a free test account [here](https://dashboard.stripe.com/register)) 

## Installation instructions
1) Clone the repository => git clone https://github.com/shivanshuu/Stripe.git
2) Install dependencies => npm install
2) Create a .env file and put your Stripe SECRET_KEY. Put your Publishable Stripe Key in client.js. In order to test, use test mode keys.
3) Run the application locally => npm start
4) Navigate to [http://localhost:3000](http://localhost:3000) to view the home page.

## Application Stack
In order to accept credit card payments, the application uses Stripe Elements. For a primer on how credit card payment works, please see [this](https://stripe.com/docs/payments/cards/overview)
Stripe Elements provides rich Javascript UI components to integrate Stripe Payments esaily into your website. To integrate Stripe Elements into the application, we used following [instructions](https://stripe.com/docs/payments/integration-builder). There might be some challenges where Stripe Elements UI Card is not getting displayed properly due to Stylesheet issues. This can be overcome by using Stylesheet we have provided and modifying only for your look and feel. Also test for various kinds of credit cards for different countries as the UI customizes itself. We have tested the application with Stripe Test Keys but once you are live, it should work with your live mode keys.

## Extending the Application
In order to customize the application for your needs, you can do the following -
1) Customize the Stylesheet and Handlebar templates as per your look and feel need
2) Currently the application only accepts Credit Card Payment. Other forms of payments including Apple &Google Pay are also supported by Stripe Elements and can easily be provided.
3) Complete the application to capture orders and build functionality to send fulfillemnt status to customers. 
4) Deploy the application in Cloud like AWS so it is accessible to your customers  [Getting Started with AWS](https://aws.amazon.com/getting-started/), 
5) The application is currently not using any database. Instead `app.js` includes a simple switch statement to read the GET params for `item`. You can store the list of books & details in a Database like DynamoDB which makes it easy to manage. [Getting Started with DynamoDB](https://aws.amazon.com/getting-started/hands-on/create-nosql-table/)
6) For the application stack, you can use a managed runtme which is scalable and secure like AWS AppRunner. [Deploy Node app on AWS Apprunner](https://docs.aws.amazon.com/apprunner/latest/dg/service-source-code-nodejs.html). Apprunner also automatically tests and deploys applications once you checkin the code.
7) Add more functionality for customers like pre-ordering books, writing & reading reviews. 



