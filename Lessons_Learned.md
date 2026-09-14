# Lessons Learned - Azure IAM Least Privilege Lab

## Overview
Document the key lessons, insights, and takeaways from implementing and working through the Azure IAM Least Privilege Lab project. This document is designed to assist in review when revisiting the project.


## Design Trade-offs
- */write wildcard for the employee role:
   - As noted in the README for 02. RBAC_Roles, the employee has an overarching */write wildcard permission for every resource that would have been in the resource group. Within a true production environment, an employee would have dedicated write permissions to resources they need access to, rather than the entire resource itself. (E.g. Write permissions to a specific blob storage service)
- Recursive group ownership design:
   - Within the README for 01. Users_and_Groups, I noted that it was quite easy for an ownership loop to occur within my project, with administrators being able to run their own security group, but this led to the question of "Who will oversee and/or govern the administrators?", with little in the way of auditability and accountability to stop administrators. To resolve this loop, I, as the root administrator, acted as the "CEO" and gave myself ownership of the administrator group to provide accountability and auditability for the administrator group.
- 

## Technical Discoveries During The Project
Since this was my first time working in Azure's IAM and Entra ID spaces, I was surprised to discover some systems and decisions from Microsoft that I did not consider or register as a feature.
- Security Defaults is a feature that is enabled by default on free-tier tenants. There is no additional cost or license needed for baseline MFA and legacy authentication blocking.
- Guest and contractor sign ins do not use a traditional or generic Azure URL to sign into their portals, they require a specific tenant portal URL to access resources.
- Due to the custom role, specifically the wildcard write permission, for the Employee role, the role got automatically classified by Azure as a "Privileged Administrator Role", so the platform will recognize and flag potential role design issues.
- Azure can be accessed via the Azure Portal or through Azure CLI, and I had to ensure that my RBAC implementation could hold no matter the access methodology.

## Open Security Concerns From Risk Register
- In the risk register created in 04.Mini_Audit_GRC, there were several risks that were either unmitigated, partially mitigated, or just identified. Below is a list of the risks that were deemed security concerns, and how I'd fix them in a future iteration.
   - R05
      - Uncontrolled role assignment could allow users to obtain elevated privileges without authorization or approval, potentially resulting in unauthorized access to resources beyond their intended role.
   - R06
      - Temporary credentials were manually distributed to users without a defined secure distribution process, which could lead to credential exposure during account provisioning and compromised credentials before the user resets the temporary credential.
   - R07
      - Temporary passwords provided for initial sign-in could allow IT or administrative personnel to authenticate as the intended user before the user changes the credential. This could allow administrators to perform unauthorized activities under the user's identity.

## What I'd Do Differently At An Enterprise Scale
- As a lab to familiarize myself with IAM principles for a fictional company, I understand that not everything in this lab could be considered best practice for an enterprise. One of the biggest points that I ended up realizing during this project is that this project doesn't truly reflect the enterprise, rather a team or department in a company.
- 
## Skills Learned
- Identity and Access Management
- 
- 
