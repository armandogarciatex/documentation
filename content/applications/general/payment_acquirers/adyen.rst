
=====
Adyen
=====

`Adyen <https://www.adyen.com/>`_ is a Dutch-based company that offers several online payment
possibilities.

Configuration
=============

To proceed your payments with Adyen, you need an Adyen account in the live environment.

.. note::
   Please refer to :ref:`Add a new Payment Acquirer <payment_acquirers/add_new>` to read how to
   enable this payment acquirer on Odoo.

Credentials tab
---------------

Odoo needs your **API Credentials** to connect with your Adyen account, which comprise:

- `Merchant Account`: The code of the merchant account to use with this acquirer.
- :ref:`API Key <adyen/api_and_client_keys>`: The API key of the webservice user.
- :ref:`Client Key <adyen/api_and_client_keys>`: The client key of the webservice user.
- :ref:`HMAC Key <adyen/hmac_key>`: The HMAC key of the webhook.
- :ref:`Checkout API URL <adyen/urls>`: The base URL for the Checkout API endpoints.
- :ref:`Recurring API URL <adyen/urls>`: The base URL for the Recurring API endpoints.

You can copy your credentials from your Adyen account, and paste them in the related fields under
the **Credentials** tab.

.. image:: media/adyen_credentials.png
   :align: center
   :alt: Adyen required credentials.
   :width: 500

.. important::
   If you are trying Adyen as a test, with a *test account*, change the **State** to *Test Mode*. We
   recommend doing this on a test Odoo database, rather than on your main database.

.. _adyen/api_and_client_keys:

API key and Client key
~~~~~~~~~~~~~~~~~~~~~~

In order to retrieve the API Key and the Client Key, log into your Adyen account, go to
:menuselection:`Developers --> API Credentials --> Username if one, else Create new credential -->
Authentication`, and get or generate your **API Key** and **Client Key**. Be carefull to copy your
API key as you'll not be allowed to get it later without generating a new one.

.. image:: media/adyen_api_and_client_keys.png
   :align: center
   :alt: Generate new API Key and Client Key.
   :width: 500

This is also the place where you'll :ref:`allow payments to be made from your website
<adyen/allowed_origins>`.

.. _adyen/hmac_key:

HMAC key
~~~~~~~~

In order to retrieve the HMAC Key, you'll need to configure a `Standard Notification Webhook`. For
this, log into your Adyen account, then go to :menuselection:`Developers --> Webhooks --> Add
webhook --> Add Standard notification`.

.. image:: media/adyen_add_webhook.png
   :align: center
   :alt: Generate new API Key and Client Key.
   :width: 500

There, in :menuselection:`Transport --> URL`, enter your server address followed by
`/payment/adyen/notification`.

.. image:: media/adyen_webhook_url.png
   :align: center
   :alt: Generate new API Key and Client Key.
   :width: 500

Then continue in :menuselection:`Additional Settings --> HMAC Key --> Generate new HMAC key`. Be
carefull to copy it as you'll not be allowed to get it later without generating a new one.

.. image:: media/adyen_webhook_hmac_key.png
   :align: center
   :alt: Generate new API Key and Client Key.
   :width: 500

.. _adyen/urls:

URLs
~~~~

To retrieve the URLs, log into your Adyen account, go to :menuselection:`Developers --> API URLs`,
and get your:

- **Checkout API URL** from the Checkout API (`https://checkout_url/checkout/`)
- **Recurring API URL** from the Recurring (`https://recurring_url/Recurring/`)

.. image:: media/adyen_api_urls.png
   :align: center
   :alt: Get the links for the different API.
   :width: 500

Adyen Account
-------------

.. _adyen/allowed_origins:

Allow payments from a specific origin
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To allow payment originated from your website, go to :menuselection:`Developers --> API Credentials
--> Username if one, else Create new credential --> Allowed Origins`, and add the URLs from where
payments will be made.

.. image:: media/adyen_allowed_origins.png
   :align: center
   :alt: Allows payments originated from a specific domain.
   :width: 500

This is also the place where you got your :ref:`API key and Client key <adyen/api_and_client_keys>`.

.. seealso::
   - `Get started with Adyen <https://docs.adyen.com/get-started-with-adyen>`_
   - :doc:`../payment_acquirers`
