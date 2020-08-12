---
permalink: /api/authentication
title: Authenticating with the API
---

# Overview 

We have two methods of authenticating with the TRA API - Google OAuth with JSON Web Tokens (JWT) issued by Google, or TRA API Keys. 
Both schemes are detailed below. 

## JWT Authentication 
We use Google Authentication so that we can identify the user submitting data to the TRA API from the TRA Mobile app. More information can be found about JWT tokens [here](https://jwt.io/), but the basic premise is that JWT tokens, defined in RFC 7519, are JSON objects which are signed by a party that can be used to authenticate users. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA. Google OAuth has implemented JWTs so that we can retrieve JWTs client-side which are passed from the Mobile app to the API via a header, which we can then use to authenticate a user. These tokens expire every hour.

## API Key Authentication