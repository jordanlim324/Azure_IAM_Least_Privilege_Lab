## Summary
For the fictionalized Shirabuki Corporation, I decided to create distinct users, groups and personas for the project. I could have easily created an administrator account and worked with Azure in that regard, but this would severely limit the usefulness and design of the project, which was to practically apply Principle of Least Privilege and Role Based Access Control within a free and safe environment.
This was an important distinction as I wanted to closely emulate real-world enterprise environments without overcomplicating my understanding of the concepts at play.

## The Problem
Shirabuki Corporation currently has two administrators, three employees, and one contractor. Shirabuki Corporation wants each user to be grouped by their role, and have access controls per role assignment.

## What Was Built
- Resource Group
   - Shirabuki_Corporation
- Users
   - Two administrator accounts (Shirabuki Admin 1 and Shirabuki Admin 2)
   - Three employee accounts (Shirabuki Employee 1, Shirabuki Employee 2, Shirabuki Employee 3)
   - One contractor account (Shirabuki Contractor 1)
- Security Groups
   - sg-shirabuki-admins
   - sg-shirabuki-employees
   - sg-shirabuki-contractors
- Roles
   - Scoped within 02.RBAC_Roles/README.md

## Ownership Decisions
The group "sg-shirabuki-admins" is owned by the root tenant account, in this case, my personal account. I had initially wanted the administrators to own their own security group, but upon closer scrutinization, I realized this would lead to a recursive path of ownership.
Both the employees and contractors security groups are owned by Admins 1 and 2. While working on this section, I wanted the admin security group to own the employee and contractors group, but this couldn't be done due to limitations of EntraID, but also, a user should own a different group, as having a whole group owning another could lead to non-separated duties, leading to issues with accountability and auditability for which admin performed which action.

## Screenshots
- Users List
![Microsoft Azure screenshot of users list](Screenshots/Users_List-Microsoft_Azure.png)

- Groups List
![Microsoft Azure screenshot of security groups list](Screenshots/Security_Group_List-Microsoft_Azure.png)

- Group Owners
   - Admin Owners
   ![Microsoft Azure screenshot of admin owners list](Screenshots/Security_Group_Admins_Owners-Microsoft_Azure.png)
   - Employee Owners
   ![Microsoft Azure screenshot of employee owners list](Screenshots/Security_Group_Employee_Owners-Microsoft_Azure.png)
   - Contractor Owners
   ![Microsoft Azure screenshot of contractor owners list](Screenshots/Security_Group_Contractor_Owners-Microsoft_Azure.png)

- Group Members
   - Admin Members
   ![Microsoft Azure screenshot of admin members list](Screenshots/Security_Group_Admins_Members-Microsoft_Azure.png)
   - Employee Members
   ![Microsoft Azure screenshot of employee members list](Screenshots/Security_Group_Employee_Members-Microsoft_Azure.png)
   - Contractor Members
   ![Microsoft Azure screenshot of contractor members list](Screenshots/Security_Group_Contractor_Members-Microsoft_Azure.png)