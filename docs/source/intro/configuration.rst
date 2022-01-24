.. raw:: html

    <style> .red {color:red} </style>

Plugin Configuration
=============

After you download the zip file of `Fire Notifications <https://techcater.com>`_, you can upload directly to the WordPress dashboard.

Prepare CLoud Messaging Credentials
----------------------------------

You can get it by logging into https://console.firebase.google.com: **Project Settings > Cloud Messaging**

.. figure:: /images/cloud-messaging-keys.png
    :scale: 70%
    :align: center

    Cloud Messaging

Then you enter the information in WordPress Dashboard: **Fire Notifications > General**

.. figure:: /images/wordpress-messaging-keys.png
    :scale: 70%
    :align: center

    General information

Prepare Firebase Credentials
----------------------------------

Before using the plugin, we need have the credentials from Firebase Console. You can get it by logging into https://console.firebase.google.com. 

.. figure:: /images/firebase-credentials.png
    :scale: 70%
    :align: center

    Firebase Credentials

Then you enter the information in WordPress Dashboard: **Fire Notifications > Firebase**

.. figure:: /images/wordpress-firebase-config.png
    :scale: 70%
    :align: center

    Firebase Credentials

Update Firestore Security Rules
----------------------------------

The notifications mechanism relies on Firestore, in order to keep track of your web clients subscription. Please add this rule to your Firestore.

.. code-block:: bash

    match /wpTokens/{token} {
        allow write: if true;
    }

After you finish all the configuration, the next step is to install cloud functions, so you web clients can receive notifications.