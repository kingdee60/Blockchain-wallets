# Cryptowallets
Background
You work at a startup that’s building a new and disruptive application named KryptoJobs2Go (a fictitious application). Your customers can use KryptoJobs2Go to find fintech professionals from a list of candidates, hire them, and then pay them. As the lead developer, you’ve been tasked with integrating the Ethereum blockchain network into the application. The purpose is to enable the customers to instantly pay their hired fintech professionals with cryptocurrency.

What You're Creating
The completed fintech_finder.py file, which contains the code that’s associated with the web interface of your application. (The included code is compatible with the Streamlit library.) You’ll write all your code for this Challenge in this file.

Note that by using import statements, you’ll integrate the crypto_wallet.py Python script into the code in this file.
A README.md file that includes screenshots to confirm that by assuming the role of a KryptoJobs2Go customer, you successfully created an Ethereum transaction, including the gas estimate, that pays a KryptoJobs2Go candidate for their work.

Files
Download the following files to help you get started:

Module 19 Challenge files
Instructions
The instructions for this Challenge are divided into the following high-level steps:

Import Ethereum transaction functions into the KryptoJobs2Go application.

Sign and run a payment transaction.

Inspect the transaction in Ganache.

Step 1: Import Ethereum Transaction Functions into the KryptoJobs2Go Application
In this section, you'll import several functions from the crypto_wallet.py file into the fintech_finder.py file. Note that the latter file contains the code for the customer interface of the KryptoJobs2Go application. And, you’ll import the functions to add wallet operations to this application. In this section, you’ll also assume the role of a KryptoJobs2Go customer (that is, you’ll provide your Ethereum wallet and account information to the application).

To do all this, complete the following steps:

Review the code in the crypto_wallet.py file. Note that the Ethereum transaction functions that you’ve built throughout this module have been incorporated into Python functions that allow you to automate the process of accessing them. The Ethereum transaction functions include wallet, wallet.derive_acount, get_balance, fromWei, estimateGas, sendRawTransaction, and others.

Add your mnemonic seed phrase (which Ganache provided) to the SAMPLE.env file. Then rename the file to .env.

Open the fintech_finder.py file. Near the beginning of the file, after the provided import statements, import the following functions from the crypto_wallet.py file:

generate_account

get_balance

send_transaction

In the Streamlit sidebar section of code, create a variable named account. Set this variable equal to a call to the generate_account function. Note that this function will create the hierarchical deterministic (HD) wallet and the Ethereum account of the KryptoJobs2Go customer (in this case, you).

In the same section of code, define a new st.sidebar.write function that displays the balance of the customer account. In this function, call the get_balance function, and pass it your Ethereum account.address.

Step 2: Sign and Run a Payment Transaction
In this section, you'll write the code to calculate the wage, in ether, of a fintech professional. The code will base this wage on both the professional’s hourly rate and the number of hours that they worked for a customer. Note that candidate_database in fintech_finder.py contains the hourly rates.

You’ll then write the code that uses the calculated wage to send a transaction that pays the professional. This code should allow the KryptoJobs2Go customer to authorize the transaction with their digital signature. To test this application, you’ll use your own Ethereum account information as the customer account information.

To do all this, complete the following steps:

Note that a KryptoJobs2Go customer will first select a fintech professional candidate from the drop-down menu in the application interface. The customer will then enter the amount of time that they’ll hire the professional for. Code the application so that when a customer completes those steps, it calculates the wage, in ether, that the professional will get paid. To do so, complete the following steps:

Write the equation that calculates the candidate’s wage. This equation should get the candidate’s hourly rate from the candidate database (candidate_database[person][3]) and then multiply that by the value of the hours variable. Save output of this calculation in a variable named wage.

Write the wage variable to the Streamlit sidebar by using st.sidebar.write.

Write the code that allows a customer (in this case, you) to send an Ethereum blockchain transaction that pays the hired candidate. To do so, first find the following code: if st.sidebar.button("Send Transaction"). Next, add logic to that if statement to send the appropriate information to the send_transaction function. To do so, complete the following steps:

Call the send_transaction function, and pass it the following three parameters:

Your Ethereum account information. Recall that this account instance got created when the generate_account function was called. And from the account instance, the application will be able to access the account.address information that it needs to populate the from data attribute in the raw transaction.

The candidate_address value. Note that this will get created and identified in the sidebar when a customer selects a candidate. It will populate the to data attribute in the raw transaction.

The wage value. This will get passed to the toWei function to determine the value, in wei, of the payment in the raw transaction.
