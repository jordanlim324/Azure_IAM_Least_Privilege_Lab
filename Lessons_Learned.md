# Lessons Learned - Azure IAM Least Privilege Lab

## Overview
Document the key lessons, insights, and takeaways from implementing and working through the Azure IAM Least Privilege Lab project. This document is designed to assist in review when revisiting the project.


## Design Trade-offs
- Recursive group ownership design:
   - Within the README for 01. Users_and_Groups, I noted that it was quite easy for an ownership loop to occur within my project, with administrators being able to run their own security group, but this led to the question of "Who will oversee and/or govern the administrators?", with little in the way of auditability and accountability to stop administrators. To resolve this loop, I, as the root administrator, acted as the "CEO" and gave myself ownership of the administrator group to provide accountability and auditability for the administrator group.
- Guest/B2B contractor identity vs native account
   - Within 01. Users_and_Groups, I used an external guest invite to mirror how enterprises separate third party identities from employees. Guest accounts will typically have different sign on behaviors and may have less privilege than a full fledged employee (e.g tenant-specific URL to sign into Azure, read only access for certain resources).
- */write wildcard for the employee role:
   - As noted in the README for 02. RBAC_Roles, the employee has an overarching */write wildcard permission for every resource that would have been in the resource group. Within a true production environment, an employee would have dedicated write permissions to resources they need access to, rather than the entire resource itself. (E.g. Write permissions to a specific blob storage service)
- Temporary Password Distribution as a currently unresolved tradeoff
   - While forcing a password reset upon the first login reduces exposure, it doesn't eliminate it entirely. Whenever an administrator generates the temporary password to be provided, they will still know the password until the user goes into the system and changes it. I accepted this gap for the lab rather than building out a secure distribution mechanism, as solving this risk would require tooling (like an automated onboarding system), which is outside this project's scope.
- Owner vs Contributor permissions:
   - Also noted in the README for 02. RBAC_Roles, the administrators of the group were scoped to Contributor, rather than Owner. As a response to the recursive group ownership design mentioned earlier, an admin would need someone with elevated access to grant a co-worker the necessary permissions on the administrator's behalf, in this case, being the root tenant. Both the recursive group ownership design and owner vs contributor permissions aimed to enforce the separation of duties.

## Technical Discoveries During The Project
Since this was my first time working in Azure's IAM and Entra ID spaces, I was surprised to discover some systems and decisions from Microsoft that I did not consider or register as a feature.
- Security Defaults is a feature that is enabled by default on free-tier tenants. There is no additional cost or license needed for baseline MFA and legacy authentication blocking.
- Guest and contractor sign ins do not use a traditional or generic Azure URL to sign into their portals, they require a specific tenant portal URL to access resources.
- Due to the custom role, specifically the wildcard write permission, for the Employee role, the role got automatically classified by Azure as a "Privileged Administrator Role", so the platform will recognize and flag potential role design issues.
- Azure can be accessed via the Azure Portal or through Azure CLI, and I had to ensure that my RBAC implementation could hold no matter the access methodology.

## Open Security Concerns From Risk Register
- In the risk register created in 04.Mini_Audit_GRC, there were several risks that were either unmitigated, partially mitigated, or just identified. Below is a list of the risks that were deemed security concerns, and how I'd fix them in a future iteration.
   - R03
      - The wildcard role created for Employee users, is one of the biggest concerns of role based access within the limits of a free Azure subscription. Employees should not have such elevated privileges, with even Microsoft Azure specifically warning me of such broad permissions given to a group.
   - R05
      - Uncontrolled role assignment could allow users to obtain elevated privileges without authorization or approval, potentially resulting in unauthorized access to resources beyond their intended role.
   - R06
      - Temporary credentials were manually distributed to users without a defined secure distribution process, which could lead to credential exposure during account provisioning and compromised credentials before the user resets the temporary credential.
   - R07
      - Temporary passwords provided for initial sign-in could allow IT or administrative personnel to authenticate as the intended user before the user changes the credential. This could allow administrators to perform unauthorized activities under the user's identity.

## Framework Alignment
- Risks identified within the Risk Register were mapped to NIST CSF 2.0 functions and select MITRE ATT&CK techniques. This exercise was designed to translate the technical controls and risks identified into standardized governance and threat modeling language.
- See 04.Mini_Audit_GRC - Framework_Alignment_Chart for more details.

## What I'd Do Differently At An Enterprise Scale
- As a lab to familiarize myself with IAM principles for a fictional company, I understand that not everything in this lab could be considered best practice for an enterprise. One of the biggest points that I ended up realizing during this project is that this project doesn't truly reflect the enterprise, rather a team or department in a company.
- Manual Tasks
   - Manual creation of users, such as how I had done for this lab, is unfeasible for an enterprise scale. Production identity and access management flows would be automated, with HR driving the lifecycle workflow, rather than an admin manually creating each and every user.
   - Similarly, security groups were manually created and populated. Membership within a group would typically be based off of rules or groups, such as department, job title, etc., and access would follow the roles that were assigned to the user, rather than being manually updated.
   - Within an enterprise environment, an organization would typically route roles through Privileged Identity Management (PIM) with just-in-time (JIT) elevation and approval workflows. My current workflow relies on roles being handed out by the root account based on the user type (Admin, Employee, Contractor).
   - Regarding the contractor/B2B role, I, as the root account, manually onboarded, and would have to manually offboard, the contractor account. Using a P2 license in Azure would grant access based on contract end date, without having an administrator remember to offboard a contractor.
- Monitoring, Alerting, and Auditing
   - The lab itself is not integrated with any monitoring, logging, alerting, or auditing tools. An enterprise IAM implementation would pair Role Based Access Controls with logs detailing sign-ins, audit trails, and a SIEM (e.g. Microsoft Sentinel) to detect unusual access patterns and allow analysts to proactively monitor for threats.
- Hybrid workflow
   - This lab is based solely off of the cloud, and does not factor the potential of a hybrid cloud environment.

## Skills Learned
- Identity and Access Management
- Role-Based Access Control (RBAC)
- Application of Least Privilege Principles
- Custom Azure Role Creation (JSON Role Definitions)
- Security Group Governance
- Azure CLI for identity and access verification
- External/Guest identity management for B2B/Contractor access
- GRC Translation of Technical Controls
- Risk Register creation
- Framework Mapping
- Technical Documentation