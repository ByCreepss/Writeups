*It is my first WriteUp written in English, which is not my first language, so I apologize if I may talk in a strange way sometimes and hope that it will still be understandable 🙂*

# Theoretical Notions (API & Broken Access)

**API → A**pplication **P**rogramming **I**nterface : allows two (or more) applications to connect, communicate and share data with each other.

**Broken Access :** a vulnerability in a system that allows users to access or perform actions beyond their initial authorizations, thus being very dangerous.

# Challenge Content

A webpage containing different APIs endpoints that we can use : http://api-broken-access.challenge01.root-me.org/

# Challenge Resolution

First of all, we land on this page :

![image.png](attachment:6c7fe3db-4484-45de-a79e-36352e10e772:image.png)

We have **4** endpoints : 

- **/api/signup** → to register users
- **/api/login** → allows user to login
- **/api/user** → to retrieve user info
- **/api/note** → to update the user’s note

The first thing we may do is to try to register a new user, then login with that user (using **/api/signup** and **/api/login** endpoints)

After you’ve successfully logged in, you should get this output : 

![image.png](attachment:3974d891-75da-4715-b42e-51830791c932:image.png)

Meaning that we can now retrieve our user’s information with the **/api/user** endpoint !

To do so, we will set any number as the user_id (the content returned by the request will always be our information, no matter which user_id we’ve put). But, **notice how it says (path)** below the field ! ****:

![image.png](attachment:54db38d6-cc83-43da-9063-4fd5bcb35c91:image.png)

We’ve successfully retrieved our data ! And we can see that the ID of my user is 3.

But now, we want to find a *Broken Access Vulnerability*, and given our context, it would probably be retrieving some informations (like a note) on someone important (admin) …

But first, we should analyze what happens when we send a request to the endpoint, to do so, we should intercept it (and intercept the response) via BurpSuite, the most important part here is to intercept the response, so make sure to configure BurpSuite’s Proxy to also intercept responses.

Let’s make a request and intercept it (the number we put in the user_id field is still not so important) : 

![image.png](attachment:07a7c3b1-f35a-4500-92e5-c20190ac1cf9:image.png)

And here’s the response, we get the informations on the user : 

![image.png](attachment:f7f343cd-3638-4a7c-816f-28a83df94a93:image.png)

When we think of it, the number **1** ID would probably be the admin’s ID, let’s try to modify the request to access to his informations by adding a /1 to the path ! :

![image.png](attachment:e041cf8a-9568-43c2-8afd-ed73d679c7c1:image.png)

 

The response gives us the flag 🙂 : 

![image.png](attachment:f307e027-b3c2-4406-9589-85284b33115f:image.png)
