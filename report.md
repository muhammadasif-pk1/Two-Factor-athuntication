Project Title

Strengthening User Authentication and Data Security

1. Introduction

Modern applications handle sensitive user information and therefore require strong authentication and data-protection controls.

This project demonstrates three major security mechanisms:

Two-Factor Authentication using Google Authenticator

OAuth 2.0 / OpenID Connect for secure sign-in

AES-256-GCM encryption for sensitive information

Synthetic data is used for development and demonstration.

2. Objectives

Strengthen user authentication.

Add a second verification factor.

Provide secure third-party sign-in.

Protect sensitive information before database storage.

Demonstrate safe handling of application secrets.

Gain practical cybersecurity implementation experience.

3. Technologies

Technology

Purpose

Python

Application development

Flask

Web framework

SQLite

Development database

Google Authenticator

TOTP-based 2FA

OAuth 2.0 / OIDC

Google sign-in

Authlib

OAuth integration

PyOTP

TOTP generation and verification

Cryptography

AES-256-GCM

Mockaroo

Synthetic data generation

GitHub

Version control

4. Two-Factor Authentication

The TOTP flow is:

Email + Password
       ↓
Password Verification
       ↓
Google Authenticator
       ↓
Six-Digit Code
       ↓
Verification
       ↓
Dashboard

2FA adds a second authentication factor so that a password alone is not sufficient for access.

5. OAuth 2.0

The OAuth flow is:

Continue with Google
       ↓
Google Authentication
       ↓
User Authorization
       ↓
OAuth Callback
       ↓
Application Session
       ↓
Dashboard

The application does not collect the user's Google password. OAuth credentials are kept outside the source code.

6. AES-256-GCM

Sensitive information is protected using authenticated encryption:

Sensitive Data
      ↓
AES-256-GCM
      ↓
Ciphertext
      ↓
Database

The encryption key is stored separately from application source code.

7. Synthetic Dataset

Public repositories should not contain real user information. This project therefore uses fictional records for testing.

Example:

Name: Ayaan Khan
Email: ayaan.khan01@example.test
Phone: +92-300-555-0101
Role: user
2FA: enabled
OAuth: google

The .test domain makes the demonstration nature clear.

8. Testing Plan

Password Authentication

Valid credentials should authenticate; invalid credentials should be rejected.

2FA

A valid TOTP code should allow access; an invalid code should be rejected.

OAuth

Successful Google authentication should return the user to the application dashboard.

Encryption

Plaintext demo data should become ciphertext and only be recoverable with the correct key.

Dataset

Only synthetic records should be used.

9. Demonstration Screenshots

Recommended recording order:

Login page

2FA QR-code setup

Google Authenticator six-digit code

Successful dashboard

Continue with Google

Google authorization

OAuth dashboard

Readable synthetic data

AES-256-GCM encryption

Encrypted database values

Never show real credentials, OAuth secrets, tokens, TOTP secrets, encryption keys, or personal data.

10. Security Checklist

Password hashing

Two-Factor Authentication

TOTP verification

OAuth 2.0 / OIDC

AES-256-GCM

Environment-based secrets

.gitignore

Synthetic data

Basic automated tests

Production HTTPS

Centralized production key management

Full penetration testing

11. Conclusion

The project demonstrates how authentication, authorization, and encryption can work together to improve application security.

Google Authenticator adds an additional authentication factor, OAuth 2.0 provides a secure sign-in flow, and AES-256-GCM protects sensitive information before storage.

Using synthetic data makes the project suitable for a public GitHub demonstration without exposing real user information.

12. Future Improvements

HTTPS/TLS enforcement

CSRF protection

Rate limiting

Secure account recovery

WebAuthn / security keys

Centralized key management

Security event logging

Dependency vulnerability scanning

Penetration testing
