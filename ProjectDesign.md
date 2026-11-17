# Project Design Document – CS 331
## Project Title: C-Smooth LLC
## Team Member(s): Jay Berry, Austin Mahon, Caden Anderson
### Objective (Purpose of the Project)

The primary objective of this project is to build a local Java application that simulates Role Based Access Control (RBAC). The application is meant to simulate an internal workplace with users assigned to roles with different permission levels. Users that do not have permissions will be restricted to certain actions.

The security features show that only authorized users will have access to relevant information and functions based on their role in the company. I.E. Admin can create/assign roles, developers can edit pages, and public users only have viewing permissions.

Users will be assigned roles by an administrator, authenticated through a login page, and the application will enforce permissions based on assigned roles. In addition actions performed by any role will be logged in a `log.txt` file.

The completed application will demonstrate how RBAC provides authorization, least privilege, and accountability. The project will show how security works while also keeping a log to show how a security threat can be traced back to previous actions.

### Scope

The project will simulate an office environment with multiple user roles that have different levels of access to actions and data.

#### Included Features:
- [ ] Simulated Public Data
- [ ] Login Interface
- [ ] Role Based Permissions
- [ ] Administrator Role
- [ ] Private Data
- [ ] Authorization
- [ ] Action Logging

#### "Late Game" Features:
- [ ] MFA
- [ ] Custom Roles
- [ ] Role Inheritance

#### Target Audience/Environment
The application will demonstrate RBAC in an office environment but the concepts can be applied to restaurants, video games, schools, and other areas with different permission levels.

| Permission | Admin | Developer | User |
|---|---|---|---|
| View public page | Allow | Allow | Allow |
| View staff page | Allow | Allow | Deny |
| Edit resources | Allow | Allow | Deny |
| Create roles | Allow | Deny | Deny |
| Assign user roles | Allow | Deny | Deny |

### Security Concepts Applied

Our project applies the AAA+I model from Module 5 to a locally hosted Java web application. The main concept we will demonstrate is role based access control (RBAC). An admin will use the web interface to create accounts, configure roles by selecting permissions and assign those roles to users.

AAA+I model application:
-	Identification: Each user enters a unique username and password on the login page. The username identifies which account is requesting access.
-	Authentication: The application verifies the username and password. After a successful login, a session identifies the signed in user until the user logs out. Our project will use demo credentials while a production version should be storing passwords using a dedicated password hashing algorithm with a unique salt for each password and use HTTPs to protect credentials in transit for appropriate authentication.
-	Authorization: A role is a set of permissions chosen by the admin. For each protected request, the Java backend checks whether the user’s assigned role allows the requested action on that resource and or when logging in and loading the session some resources and actions may not even be present to request access to. For example, only an admin account can create and assign roles to other users and view and edit public and private resources while a user can only view public resources. If a role lacks permission to an action, the backend denies the request, including when the user opens a protected URL directly.
-	Accounting: We plan to log role assignments, changes to role permissions, actions, requests and denied access attempts. Each entry will record the account, action, time and outcome so admin can review who did what. The log will exclude passwords.

CIA Triad application:
-	Confidentiality: The access controls support confidentiality by restricting who can view what resource.
-	Integrity: The access controls support integrity by restricting who can modify a given resource. 
-	Availability: Preserving accounts, role assignments and resource changes across normal restarts and log outs so that authorized users can resume their work supports availability.
 
Additionally, we will adhere to the least privilege security principle that guides how the admin configures roles. Each role should receive only the permissions needed for its purpose. Creating account, configuring roles and assigning roles will be reserved for the admin. The application will deny protected actions unless the assigned role explicitly allows them. 
	
### Methodology
-	Describe the approach, methods, and tools you will use to design, implement,
-	and evaluate the project.
-	You can structure it like this:
    - System Design Overview:
    The system will use role-based access control to manage user permissions. Each user will be assigned a role, such as admin, developer, or player. Roles will have different levels of access depending on the actions they are allowed to perform. Admins will also have the ability to create new roles and assign permissions to them.
    - Data Collection & Preprocessing:
    The project will use manually created characters and resources rather than external data. Users will be assigned a role with permissions that determine their level of access. Passwords will be hardcoded for the initial implementation.
    - Implementation Details:
    We will be using Java for our project. Classes and methods will manage players, roles, permissions, and resources. The program will check a user's permissions before allowing them to view, edit, or change anything. Admins will also be able to create custom roles and update the permissions for each role. An audit log will record important actions, such as access attempts, resource changes, and role modifications.
    - Evaluation Metrics:
    Our evaluation metrics will focus on testing different roles and their ability to access and view resources. We will check that admins can create new roles and assign permissions, developers can view and edit resources, and players have the appropriate permissions. We will also make sure that important actions are recorded in the audit log. Testing itself will mainly focus on making sure permissions are properly implemented and enforced.
