# Azure IAM Least Privilege Lab

Demonstrating least-privilege IAM design in Microsoft Azure's EntraID using free-tier RBAC and Security Defaults.

Initally dated: 06 August 2026

Most recent update: 20 August 2026

## Project Overview
This project is designed to leverage free Azure resources to understand and practice IAM principles for a fictionalized organization called Shirabuki Corporation. The primary goal of this project is to build a practical, demonstrable experience  with enterprise access control patterns before applying them in a production environment. Shirabuki Corp. has two admins, three employees, and one contractor.

## Skills Demonstrated
- Least privilege access design
- Custom RBAC roles
- Group-based access assignment
- Security baseline configurations
- Infrastructure documented as code
- Security Defaults
- MFA enforcement

## Tech Stack/Tools Used
- Microsoft EntraID (free tier)
- Azure RBAC
- Azure CLI
- Powershell
- Markdown

## Project Structure
```
Azure_IAM_Least_Privilege_Lab/
├── README.md
├── LICENSE
├── 01.Users_And_Groups/
│   ├── README.md
│   └── Screenshots/
├── 02.RBAC_Roles/
│   ├── README.md
│   ├── EmployeeCustomRoleDefinition.json
│   └── Screenshots/
├── 03.RBAC_Roles/
│   ├── README.md
│   ├── AzureCommands_EMP.md
│   └── Screenshots/
├── 04.Mini Self Audit - Governance, Risk, and Compliance         (in progress)
│   ├── README.md
│   └── Screenshots/
```

## Scenarios and Table of Contents
| Scenario | Description | Status |
|---|---|---|
| [01 - Users and Groups](./01.Users_and_Groups/README.md) | Personas, security groups, default configurations, and ownership/governance decisions for Shirabuki Corp | ✅ Complete |
| [02 - RBAC Roles](./02.RBAC_Roles/README.md) | Custom least-privilege roles assigned to groups | ✅ Complete |
| [03 - Access Verification](./03.Access_Verification/README.md) | Proof of role access enforcement | ✅ Complete |
| [04 - Mini Audit GRC](./04.Mini_Audit_GRC/README.md) | Assessing the project through the lens of a Governance, Risk, and Compliance audit | 🔧 In Progress |

## Architecture Overview
```mermaid
graph TD
    RootTenant["Root Tenant Account<br/>(Owner/Governance)"]

    subgraph Users["Users"]
        Admin1["Shirabuki_Admin_1"]
        Admin2["Shirabuki_Admin_2"]
        Emp1["Shirabuki_Employee_1"]
        Emp2["Shirabuki_Employee_2"]
        Emp3["Shirabuki_Employee_3"]
        Contractor["Shirabuki_Contractor<br/>(Guest)"]
    end

    subgraph Groups["Security Groups"]
        GAdmins["sg-shirabuki-admins"]
        GEmployees["sg-shirabuki-employees"]
        GContractors["sg-shirabuki-contractors"]
    end

    subgraph Roles["RBAC Roles"]
        RContributor["Contributor (Built-in)"]
        REmployee["Shirabuki_Employee_Custom_Role"]
        RReader["Reader (Built-in)"]
    end

    RG["Shirabuki_Corporation<br/>(Resource Group)"]

    RootTenant -.owns.-> GAdmins
    Admin1 -.owns.-> GEmployees
    Admin1 -.owns.-> GContractors
    Admin2 -.owns.-> GEmployees
    Admin2 -.owns.-> GContractors

    Admin1 -->|member of| GAdmins
    Admin2 -->|member of| GAdmins
    Emp1 -->|member of| GEmployees
    Emp2 -->|member of| GEmployees
    Emp3 -->|member of| GEmployees
    Contractor -->|member of| GContractors

    GAdmins -->|assigned| RContributor
    GEmployees -->|assigned| REmployee
    GContractors -->|assigned| RReader

    RContributor -->|scoped to| RG
    REmployee -->|scoped to| RG
    RReader -->|scoped to| RG
```

## Prerequisites
This project was built using only Microsoft Azure's free tier plan. To reproduce this project, the only things needed are:
- Microsoft Account
- Azure free tier tenant
- Time and patience

## License Note
This project uses the MIT license.
