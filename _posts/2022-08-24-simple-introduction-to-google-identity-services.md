---
layout: post
title: "Simple Introduction to Google Identity Services"
---

With Google Sign-In [going away](https://developers.googleblog.com/2022/03/gis-jsweb-authz-migration.html), developers would need to work with a new service called Google Identity.

But As with Google, this has become a mess of docs and seemingly relevant code which will render your app unusable. My team spent two days implementing both of them due to this mess. So I am gonna make it simple for you to decide.

With this Google Identity service, Google has designed two flows

1. Sign-In flows - Apps that just need to know the user’s email and name for auth
2. Authorization - Apps that need to access Docs API, Sheets API on behalf of the user.

## Sign-In flows

This is the newest sign-in-flow for developers without much need for handling oauth.

It goes like this,

1. App code triggers a google-sign in
2. your code gets back JWT token
3. using a standard JWT decoder, you can read names and emails.

It is that simple.

Steps:

1. Configure WebApp consent screen in GCP. Read [https://developers.google.com/identity/gsi/web/guides/get-google-api-clientid](https://developers.google.com/identity/gsi/web/guides/get-google-api-clientid)
2. Load Google Library - [https://developers.google.com/identity/gsi/web/guides/client-library](https://developers.google.com/identity/gsi/web/guides/client-library)
3. Display the Sign-In Button - [https://developers.google.com/identity/gsi/web/guides/display-button](https://developers.google.com/identity/gsi/web/guides/display-button)
4. Add A Server script/endpoint to handle the JWT token.

## Authorization

If you are the developer building integration with Google APIs, forgot above and you must do Authorisation flow. I know names are confusing. But let it be. You need Auth from the user to access his/her google docs. So, Authorisation for you.

Steps:

1. Load the client library into your webpage - [https://developers.google.com/identity/oauth2/web/guides/load-3p-authorization-library](https://developers.google.com/identity/oauth2/web/guides/load-3p-authorization-library)
2. Trigger and Process the Google OAuth flow - It’s a typical OAuth2 Workflow most platforms offer like Github, Bitbucket, Facebook. [https://developers.google.com/identity/oauth2/web/guides/use-code-model](https://developers.google.com/identity/oauth2/web/guides/use-code-model). (See note below)

Note: There are two models of authorization: Code model and Token model. [https://developers.google.com/identity/oauth2/web/guides/choose-authorization-model](https://developers.google.com/identity/oauth2/web/guides/choose-authorization-model).

Token model is useful only if all the actions are done from the user’s browser. If you want to use that, Refer [https://developers.google.com/identity/oauth2/web/guides/use-token-model](https://developers.google.com/identity/oauth2/web/guides/use-token-model).

If your apps work offline, Go with the Code model as shown in the above steps.

This was an introductory article to give a general idea of Google Identity Services. It is not a step-by-step tutorial. Google Docs has provided all that but in a messy structure. So I have given you direct links. Enjoy!

*Originally published on [HackerNoon](https://hackernoon.com/simple-introduction-to-google-identity-services).*
