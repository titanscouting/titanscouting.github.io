---
permalink: /api/authentication
title: Authenticating with the API
---

# Overview 

We have two methods of authenticating with the TRA API - Google OAuth with JSON Web Tokens (JWT) issued by Google, or TRA API Keys. These authentication methods are checked via Express middleware, which reject requests that fail authentication. Both authentication schemes are detailed below. 

## JWT Authentication 
We use Google Authentication so that we can identify the user submitting data to the TRA API from the TRA Mobile app. More information can be found about JWT tokens [here](https://jwt.io/), but the basic premise is that JWT tokens, defined in RFC 7519, are JSON objects which are signed by a party that can be used to authenticate users. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA. Google OAuth has implemented JWTs so that we can retrieve JWTs client-side which are passed from the Mobile app to the API via a header, which we can then use to authenticate a user. These tokens expire every hour.

## API Key Authentication
While JWT authentication is suitable when an end-user application is contacting the API, this type of authentication is not suitable for applications which require permanent access in a more traditional manner. For these situations, the API supports API key authentication. The API issues both a client ID and a client secret to a user requesting an API key via an authenticated route. The client ID is a generated UUID, and the client secret is encrypted and hashed with `bcrypt` and stored in the database. This hash is then compared upon an authentication request. 

## Controlling route access
By default, any authenticated route can be accessed via JWT or API Key authentication. However, it is not desirable for some routes to be accessed via API key, such as the route to create an API key. In this scenario, you may use the `auth.noAPIKey` middleware to only allow JWT authentication for a given route.