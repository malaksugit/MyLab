# Windows Server – File Server & Access Permissions Management

## 1. Project Overview

This project demonstrates practical Windows Server administration through Active Directory user and group management, departmental file sharing, and access permissions configuration.

The project simulates a company environment with two departments (HR and IT), where each department has access to its own shared resources while unauthorized access to other departmental files is restricted.

## 2. Lab Environment

| Component | Description |
|---|---|
| Server | Windows Server |
| Directory Service | Active Directory Domain Services (AD DS) |
| Management Tool | Active Directory Users and Computers (ADUC) |
| File System | NTFS |
| File Sharing | Windows Shared Folders |
| Command-Line Tool | Command Prompt (CMD) |
| Environment | Virtual Lab |

## 3. Project Objectives

- Organize departments using Active Directory Organizational Units (OUs).
- Create and manage domain user accounts.
- Create security groups for departmental access management.
- Configure departmental folders on Windows Server.
- Apply NTFS security permissions.
- Configure Shared Folder permissions.
- Test authorized and unauthorized access.
- Troubleshoot file and folder permission issues.

## 4. Active Directory Structure

Created two Organizational Units (OUs) to organize departmental users and resources:

- HR_Dept
- IT_Dept

### User Accounts

| Department | Username |
|---|---|
| HR | hr.user |
| IT | it.user |

### Security Groups

| Group | Department |
|---|---|
| HR_Staff | Human Resources |
| IT_Staff | Information Technology |

Each user was assigned to the corresponding departmental security group.

## 5. Folder Structure

Created departmental folders on the Windows Server:

```text
C:\ITLab
│
├── HR
│   └── Employees.txt
│
└── IT
    └── Technical.txt
```

Each department has a dedicated folder for storing its files.

## 6. NTFS Permissions Configuration

Configured NTFS permissions through:

**Folder Properties → Security → Advanced**

### HR Folder

| Group | Permission |
|---|---|
| HR_Staff | Modify |
| Administrators | Full Control |
| SYSTEM | Full Control |

### IT Folder

| Group | Permission |
|---|---|
| IT_Staff | Modify |
| Administrators | Full Control |
| SYSTEM | Full Control |

These permissions ensure that users can modify files within their assigned departmental folders while preventing unauthorized access to other departments' resources.

## 7. Shared Folder Configuration

Configured network sharing for both departmental folders using:

**Properties → Sharing → Advanced Sharing**

Shared folders:

- HR
- IT

Configured Share Permissions to work together with NTFS permissions.

The effective network access is determined by both Share and NTFS permissions, with the more restrictive permissions taking precedence.

### Network Paths

```text
\\SERVERNAME\HR
\\SERVERNAME\IT
```

*SERVERNAME represents the actual Windows Server hostname.*

## 8. Access Control Testing

Tested access using the individual domain user accounts.

### HR User Testing

Logged in using `hr.user` and performed the following tests:

```cmd
whoami
dir \\SERVERNAME\HR
dir \\SERVERNAME\IT
```

Expected results:

- Successful access to the HR shared folder.
- Access denied when attempting to access the IT shared folder.

### IT User Testing

Logged in using `it.user` and performed the following tests:

```cmd
whoami
dir \\SERVERNAME\IT
dir \\SERVERNAME\HR
```

Expected results:

- Successful access to the IT shared folder.
- Access denied when attempting to access the HR shared folder.

### File Creation Testing

Tested file creation within the authorized departmental folders:

```cmd
echo Test > \\SERVERNAME\HR\test.txt
```

```cmd
echo Test > \\SERVERNAME\IT\test.txt
```

Verified that users could create files only within their authorized departmental folders.

## 9. Troubleshooting

Performed basic permission troubleshooting during the lab, including:

- Investigating insufficient permission errors.
- Checking user and group membership.
- Reviewing NTFS permissions.
- Reviewing Share permissions.
- Verifying access using individual user accounts.

## 10. Skills Demonstrated

- Windows Server Administration
- Active Directory Domain Services (AD DS)
- Organizational Unit (OU) Management
- User and Security Group Management
- NTFS Permissions
- Shared Folder Management
- File Server Administration
- Access Control and Authorization
- Command-Line Administration
- Basic IT Troubleshooting

## 11. Screenshots

The following screenshots document the implementation and testing process.

| Screenshot | Description |
|---|---|
| 01-AD-Organizational-Units.png | Active Directory OU structure |
| 02-AD-Users-and-Groups.png | User accounts and security groups |
| 03-Server-Folder-Structure.png | Departmental folder structure |
| 04-HR-NTFS-Permissions.png | HR folder NTFS permissions |
| 05-IT-NTFS-Permissions.png | IT folder NTFS permissions |
| 06-Share-Permissions.png | Shared folder permissions |
| 07-HR-Access-Test.png | HR authorized access test |
| 08-HR-Access-Denied.png | HR unauthorized access test |
| 09-IT-Access-Test.png | IT authorized access test |

## 12. Conclusion

Successfully implemented a centralized departmental file management environment using Windows Server and Active Directory.

The lab demonstrated how to organize users through Organizational Units, manage access through security groups, configure NTFS and Share permissions, and verify access restrictions through practical testing.

This project provided hands-on experience with fundamental Windows Server administration and file access management tasks commonly performed in IT Support and Junior System Administrator roles.

---

**Project Type:** Practical IT Administration Lab

**Focus:** Windows Server, Active Directory, File Server and Access Permissions
