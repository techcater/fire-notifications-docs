.. raw:: html

    <style> .red {color:red} </style>

Firebase Cloud Functions Deployment
=============

.. role:: red

:red:`This is step is important, without this. Your web clients will not able to receive notifications.`

Prerequisite
`````````````

In order to deploy cloud functions, you need to have `Nodejs v14 <https://nodejs.org/dist/latest-v14.x/>`_ installed on your machine. 

On Google Cloud Platform, go to your project and make sure Cloud Buid API and Cloud Functions are enabled. And the account that you use to deploy has `Service Account User` Role in order to deploy cloud functions to Firebase.

Then install `firebase-tools <https://firebase.google.com/docs/cli>`_ packaged

.. code-block:: bash

    npm install -g firebase-tools

SignIn and test firebase cli

.. code-block:: bash

    firebase login

Change Your Plan to Blaze
`````````````

**Why will I need a billing account to use the Node.js 10 runtime for Cloud Functions for Firebase?**

Because of updates to its underlying architecture planned for August 17, 2020, Cloud Functions for Firebase will rely on some additional paid Google services: Cloud Build, Container Registry, and Cloud Storage. These architecture updates will apply for functions deployed to the Node.js 10 runtime. `Usage of these services will be billed in addition to existing pricing <https://firebase.google.com/support/faq#pricing-blaze-free>`_.

.. figure:: /images/pay-as-you-go.png
    :scale: 70%
    :align: center

    Firebase pricing plans

Install Packages & Deploy Cloud Functions
`````````````

Install packages and build functions. I'm using Yarn, you can use npm if you want.

.. code-block:: bash

    cd functions/
    yarn OR npm install

The code will go to *functions* folder, then installs packages with yarn / npm.

Start deploying firebase functions

.. code-block:: bash

    cd functions
    yarn deploy --project project-id
    // OR 
    firebase deploy --project project-id

The deployment result should look like this

.. code-block:: bash 

    ✔  functions: Finished running predeploy script.
    i  functions: ensuring necessary APIs are enabled...
    ✔  functions: all necessary APIs are enabled
    i  functions: preparing functions directory for uploading...
    i  functions: packaged functions (103.29 KB) for uploading
    ✔  functions: functions folder uploaded successfully
    i  functions: updating Node.js 14 function wpTokens-onCreate(us-central1)...
    ✔  functions[wpTokens-onCreate(us-central1)] Successful update operation.

    ✔  Deploy complete!

    Project Console: https://console.firebase.google.com/project/project-id/overview
    ✨  Done in 77.56s.

Just to verify that everything works, you can find a cloud functions **wpTokens-onCreate** in your firebase console after the deployment. 