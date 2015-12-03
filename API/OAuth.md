## Using OAuth 2.0 to access Calendar42 Apis (WIP)

Calendar42 APIs use the OAuth 2.0 protocol for authentication and authorization. Calendar42 supports common OAuth 2.0 scenarios such as those for web server, installed, and client-side applications.

To begin, obtain OAuth 2.0 client credentials from the Calendar42 Developers Console. Then your client application requests an access token from the Calendar42 Authorization Server, extracts a token from the response, and sends the token to the Calendar42 API that you want to access. For an interactive demonstration of using OAuth 2.0 with Calendar42 (including the option to use your own client credentials), experiment with the OAuth 2.0 Playground.

This page gives an overview of the OAuth 2.0 authorization scenarios that Calendar42 supports, and provides links to more detailed content. For details about using OAuth 2.0 for authentication, see OpenID Connect.

### WIP!

"WIP" stands for "*Work in progress*".
Because at Calendar42 we are working to improve and increase all functionalities we provide in our systems it is important to keep an eye on our [Changenotes](http://docs.calendar42.com/en/latest/rest-api/change-notes/) and have in mind the following list of endpoints can be accessed through oAuth authorization.

#### 3 December 2015

Only the following endpoints and operations can be performed with the token provided through oAuth.

* calendars
  * GET
  * POST
* events
  * GET
  * POST

> If you notice this documentation is not up to date, please let us know and we will help as soon as possible.

### Basic steps

All applications follow a basic pattern when accessing a Calenda42 API using OAuth 2.0. At a high level, you follow four steps:

1. Obtain OAuth 2.0 credentials from the Calenda42.

  Contact Calendar42 to obtain OAuth 2.0 credentials such as a client ID and client secret that are known to both Calenda42 and your application. The set of values varies based on what type of application you are building. For example, a JavaScript application does not require a secret, but a web server application does.

2. Obtain an access token from the Calenda42 Authorization Server:

3. Send the access token to an API:

  After an application obtains an access token, it sends the token to a Calenda42 API in an HTTP authorization header. It is possible to send tokens as URI query-string parameters, but we don't recommend it, because URI parameters can end up in log files that are not completely secure. Also, it is good REST practice to avoid creating unnecessary URI parameter names.
  Access tokens are valid only for the set of operations and resources described in the scope of the token request. For example, if an access token is issued for the Calenda42+ API, it does not grant access to the Calenda42 Contacts API. You can, however, send that access token to the Calenda42+ API multiple times for similar operations.

4. Refresh the access token, if necessary.

  Access tokens have limited lifetimes. If your application needs access to a Calenda42 API beyond the lifetime of a single access token, it can obtain a refresh token. A refresh token allows your application to obtain new access tokens.

> Note: Save refresh tokens in secure long-term storage and continue to use them as long as they remain valid. Limits apply to the number of refresh tokens that are issued per client-user combination, and per user across all clients, and these limits are different. If your application requests enough refresh tokens to go over one of the limits, older refresh tokens stop working.

### Scopes (WIP)

Scopes let you specify exactly what type of access you need. Scopes limit access for OAuth tokens. They do not grant any additional permission beyond that which the user already has.

For the web flow, requested scopes will be displayed to the user on the authorize form.

| Name        | Description|
| ------------- |:---------:|
| Service.read      | Read all calendars and events related to the user and the service. |
| Service.write      | *Read* and modify all calendars and events related to the user and the service. |
| ...      | ... |

#### Which scope(s) should I use?

| Need        | Scope(s) |
| ------------- |:---------:|
| Access to the service related calendars and events, but not modify it. | Service.read |
| Access to the service related calendars and events and modify it. This scope provides of *read* and write access     | Service.write|
| ... | ... |

### Scenarios

#### Web server applications

The Calendar42 OAuth 2.0 endpoint supports web server applications that use languages and frameworks such as PHP, Java, Python, Ruby, and ASP.NET.

We allow app developer to manage user data using an email as initial starting point without user interaction by adding the email_address as a parameter in the first oAuth call.

For that is required to accomplish the following requirements:

* The app needs to be registered on the C42 platform
* The email should be sent along in the call in the email_address parameter in the url.
* The email shouldn't belong to a user that has an active service subscription to the service.

For security reasons a Service is only allowed to manage planning of that email, as long as:

* The service CAN ONLY access user data created inside the service.
* The service CAN NOT act as the email address towards other users.

As soon as the service wants to do any of the above, the user needs to approve the relation between his email and the service. This verification can be implicitly triggered based on actions of the user (e.g: sharing an event) or explicitly by the service

> If any of the above list requirements are not covered or a non accepted action is triggered the API would respond with an error code to notify the app that it should ask the user for a service verification.

#### Installed applications

(WIP)

#### Client-side (JavaScript) applications

(WIP)

#### Applications on limited-input devices

(WIP)

### Technical implementation

By sending along an email_address param the oAuth flow can result in a flow that doesn't require any user interaction but still results in a user with which the app can manage data for that user.
A registered oAuth App related to a Service requests the following:

```
https://calendar42.com/oauth2/authorize?email_address=someone@somesite.com&app=&token=&scope=...
```

Different actions would be performed based on the current status of the email_address used to request authorization:

| Status         | Performed action |
| ------------- |:---------:|
| email_address is not in C42 | (WIP) |
| email_address is related to inactive user in C42 | (WIP) |
| email_address is related to active user in C42 | (WIP) |
| email_address is related to an inactive ServiceUser of service already (also diff app)    | (WIP) |
| email_address is related to user with an (in)active service-subscription to service         | Access to normal oAuth flow |
| Scope requested is a full scope, not just service                                            | Forbidden |

> In all cases the service will be checked to verify that this app is registered and have access to the requested scopes

Despite this process doesn't require of any user action, it is REQUIRED to perform the oAuth through the browser.
In the case that no user action is required, a solution would be:

1. After to successfully log in in the app, redirect to the Calendar42 oAuth login page, requesting in this way of the authorization.
1. Preform all required redirections to finalize the authorization to our servers.
1. On success redirect to the logged in page, where the token will be used to proceed of all actions to the Calendar42 API.

In this case the user experience could be a 'longer' response time from the login page.
Different options are available like showing a loader with a message explaining which actions are happening in the background.
In a Smartphone Native app a Webview can be opened in the background and make this process totally invisible for the user.

### Common errors for the authorization request
