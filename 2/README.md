# Windows Server – Group Policy Management & Security Policies

## 1. Project Overview

This project demonstrates practical Windows Server administration using Active Directory and Group Policy Management (GPMC).

The lab simulates a company environment with two departments (HR and IT), where Group Policy Objects (GPOs) are used to enforce centralized security standards and department-specific restrictions.

The main objective is to manage Windows user settings, restrict access to selected administrative tools, and improve workstation security through centralized Group Policy management.

## 2. Lab Environment

- Operating System: Windows Server
- Server Role: Active Directory Domain Services (AD DS)
- Management Tool: Group Policy Management Console (GPMC)
- Client: Windows Client joined to the domain
- Domain Structure: Active Directory Domain
- Organizational Units (OUs):
  - HR_Dept
  - IT_Dept

## 3. Project Objectives

- Create and manage Group Policy Objects (GPOs).
- Apply company-wide security standards.
- Configure department-specific restrictions.
- Restrict access to selected Windows tools.
- Configure screen saver security settings.
- Configure a login security banner.
- Apply Group Policy updates across the domain.

## 4. Group Policy Configuration

### 4.1 Company-Wide Security Standards

GPO Name: ComStandars

Scope: Domain

The following policies were configured:

- Disable Registry Editor (Regedit).
- Configure Screen Saver Timeout to 600 seconds (10 minutes).
- Require a password when returning to the computer.

**Screenshots:**
- 01-GPO-Configuration.png
- 02-Regedit-Disabled.png

### 4.2 HR Department Restrictions

Three separate GPOs were configured for the HR department.

#### Disable Control Panel

Prevents HR users from accessing Control Panel.

**Screenshot:**
- 03-Control-Panel-Blocked.png

#### Disable Command Prompt (CMD)

Restricts HR users from accessing Command Prompt.

**Screenshot:**
- 04-CMD-Disabled.png

#### Hide Run

Hides the Run command from the Start menu.

**Screenshot:**
- 05-Run-Disabled.png

### 4.3 Login Security Banner

A separate GPO was configured to display a security message before users sign in.

**Screenshot:**
- 06-Login-Banner.png

## 5. Screen Saver Security Configuration

The screen saver timeout was configured to 600 seconds (10 minutes), with password protection enabled.

This configuration helps protect company computers when users leave their workstations unattended.

**Screenshot:**
- 07-Lock-Screen.png

## 6. Group Policy Deployment

Group Policy was refreshed on the client computer using:

`gpupdate /force`

This command forces the client to refresh its Group Policy settings.

## 7. Domain GPO Management

Group Policy Management Console was used to manage the configured GPOs and review their links within the domain and Organizational Units.

**Screenshot:**
- 09-Domain-GPOs.png

## 8. Skills Demonstrated

- Active Directory Administration
- Group Policy Management (GPMC)
- GPO Creation and Configuration
- Domain-Level Policy Management
- Department-Specific Security Restrictions
- Windows Security Configuration
- Screen Saver and Workstation Security
- Centralized IT Administration

## 9. Conclusion

This project demonstrates how Group Policy Management can be used to enforce centralized security standards and department-specific restrictions within an Active Directory domain.

It also demonstrates practical Windows Server administration, policy organization, and centralized security management in a simulated corporate environment.
