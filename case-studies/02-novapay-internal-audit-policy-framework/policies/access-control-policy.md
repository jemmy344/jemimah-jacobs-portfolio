# NovaPay Access Control Policy

> Written by Jemimah Jacobs in the case-study role of Head of Corporate IT and Access Management. Part of the [NovaPay Internal Audit and Policy Framework](../README.md) group project. NovaPay is a fictional organisation.

## Document control

| Field | Value |
|---|---|
| **Organisation** | NovaPay |
| **Hierarchy tier** | Policy |
| **Document owner** | Chief Information Security Officer (CISO) |
| **Prepared by** | Head of Corporate IT and Access Management |
| **Approving authority** | Chief Executive Officer (CEO) |
| **Version** | 1.0 |
| **Date prepared** | 25/09/2026 |
| **Review frequency** | Annually |
| **Next review** | 25/09/2027 |
| **Distribution** | All employees, contractors and relevant third parties |

---

## 1. Purpose

This policy sets out how NovaPay grants, manages, reviews and removes access to its information and systems. Its aim is to reduce unauthorised access to customer data, payment information and other sensitive assets.

## 2. Scope

This policy applies to employees, contractors and third-party suppliers who access NovaPay systems or information. It covers the banking app, payment gateway, Azure-hosted services, corporate systems and the accounts used to administer them.

## 3. Access control principles

### 3.1 Need to know and least privilege
Users are only given access to the information and systems they need for their role. The level of access must be the minimum needed to perform those tasks.

### 3.2 Segregation of duties
Critical tasks should be separated so that no one person has unchecked control over a process. For example, where possible, the person who approves a payment should not be the person who executes it.

### 3.3 Role-based access
Access to systems is based on the user's role. Access must be formally requested and approved before it is granted.

## 4. Access requests and approval

A manager must request access for a user. The relevant Department Head (System Owner) must approve the request, and the Head of Corporate IT must grant the approved access.

## 5. Confidentiality agreements

Employees, contractors and relevant third parties who are given access to confidential information must agree to confidentiality obligations before access is granted.

## 6. Unique identifiers

Each user is assigned a unique username or identifier. The principle of *one user, one ID* applies so that every action can be traced to an individual. User accounts and passwords must not be shared.

## 7. Authentication

Users must be identified and authenticated before gaining access to systems and information. **Multi-factor authentication (MFA)** must be used for Azure-hosted services, remote access, payment systems and privileged accounts.

Initial passwords must be changed on first use. Vendor-supplied and default passwords must be changed before a system is put into use.

## 8. Access rights review

| Access type | Reviewed by | Frequency |
|---|---|---|
| Standard user access | Department Head (System Owner) | Every 6 months |
| Privileged access | Department Head (System Owner) | Every 90 days |
| Third-party access | Department Head (System Owner) | Every 90 days |

Inactive or unnecessary accounts must be investigated, and access updated or removed where appropriate. Each review and any actions taken must be documented.

## 9. Privileged and administrator accounts

Administrator access is only given to authorised users who need it for their role. Where possible, these users must have a separate administrator account for privileged tasks and use their normal account for everyday work.

Privileged and administrator accounts must not be shared or generic. A register of these accounts must be maintained, and their use must be logged and monitored. Temporary privileged access must only be granted for an approved period.

## 10. Changes to access and leavers

Managers must inform the Head of Corporate IT when a user changes role or leaves NovaPay. The Head of Corporate IT must update or remove the user's access promptly and keep a record of the action.

Third-party access must be removed when the agreed work ends or when access is no longer needed.

## 11. Exceptions

Any exception to this policy must be documented and approved by the Head of GRC, the CISO and the relevant Department Head (System Owner).

## 12. Compliance

Failure to comply with this policy may result in access being removed and, where appropriate, disciplinary or contractual action.

## 13. Review

This policy will be reviewed annually, or after significant changes to NovaPay's systems, working arrangements or security requirements.

## 14. Review log

| Date | Reviewer | Change | Owner confirmation | CISO approval |
|---|---|---|---|---|
| 25/09/2026 | Head of Corporate IT | Initial implementation | CISO | Approved |

## 15. Approval

| Role | Date |
|---|---|
| Document owner (CISO) | 25/09/2026 |
| Approving authority (CEO) | 25/09/2026 |

---

## References

1. ISO/IEC 27001:2022, *Information security, cybersecurity and privacy protection: Information security management systems: Requirements.* [iso.org/standard/27001](https://www.iso.org/standard/27001)
2. High Table, *ISO 27001 Access Control Policy: Ultimate Guide.* [hightable.io](https://hightable.io/iso-27001-access-control-policy-ultimate-guide/)
