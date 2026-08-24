# Two-Factor-athuntication
Secure Authentication & Data Security

Cybersecurity internship project demonstrating:

Two-Factor Authentication (2FA) with Google Authenticator / TOTP

OAuth 2.0 / OpenID Connect for secure sign-in

AES-256-GCM encryption for sensitive data

Synthetic user data for safe testing

Objective

Strengthen user authentication and data security while demonstrating practical cybersecurity controls in a web application.

Architecture

User
 |
 +--> Email + Password --> 2FA/TOTP --> Dashboard
 |
 +--> Continue with Google --> OAuth 2.0/OIDC --> Dashboard
 |
 +--> Sensitive Data --> AES-256-GCM --> Encrypted Database

Project Components

1. Two-Factor Authentication

The application uses TOTP-based 2FA compatible with Google Authenticator.

Login
  -> Password Verification
  -> Six-Digit TOTP Code
  -> Verification
  -> Dashboard

2. OAuth 2.0

Google sign-in is implemented using OAuth 2.0 / OpenID Connect.

Continue with Google
  -> Google Authentication
  -> User Authorization
  -> OAuth Callback
  -> Application Dashboard

OAuth client credentials are stored in environment variables and are never hard-coded.

3. AES-256-GCM

Sensitive demonstration data is encrypted before database storage.

Readable Synthetic Data
  -> AES-256-GCM
  -> Encrypted Ciphertext
  -> Database

AES-GCM provides confidentiality and integrity protection.

Dataset

The data/ directory contains synthetic records only:

users_synthetic.csv

users_synthetic.json

sensitive_data_demo.json

seed_synthetic_users.sql

MOCKAROO_SCHEMA.md

No real Internee.pk user records are included.

Security

Never upload these to GitHub:

.env
Passwords
OAuth Client Secrets
Access Tokens
Refresh Tokens
Encryption Keys
TOTP Secrets
Recovery Codes
Real User Data
Production Databases

Suggested Repository Structure

secure-authentication-data-security/
├── README.md
├── REPORT.md
├── requirements.txt
├── .env.example
├── .gitignore
├── app.py
├── auth/
├── security/
├── database/
├── data/
├── templates/
├── static/
└── tests/

Installation

python -m venv .venv

Windows:

.venv\Scripts\activate

macOS/Linux:

source .venv/bin/activate

Install dependencies:

pip install -r requirements.txt

Create .env from .env.example, configure local secrets, then run:

python app.py

Run tests:

pytest

Learning Outcomes

This project provides practical experience with:

Authentication

Multi-factor authentication

TOTP / Google Authenticator

OAuth 2.0 / OpenID Connect

AES-256-GCM encryption

Secure secret management

Synthetic test data

Basic security testing

Disclaimer

This is an educational internship demonstration, not a complete production security architecture. Production systems should additionally use HTTPS, CSRF protection, rate limiting, secure recovery, centralized key management, audit logging, dependency monitoring, and professional security testing.
