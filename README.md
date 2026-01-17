# Staff Management – Power Platform Solution

Staff Management is a Power Platform solution for managing staff profiles, jobs, and rosters. It leverages Dataverse for structured data storage, Canvas App for user interface, and Power Automate Cloud Flows for automations.

This solution allows users to manage profiles, assign roles, and roster staff efficiently within an organization.

## Project Overview

Staff Management allows users to:

- Create and update staff profiles
- View all staff profiles via dashboard
- Assign staff to jobs and manage rosters
- Manage roles and job tables for administrators
- Automate test setup (auto-add logged-in users, assign superuser role, populate jobs table)
- Enforce role-based access for Basic Users, Admins, and Superusers

## Tech Stack

- **Power Apps** – Canvas App for user interface
- **Dataverse** – Stores staff, jobs, roster, and roles data
- **Power Automate** – Cloud Flow automation for test data initialization
- **Security Group** – Provides access to Dataverse tables for users based on roles


## Components

### Dataverse Tables

| Table | Purpose |
|-------|---------|
| User | System users information |
| Staff | Personal details, education, location, software expertise, remote work availability |
| Jobs | List of job titles and roles |
| RosterMembership | Tracks staff added to rosters and assigned jobs |
| RoleManagement | Manages user roles and permissions |

### Canvas App Modules

- **Profile Update** – Staff can update their personal profiles
- **Dashboard** – View all staff profiles
- **RosterMembership** – View rostered staff and assign jobs
- **Settings** – Update jobs table and role management

### Automations

- Auto-add logged-in user to Staff table
- Auto-assign superuser role to logged-in user for test purposes
- Auto-populate Jobs table with test entries if empty

### Security Group
- **StaffManagementDataAccess** – Controls user access to all Dataverse tables in the solution

## Installation / Setup

### 1. Export / Import the Solution

1. Export the **StaffManagement** solution from this GitHub repository.
2. Go to **Power Apps** → **Solutions** → **Import**
3. Upload the exported `StaffManagement.zip` solution


### 2. Configure Dataverse Tables 

- Ensure tables (User, Staff, Jobs, RosterMembership, RoleManagement) are present
- Check if the Cloud Flow `SM_InitializeJobsTableIfEmpty` exists


### 4. Assign App Access

- Share the StaffManagement Canvas App with any users who need access
- During the sharing process, ensure the users are also granted access to all underlying Dataverse tables via the StaffManagementDataAccess security group.
- This ensures users can fully interact with the app and its data according to their role.

### 5. Run the App

Navigate through modules:
- **Home** → Welcomes the user and shows Profile Completion %
- **Profile Update** → Update personal info
- **Dashboard** → View all staff
- **RosterMembership** → View all rostered users and manage rostered profiles. Roster staff profiles as needed.
- **Settings** → Manage jobs and roles

## Testing Credentials

- Any logged-in user is automatically added to the Staff table
- The same user is assigned superuser role for testing
- Three job records are automatically added to the Jobs table if it is empty.
- Use any Microsoft 365 account in your environment to log in

## Repository Structure

```
/staff-management-solution
├── StaffManagement_1_0_0_1_managed.zip
│ 
└── README.md
│   
└── StaffManagementScreenshots
```

## Features

- Full CRUD operations for Staff and RosterMembership
- Lookup relationships: Staff → RosterMembership → Jobs
- Clean Canvas App interface with dashboards and forms
- Automations simplify testing: auto-add staff, auto-assign superuser, auto-populate jobs
- Modular design for future HR workflow extensions