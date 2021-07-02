## Application overview
Sample application to set up eCommerce store to sell books. The application only provides the front end to display & purchase books but does not have the backend to capture Order details. Credit card payment is handled through integration with Stripe. For a primer on how credit card payment works, please see [this](https://stripe.com/docs/payments/cards/overview). To run the application, you'll need to create a Stripe account and retrieve API keys from the Stripe dashboard (you can create a free test account [here](https://dashboard.stripe.com/register)). Stripe provides test mode and live mode keys.

## Installation instructions
1) Clone the repository => git clone https://github.com/shivanshuu/Stripe.git
2) Install dependencies => npm install
2) Create a .env file in app home directory and put your Stripe SECRET_KEY. Put your Publishable Stripe Key in client.js. In order to test, use test mode keys.
3) Run the application locally => npm start
4) Navigate to [http://localhost:3000](http://localhost:3000) to view the home page and complete purchase of a book. Confirmation id returned by Stripe API is displayed

## Application Stack
The application is written in JavaScript (Node.js) and uses [Stripe](https://stripe.com/) for payments. For Node, [express](https://expressjs.com/) is used as web framework and [handlebars](https://handlebarsjs.com/) is used for HTML templates to generate content. In order to accept credit card payments, the application uses Stripe Elements. Stripe Elements provides rich JavaScript(JS) UI components to integrate Stripe Payments easily into your application. To integrate Stripe Elements, I used following [instructions](https://stripe.com/docs/payments/integration-builder) which has sample JS code and test card numbers. Please be careful in writing JS as small errors could cause page not to work properly. The errors can be viewed using More Tools -> Developer Tools in chrome. There might be some challenges where Stripe Elements UI Card is not getting displayed properly due to stylesheet issues. Please start with the stylesheet I have provided and then make changes for your look & feel. To view server side Node errors, you can print debug messages.

## Extending the Application
In order to extend the application for your needs, you can do the following -
1) Customize the Stylesheet and Handlebar templates as per your look & feel and content.
2) Complete the application to capture orders and build functionality to send fulfillemnt status to customers. 
3) Currently the application only accepts Credit Card Payment. Other forms of payments including Apple & Google Pay are also supported by Stripe Elements and can easily be provided. Sample code [here](https://github.com/stripe/stripe-payments-demo). I have tested the application with Stripe Test Keys but once you are live, it should work with your live mode keys. Also test for various kinds of credit cards for different countries to test the Stripe elements UI which customizes itself.
4) Once you have tested locally, deploy the application in Cloud like [AWS](https://aws.amazon.com/getting-started/) so it is accessible to your customers. 
5) The application is currently not using any database. Instead `app.js` includes a simple switch statement to read the GET params for `item`. You can store the list of books & details in a Database like [DynamoDB](https://aws.amazon.com/getting-started/hands-on/create-nosql-table/) which is easy to manage. Orders can also be stored in DynamoDB. Order status emails can be sent by using [SES](https://aws.amazon.com/ses/getting-started/).
6) For the application stack, you can use a managed runtime which is scalable and secure like AWS [AppRunner](https://docs.aws.amazon.com/apprunner/latest/dg/service-source-code-nodejs.html). AppRunner also automatically tests and deploys applications once you checkin the code in Git.
7) Once application is up & running, you can add more functionality for customers like pre-ordering books and writing & reading reviews. 

