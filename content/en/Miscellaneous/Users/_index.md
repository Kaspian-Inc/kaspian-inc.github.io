---
title: "User Management"
date: 2021-02-13
weight: 2
description: >
  An overview of the user management console.
---

## Account permission levels
There are 3 levels of user permissions:
1. __Root:__ The Root user is able to perform all actions in the account, including managing billing, managing other users.
2. __Admin:__ Admin users are able to perform most Root actions. The exceptions are that it is only allowed to view the invoices for billing and view account details for other users instead of having full management control.
3. __Developer:__ Developer users are able to perform all pipeline management actions but are unable to view billing or details about other users.

## Managing your account
Account management settings are available under the `Account` option in the top-right settings icon. Once your account has been made, you can change your name, change your password, and toggle two-factor authentication settings.

{{< figure src="my_account.png" width="850px">}}

### Two-Factor authentication
To enable two-factor authentication, click the toggle when editing your account preferences. This will display a QR code that can be scanned using most time-based one-time password (TOTP) apps like Google Authenticator or Duo Mobile. Once scanned, you will be requested to enter the resulting 6-digit code from the app to verify that the two-factor authentication has been set up correctly. If two-factor authentication is already enabled, you can disable it by simply toggling again.

## Managing account users
New users in your org can be added from this page for Root and Admin accounts. Root accounts can add Admin and Developer users, but Admin accounts can only add Developer users. By clicking the Add button, the following form appears.

{{< figure src="new_user.png" width="850px">}}

Simply specify the requested info about the user, and they will be sent an email with their login credentials. They will be asked to change their password upon logging in. 

The Root account is also able to reset the password for any given account. Simply click on the user who's account password must be reset and they will receive an email with instructions to do so.
