# Azure_IAM_Least_Privilege_Lab

Demonstrating least-privilege IAM design in Microsoft Azure's EntraID using free-tier RBAC and Security Defaults.

## Project Overview
This project is designed to leverage free Azure resources to understand and practice IAM principles for a fictionalized organization called Shirabuki Corporation. The primary goal of this project is to build a practical, demonstrable experience  with enterprise access control patterns before applying them in a production environment. Shirabuki Corp. has two admins, three employees, and one contractor.

## Skills Demonstrated
- Least privilege access design
- Custom RBAC roles
- Group-based access assignment
- Security baseline configurations
- Infrastructure documented as code

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
├── 01_Users_and_Groups/
│   ├── README.md
│   └── Screenshots/
├── 02_RBAC_Roles/          (in progress)
│   ├── README.md
│   ├── EmployeeCustomRoleDefinition.json
│   └── Screenshots/
```

## Scenarios and Table of Contents
| Scenario | Description | Status |
|---|---|---|
| [01 - Users and Groups](./01_Users_and_Groups/README.md) | Personas, security groups, and ownership/governance decisions for Shirabuki Corp | ✅ Complete |
| [02 - RBAC Roles](./02_RBAC_Roles/README.md) | Custom least-privilege roles assigned to groups | 🔧 In Progress |

## Architecture Overview
TBD

## Prerequisites
This project was built using only Microsoft Azure's free tier plan. To reproduce this project, the only things needed are:
- Microsoft Account
- Azure free tier tenant
- Time and patience

## License Note
This project uses the MIT license.
