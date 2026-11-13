# Project Design Document – CS 331
## Project Title: 
## Team Member(s): Jay Berry, Austin Mahon, Caden Anderson
### Objective (Purpose of the Project)
- Clearly state what the project aims to achieve.
- Simulate RBAC by authenticating user log in 
- Mention why this project is important or relevant to this course.	
- Example points to include:
    - The problem or gap the project addresses.
    - The main goals and expected outcomes.
    - How the project contributes to research or practice.
### Scope
- Define the boundaries of the project: what is included and excluded.
- Is this hosted, or ran locally? Is this with real data? Is this end to end? Is there a UI?
    - Local
    - Simulated Data
    - Basic login page
        - Admin account can access all pages + add pages
        - can access all pages
        - only public pages
        - Custom role? 
    - Log.txt to track access
- Describe the target audience, systems, or environments involved.
    - Office
    - Restaurant
    - Anyone with diff access employees
- Mention any assumptions or limitations.
### Security Concepts Applied
-	Describe the core security principles and concepts applied in the
-	project. You can include, but are not limited to, concepts such as:
-	Confidentiality, Integrity, Availability (CIA)
-	Authentication and Authorization
-	Least Privilege, Open Design, etc.
    - RBAC
    - jay.admin
    - john.dev
	
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