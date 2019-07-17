---
title: export
id: export
---
ODE Framework provide an referential’s data export API granted by OAuth2 or HTTP Bascis credential. In some integration case, it can be usefull for data’s setup in third party application.

# Configuration

In backoffice, go to external application management screen (`application registry > external application`) and choose a structure (a school)

## 1. Create a new external application

-   enter your external application’s identifier. It will become the application’s clientID in Oauth2 vocabulary

## 2. Setup advanced options

-   enter a secret code (to grant access to external application)

-   set identification mode to chosse *Basic*

-   configure authorized scopes. You have to tip the *full qualified name* of the endpoint you want to grant. You must separe scope with a space.

> **Note**
>
> the following endpoint are availables
>
> -   org.entcore.directory.controllers.StructureController|listStructures
>
> -   org.entcore.directory.controllers.UserController|listUserInStructuresByUAI
>
# Fetch Data

## List Structures

    curl -i -kH "Authorization: Basic {base64(clientId:secret)}==" https://$domaineENT/directory/structures

``` json
[
    {
        "id":"d31ea442-d070-4a71-8742-c20a33a74a8c",
        "externalId":"55567",
        "name":"Collège Denis Poisson",
        "UAI":"0805432C",
        "address":"15 RUE DE LA VARENNE",
        "zipCode":"45300",
        "city":"TYQPE",
        "phone":"+33 1 64 59 25 20",
        "academy":"VERSAILLES"
    },
    {...},...
]
```

## List users per structure

    curl -i -kH "Authorization: Basic {base64(clientId:secret)}==" https://$domaineENT/directory/user/structures/list?format=xml&uai=0805432C&uai=5551628K

``` json
[
    {
        "externalId":"4eb5864e-1521-4c0c-ac54-1332a7ee101b",
        "lastName":"Martin",
        "firstName":"Marie",
        "login":"marie.martin"
    },
    {...}, ...
]
```
