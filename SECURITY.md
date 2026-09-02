# Security Policy

## Internee.pk User Authentication & Data Security

This document defines the security requirements for reporting, handling, and protecting vulnerabilities related to user authentication and sensitive data.

## Scope

This security policy covers:

* Two-Factor Authentication (2FA)
* Google Authenticator / TOTP
* OAuth 2.0 authentication and authorization
* User sessions and tokens
* Sensitive user data
* AES-256 encryption
* Staging databases
* Synthetic test datasets
* Authentication APIs and related services

## Security Vulnerability Reporting

Security vulnerabilities should be reported privately through the approved Internee.pk security channel.

Do not publicly disclose a vulnerability before it has been investigated and appropriately remediated.

A security report should include:

* Vulnerability description
* Affected application or component
* Steps to reproduce
* Potential security impact
* Relevant timestamps
* Sanitized screenshots or logs
* Suggested remediation, if available

Never include passwords, TOTP secrets, OAuth tokens, encryption keys, or other credentials in a report.

## Authentication Security

### Two-Factor Authentication

2FA should be enabled for accounts where required by the application's security policy.

The implementation should:

* Use TOTP-compatible authentication.
* Protect TOTP secrets.
* Rate-limit failed verification attempts.
* Prevent brute-force verification.
* Log authentication events.
* Provide secure account-recovery procedures.
* Invalidate or rotate recovery credentials when necessary.

### OAuth 2.0

OAuth 2.0 implementations must:

* Use HTTPS.
* Validate redirect URIs.
* Protect authorization codes.
* Use PKCE where applicable.
* Protect access and refresh tokens.
* Use appropriate token expiration.
* Validate tokens correctly.
* Request minimum required scopes.
* Never expose confidential client secrets in frontend code.

## Data Encryption

Sensitive data must be protected using appropriate encryption controls.

Where AES-256 is specified:

* Use a secure AES-256 implementation.
* Prefer authenticated encryption such as AES-GCM.
* Protect encryption keys separately from encrypted data.
* Never hard-code encryption keys.
* Never store encryption keys in Git.
* Restrict access to encryption keys.
* Establish key rotation and revocation procedures.
* Never log plaintext sensitive information or encryption keys.

## Staging Data

The staging environment should not contain unnecessary production data.

Preferred approach:

1. Use synthetic data whenever possible.
2. Mask or anonymize sensitive fields when staging data is required.
3. Restrict staging database access.
4. Encrypt sensitive staging data.
5. Delete temporary test datasets when no longer required.

## Synthetic Data

Synthetic datasets may be generated using approved data-generation tools such as Mockaroo.

Synthetic datasets must not contain:

* Real passwords
* Real authentication secrets
* Real OAuth tokens
* Real API keys
* Real encryption keys
* Unnecessary real customer information

## Credential Exposure

If a password, token, secret, encryption key, or other credential is accidentally exposed:

1. Treat it as compromised.
2. Revoke or disable it immediately.
3. Rotate the affected credential.
4. Investigate possible unauthorized access.
5. Remove the exposed information from the repository where appropriate.
6. Record the incident.
7. Review controls to prevent recurrence.

Removing a secret from the latest Git commit does not make the credential safe. The credential must still be revoked or rotated.

## Security Testing

Security testing should be performed only against systems and environments for which authorization has been provided.

Testing should include:

* 2FA verification testing
* Brute-force protection testing
* Session-management testing
* OAuth flow validation
* Token expiration testing
* Authorization testing
* Encryption/decryption testing
* Access-control testing
* API security testing

Testing must not intentionally:

* Destroy production data.
* Access unauthorized user information.
* Disrupt production services.
* Expose credentials.
* Create persistent unauthorized access.

## Severity Classification

| Severity      | Description                                                                                                              |
| ------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Critical      | Severe authentication bypass, major account takeover, encryption-key compromise, or significant sensitive-data exposure. |
| High          | Significant vulnerability that could enable unauthorized access or sensitive-data exposure.                              |
| Medium        | Security weakness with limited or conditional impact.                                                                    |
| Low           | Minor security weakness or hardening opportunity.                                                                        |
| Informational | Security recommendation without significant immediate impact.                                                            |

## Incident Response

For confirmed security incidents:

1. Identify the affected system.
2. Contain the incident where necessary.
3. Revoke compromised credentials or tokens.
4. Preserve relevant evidence.
5. Investigate the scope and impact.
6. Remediate the vulnerability.
7. Validate the fix.
8. Document the incident.
9. Monitor for recurrence.

## Repository Security

The repository must not contain:

* Passwords
* TOTP secrets
* OAuth client secrets
* Access tokens
* Refresh tokens
* AES encryption keys
* Private keys
* Database credentials
* Production user data

Secret scanning and appropriate repository access controls should be enabled.

## Responsible Disclosure

Security researchers and authorized testers should report vulnerabilities privately and avoid accessing, modifying, or exposing data that does not belong to them.

Security testing should remain within the authorized scope.

## Policy Review

This document should be reviewed:

* At least annually.
* After major security incidents.
* After significant authentication changes.
* After changes to encryption architecture.
* After major changes to the application's security architecture.

## Ownership

**Organization:** Internee.pk
**Project:** User Authentication & Data Security
**Owner:** Security / Development Team
**Classification:** Internal
**Review Frequency:** Quarterly
