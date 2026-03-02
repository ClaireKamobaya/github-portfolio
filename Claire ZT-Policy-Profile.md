**1. ZTA Component Definitions**



Policy Engine (PE)

The Policy Engine is the "brain" of a Zero Trust Architecture. Its sole job is to make the access decision grant or deny by continuously evaluating all available security signals such as user identity, device health, location, and threat intelligence against the organization's defined policies. In the context of the Golden State Water Treatment Facility, the PE decides whether an HR staff member attempting to access the PII database actually meets every required condition before any access is allowed.

Policy Administrator (PA)

The Policy Administrator is the "rule setter and messenger." It does not make the access decision itself instead, it receives the Policy Engine's verdict and translates it into a concrete command. If the PE says "grant access," the PA sends the signal to open the session. If the PE says "deny," the PA instructs the enforcement layer to block it. At the Water Treatment Facility, the PA would configure the communication channel between the decision layer and the gate, ensuring the right doors open only for the right people.

Policy Enforcement Point (PEP)

The Policy Enforcement Point is the "gatekeeper." It is the component that physically sits between the user and the protected resource, and it is the only component that can actually allow or block the connection. It acts entirely on the PA's instructions it has no decision-making authority of its own. At the facility, the PEP would be the proxy or access gateway that intercepts every request to the HR PII database and either permits or terminates the session based on what the PA has directed.



**2. Core Principle Application**

*Chosen Principle:* Verify Explicitly

The Verify Explicitly principle requires that every access request be fully authenticated and authorized using all available signals — no user, device, or location is ever trusted by default.

The Policy Engine (PE) enforces this at the Golden State Water Treatment Facility in the following way: when an HR manager attempts to access the employee PII database, the PE does not simply check their username and password. Instead, it simultaneously evaluates multiple signals confirming the user's identity via multi-factor authentication, verifying that the device has up-to-date security patches and an active EDR agent, and checking that the request originates from a trusted network location (either the facility's internal network or an approved VPN endpoint).

For example, if the HR manager is authenticated but is attempting to log in from an unrecognized personal device at a coffee shop with no VPN, the PE will evaluate those signals and return a Deny decision even though the credentials are valid. This demonstrates Verify Explicitly in action: identity alone is never sufficient. Every signal must be checked every single time.



**3. Simplified Policy Table**

*Target Resource:* HR Employee PII Database Golden State Water Treatment Facility

Policy Requirement (Signal)Condition to be Met by UserAction if Condition is MetUser IdentityUser must be authenticated via MFA and belong to the authorized HR role group in the directoryGrant AccessDevice PostureUser's device must be facility-managed, with current OS patches applied and an active endpoint protection agent runningGrant AccessNetwork ContextRequest must originate from the facility's internal network or an approved, authenticated VPN endpoint not a public or unrecognized networkGrant Access



**4. Submission Details**

Git Repository Metadata

Project: Lab 03: Zero Trust Policy Profile

Filename: ZT-Policy-Profile.md

Commit Message: Add Lab 03 ZT-Policy-Profile.md defining ZTA components, Verify Explicitly principle, and HR PII access policy table — https://github.com/ClaireKamobaya/github-portfolio

Due Date: March 2, 2026

