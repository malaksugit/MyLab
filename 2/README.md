# Windows Server – Group Policy Management & Company Security Standards

## 1. Project Overview

This project demonstrates practical Windows Server administration using Active Directory and Group Policy Management (GPMC).

The lab simulates a company environment with two departments: HR and IT. Group Policy Objects (GPOs) are used to apply company-wide security standards and department-specific restrictions.

The main objective is to centrally manage Windows user settings and enforce security policies across the domain.

## 2. Lab Environment

- **Server:** Windows Server
- **Directory Service:** Active Directory Domain Services (AD DS)
- **Policy Management:** Group Policy Management Console (GPMC)
- **Client:** Domain-joined Windows Client
- **Organizational Units (OUs):**
  - `HR_Dept`
  - `IT_Dept`
- **Departments:** Human Resources (HR) and Information Technology (IT)

## 3. Group Policy Configuration

The project uses separate GPOs to keep company-wide standards independent from HR-specific restrictions.

### 3.1 Company-Wide Security Standards

**GPO Name:** `ComStandars`

**Linked to:** Domain

The following policies were configured:

- **Disable Registry Editor:** Prevents users from accessing Registry Editor.
- **Screen Saver Timeout:** Configured to 600 seconds (10 minutes).
- **Password-Protected Screen Saver:** Requires users to authenticate when returning to the computer.

### 3.2 HR-Specific Restrictions

Three separate GPOs were created for the HR department:

| Policy | Purpose |
|---|---|
| Disable Control Panel | Prevents HR users from accessing Control Panel |
| Disable CMD | Restricts access to Command Prompt |
| Hide Run | Hides the Run command from the Start menu |

These restrictions are intended for the HR department and are kept separate for easier policy management.

### 3.3 Login Banner

A separate GPO was configured to display a login security banner before users sign in.

This demonstrates the use of Windows security policies to display an organizational notice during the logon process.

## 4. Applying Group Policies

After configuring the GPOs, Group Policy was refreshed on the client using:

```cmd
gpupdate /force
```

This command forces the client to refresh its Group Policy settings.

## 5. Screenshots & Evidence

The following screenshots document the configuration and visible results of the lab.

### 5.1 GPO Configuration

![GPO Configuration](Screenshots/01-GPO-Configuration.png)

### 5.2 Registry Editor Disabled

![Registry Editor Disabled](Screenshots/02-Regedit-Disabled.png)

### 5.3 Control Panel Restricted

![Control Panel Blocked](Screenshots/03-Control-Panel-Blocked.png)

### 5.4 Command Prompt Disabled

![CMD Disabled](Screenshots/04-CMD-Disabled.png)

### 5.5 Run Command Hidden

![Run Hidden](Screenshots/05-Run-Disabled.png)

### 5.6 Login Security Banner

![Login Banner](Screenshots/06-Login-Banner.png)

### 5.7 Screen Saver and Lock Settings

![Screen Saver and Lock Settings](Screenshots/07-Lock-Screen.png)

### 5.8 Domain GPO Management

![Domain GPOs](Screenshots/09-Domain-GPOs.png)

## 6. Skills Demonstrated

- Active Directory administration.
- Organizational Unit (OU) management.
- Group Policy Object (GPO) creation and configuration.
- Domain-level and department-specific policy management.
- Windows security policy configuration.
- Centralized administration using Group Policy Management.
- Applying Group Policy updates using `gpupdate /force`.
- Technical documentation and evidence collection.

## 7. Project Outcome

This lab demonstrates how Group Policy can be used to apply centralized security standards across a Windows domain while maintaining separate restrictions for specific departments.

It also highlights the importance of organizing GPOs according to their purpose and scope to simplify administration and future policy changes.
