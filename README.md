# immutable-passport-writeup
 A guide that teaches users how to integrate Immutable Passport into their application. 

 Integrating Immutable Passport into your application involves several steps, including creating a simple application, registering it on the Immutable Developer Hub, installing and initializing the Passport client, logging in a user, displaying user information, and initiating a transaction. Here's a step-by-step guide to help you through the process:

Prerequisites
Before you begin, make sure you have the following prerequisites:

1. A code editor installed (e.g., Visual Studio Code, Sublime Text, or any of your choice).
2. Node.js and npm (Node Package Manager) installed on your system.
3. Basic knowledge of JavaScript and web development.
   
**Step 1: Create a Simple Application or Clone a Repository**

You can start by creating a simple web application or use an existing one. If you want to create a new application from scratch, follow these steps:

1. Create a new directory for your project:

   `mkdir my-immutable-passport-app`

   `cd my-immutable-passport-app`

2. Initialize a new Node.js project:

   `npm init -y`

3. Create an HTML file (e.g., index.html) and a JavaScript file (e.g., app.js) in your project directory.
   
4. Open the HTML file and set up a basic structure. You can include a button for login and placeholders for displaying user information and transaction details.

5. Open the JavaScript file (app.js) and proceed with the following steps.

**Step 2: Register Your Application on Immutable Developer Hub**

To use Immutable Passport, you need to register your application on the Immutable Developer Hub. Follow the steps provided by Immutable to create your application and obtain the necessary credentials (client ID and client secret).
   
**Step 3: Installing and Initializing Passport Client**

1. Install the Immutable Passport client library using npm:

   `npm install @immutable/passport`

2. In your app.js file, import and initialize the Passport client using the credentials obtained from the Immutable Developer Hub:

   ```const ImmutablePassport = require('@immutable/passport');
      const client = new ImmutablePassport({
      clientId: 'YOUR_CLIENT_ID',
      clientSecret: 'YOUR_CLIENT_SECRET',
      });

**Step 4: Logging in a User with Passport**

1. Add an event listener to the login button in your HTML file:

    `<button id="login-button">Log In</button>`

2. In app.js, add code to handle the login button click event:

   ```document.getElementById('login-button').addEventListener('click', async () => {
       try {
       const { idToken, accessToken, nickname } = await client.login();
       // Display the obtained user information on your application.
       console.log('ID Token:', idToken);
       console.log('Access Token:', accessToken);
       console.log('Nickname:', nickname);
       } catch (error) {
      console.error('Login error:', error);
      }
     });


**Step 5: Logging Out a User**

1. Add a logout button in your HTML:

   `<button id="logout-button">Log Out</button>`

2. Handle the logout button click event in app.js:

   ```document.getElementById('logout-button').addEventListener('click', () => {
       client.logout();
       // Optionally, clear user information from your application interface.
      });


**Step 6: Initiating a Transaction from Passport**

To initiate a transaction using Passport, you need to interact with the Immutable blockchain. This typically involves sending assets or invoking a smart contract function. Implement this functionality according to your specific use case, using the access token obtained during the login step to authorize the transaction.

For example, if you want to send a placeholder string and obtain the transaction hash:

    // Define your transaction data
    const transactionData = {
      to: 'RECIPIENT_ADDRESS',
      value: '0.001 ETH', // Specify the amount and currency you want to send.
      data: '0x' + Buffer.from('Hello, Immutable!', 'utf-8').toString('hex'), // Convert your string data to hexadecimal.
    };
 
    // Initiate the transaction
    try {
      const transactionHash = await client.sendTransaction(transactionData);
      console.log('Transaction Hash:', transactionHash);
    } catch (error) {
      console.error('Transaction error:', error);
    }


Replace **'RECIPIENT_ADDRESS'** with the recipient's Ethereum address.

That's it! You've successfully integrated Immutable Passport into your application, allowing users to log in, log out, and initiate transactions on the Immutable blockchain.
