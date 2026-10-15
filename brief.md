Version: NAFATH-V1
Track: Cybersecurity

## Overview
The login service is one journey for a citizen using a phone or browser. The Android app asks only for the permissions it needs (Mobile). The device resolves the service address, where DNS over HTTPS protects the lookup but not the connection itself (Networking). OpenID Connect, built on OAuth 2.0, tells each government service who the citizen is (Software). The citizen proves identity with a second factor, and phishing-resistant methods matter most because one account unlocks many services (Cybersecurity). An AI model watches for suspicious logins, so its risks must be managed first (AI). Finally, every login creates personal data that the authority must collect and protect lawfully (Data). Because one account opens many services, phishing-resistant authentication is the control that protects the whole chain.
## Software

OAuth 2.0 is an authorization framework: it lets an application obtain limited access to a user's resources without sharing the password. OpenID Connect (OIDC) is an identity layer built on OAuth 2.0. It adds an ID Token and standard claims so a service can verify who the user is after the identity provider authenticates them. For a single sign-on service, OIDC is the right choice for login, while OAuth 2.0 alone suits delegated access to resources.

Resource: OpenID Connect Core 1.0 - https://openid.net/specs/openid-connect-core-1_0.html

## AI

The NIST AI Risk Management Framework (AI RMF 1.0) organizes risk work into Govern, Map, Measure and Manage, and defines seven trustworthy characteristics. Before launch, the authority must manage accuracy, because false alerts could block citizens from services; bias, if some devices or networks are flagged unfairly; privacy of login data; resilience against attackers who evade or poison the model; and explainability, with human review and an appeal route. Clear accountability must be assigned under Govern.

Resource: Artificial Intelligence Risk Management Framework (AI RMF 1.0), NIST AI 100-1 - https://doi.org/10.6028/NIST.AI.100-1

## Mobile

Android apps run in a sandbox and can access only their own data unless permissions are granted. Normal permissions are granted automatically, but dangerous permissions, which touch private user data, must be requested at runtime on Android 6.0 and later. The login app should declare only what it needs and ask in context, when the user starts a feature such as scanning a QR code with the camera. Denied requests must not break the app.

Resource: Request runtime permissions - https://developer.android.com/training/permissions/requesting

## Networking

## Cybersecurity

## Data

## Misconception in My Track

## Open Question
