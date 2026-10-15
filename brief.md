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

DNS over HTTPS (DoH, RFC 8484) sends DNS queries and answers inside an HTTPS connection, so they gain TLS encryption and integrity. For users of the login service, it hides which domain names their device looks up from people on the same network and stops tampering with DNS answers in transit. It does not hide queries from the resolver itself, or the destination IP address, and it does not make a fake website safe.

Resource: RFC 8484 - DNS Queries over HTTPS (DoH) - https://www.rfc-editor.org/rfc/rfc8484

## Cybersecurity

An authentication method is phishing-resistant when it cannot be tricked into giving a valid secret or code to a fake site; NIST calls this verifier impersonation resistance. Qualifying methods bind the credential to the real website's domain: FIDO2/WebAuthn passkeys, hardware security keys and PIV smart cards. SMS codes, one-time password apps and push approvals do not qualify, because a user can be fooled into handing them over or approving them.

Resource: NIST SP 800-63B-4, Digital Identity Guidelines: Authentication and Authenticator Management - https://pages.nist.gov/800-63-4/sp800-63b.html

## Data

Oman's Personal Data Protection Law (Royal Decree 6/2022) requires a controller to obtain the person's explicit consent and to tell them in writing, before processing, who is processing their data, why, and what rights they have. The controller must appoint a data protection officer, keep the data confidential, notify the ministry and the person of a breach, and transfer data outside Oman only under the Executive Regulation. Its scope for government bodies should be checked.

Resource: Royal Decree 6/2022, Personal Data Protection Law - https://decree.om/2022/rd20220006/

## Misconception in My Track

A common belief is that any multi-factor authentication, such as a password plus an SMS code, stops phishing. This is wrong. A fake site can relay the password and the code to the real service in real time. NIST SP 800-63B-4 defines phishing resistance as the protocol's ability to stop secrets and valid authenticator outputs reaching an impostor without relying on the user's vigilance, and it requires cryptographic authentication. Passwords are not phishing-resistant, and relayable codes do not meet this either. Proof: SP 800-63B-4, Section 3.2.5, Phishing Resistance.

## Open Question

Do passkeys that sync across a citizen's devices through a cloud account still count as phishing-resistant under NIST SP 800-63B-4? I would also check how account recovery should work when a citizen loses their phone, without creating a phishable fallback.
