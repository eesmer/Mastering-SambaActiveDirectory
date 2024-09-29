## Table of Contents
- [Preface](#Preface)
- [Acknowledgements](#Acknowledgements)
- [Document Structure and Usage](#Document-Structure-and-Usage)
- [1- Introduction](#Introduction)
- [Chapter-1: What is Active Directory?](#What-is-Active-Directory?)
- [Chapter-2: Active Directory Concepts](#Active-Directory-Concepts)
  
---

## Preface
SambaAD, which is installed with the Samba software package, is an open-source software developed to provide Microsoft Active Directory services and is distributed under the GPLv3 license. <br>
SambaAD allows for the setup and management of a Domain and Active Directory environment. <br>
<br>
The Samba software project, which began development in 1991 with the aim of enabling Windows and UNIX/Linux environments to work together; <br>
- First achieved compatibility with LAN Manager and Workgroup environments through Samba 1. <br>
- With Samba 2, it provided NT4-Style Domain Controller services for Windows clients. <br>
- Samba 3 introduced file and printer sharing management and FileServer services. <br>
<br>
Finally, Samba 4 provided the setup and management services for a Domain and Active Directory environment. <br>
<br>
Named after the file and printer sharing protocol SMB, Samba has become a great tool for us thanks to the outstanding work of Andrew Triggel and the Samba Team. <br>
And today, we have an excellent option for setting up and managing Domain and Active Directory environments in production environments. <br>

#### On Paradigm Shift
I'm not sure the paradigm example is the best fit for this work. <br>
<br>
If we define paradigm as the accepted way of doing things in a particular field, then Samba software is a great example of a paradigm shifter because it offers an alternative solution. <br>
Historically, paradigm shifts have been a way to bring about positive change. But sometimes, sticking too closely to the current model can get in the way of  new ideas. <br>
<br>
Regardless of whether this topic is the perfect example of a paradigm shift or if it's causing what's known as "paradigm paralysis," which makes it harder to learn and grow, we can still evaluate this work by focusing on the potential of open-source alternatives in the IT world today. <br>
<br>
Then, we can get started.

#### Acknowledgements
It's impossible not to acknowledge the efforts behind this work. <br>
Special thanks to the Samba project team and Andrew Triggel for their incredible contributions. <br>
Samba4 is a remarkable achievement. <br>
<br>
My goal with this work is to offer guidance and consistent study notes to Samba users and to those who are interested in learning and using Samba. <br>

#### Document Structure and Usage
This work will be kept electronically in this repository. <br>
It is available in Turkish, English and PDF format. <br>
<br>

The study will be updated here. <br>

**Update:** September 28, 2024

---

<br>

## 1- Introduction
In this section we will basically talk about Active Directory and its concepts. <br>
With this section we will have detailed information about AD and AD environment. <br>
<br>

## Chapter-1: What is Active Directory?
Active Directory is a directory service for network users. <br>
It stores information about the organisation, such as users, computers, printers, etc. Administrative restrictions can be created on all components and rules can be executed as required. <br>
<br>
When a user logs on to a computer in a domain environment, Active Directory checks the username and password entered. <br>
If the login is valid, AD policies authorise it and the user can access network resources. <br>
<br>
Active Directory was first released with Windows 2000 Server. It was developed with lots of changes in the Windows 2003 version. With the improvements in Windows 2008 and later versions, it took on its current capabilities. As a result, all identity-related work was collected and managed under AD. <br>
<br>
[wikipedia.org/Active Directory](https://en.wikipedia.org/wiki/Active_Directory)
<br>

<br>
![alt text](images/AD_BasicSchema1.jpg "Active Directory Basic Schema")
![alt text](images/kerberos.gif "Kerberos Service")
<br>

![alt text](images/AD_BasicSchema1.jpg "DebianDC_Desktop")

<br>

![alt text](images/kerberos.gif "DebianDC StartMenu")

## Chapter-2: Active Directory Concepts
If you want to get to grips with the overall structure of an Active Directory (AD) or Samba AD environment, it's really important to understand the basic concepts. <br>

- ### Forest
In Active Directory, a forest is the top-level logical structure. <br>
A forest can have more than one domain, and they're all connected to each other with a trust relationship. All the domain environments in the forest use the same Global Catalog and Schema.

- ### Schema
This defines the object types and their properties that are shared at the forest level and used in all domain environments.

- ### Global Catalog
This contains a copy of all domain environment objects in the forest and provides quick access when searched.

- ### Site
In an Active Directory environment, a site is basically a physical network structure. <br>
Usually, you'll find that networks in different geographical locations are defined as a site. <br>
**Site Link:** It's the tool you use to set up connections for replication traffic between each site.

- ### Domain
Before we get into the domain environment, it's important to understand the workgroup environment, which is made up of smaller computer groups. <br>
A workgroup is a network of computers that are all connected to the same network. They can share files and printers and use each other's resources. <br>
<br>
However, there is no central policy for workgroup computers, so each computer decides for itself which resources it can access. <br>
<br>
A domain environment is a way of central controlling who can connect to what and similar policies in computer environments that are bigger than just a workgroup. <br>
<br>
[wikipedia.org/Workgroup](https://en.wikipedia.org/wiki/Workgroup_(computer_networking)) <br>
[wikipedia.org/WindowsDomain](https://en.wikipedia.org/wiki/Windows_domain) <br>

- ### Domain Controller
The Domain Controller is the computer where the domain environment is installed. <br>
It also hosts the Active Directory database, which is used to manage users, computers, groups and other resources in the domain environment. <br>
<br>
The Domain Controller basically performs the following tasks; <br>
    • Authentication <br>
    • Authorization <br>
    • Replication <br>
    • FSMO Roles <br>
    • Group Policy Management <br>
  
- ### Domain Join
Domain Join is the process of adding a computer or device to the Active Directory (AD) domain environment. <br>
The idea of joining is usually used to express membership. Put simply, it's a concept used in the process of making a new component a member of the domain environment. <br>
<br>
In order to talk about a domain environment in an organisation, there must be at least one Domain Controller computer in the environment. <br>
Computers other than the Domain Controller in the organisation join the domain environment run by the Domain Controller. <br>
Thus, they are subject to the security rules and policies operated by the Domain Controller. <br>
<br>
For example, let there be a file server and shares in the domain environment. <br>
The access request of a domain member computer that wants to access these shares is asked to the Domain Controller computer by the file server and the request is answered according to the response of the Domain Controller computer. <br>

The Domain Controller computer manages the join process and the policies of the joined computer to access resources and work in the domain environment. <br>

- ### Domain Member
It refers to a machine that has joined (joined) a domain environment. <br>

- ### Domain Users Account
The account defined in AD for a user that provides access to network resources. <br>
Each user account contains specific permissions and authentication information. <br>
<br>
User accounts authenticate and log in from member devices according to domain policies and receive access authorisations to resources. <br>

- ### Domain Groups and Organisation OU (OU)
In a domain environment, these objects are used to organise resources. <br>
It pertains to the areas where user accounts and computers are members and can be relocated. <br>
OU objects are utilised for administrative purposes, with the ability to assign different policies and permissions to each OU. <br>

- ### Group Policy Object (GPO)
It is a tool used to implement policies on computers and users within the domain. <br>
GPO enables the central application of user settings, security policies and similar administrative tasks to the domain environment. <br>

- ### FSMO roles (Flexible Single Master Operations roles)
These are the roles that have been assigned the task of managing specific processes at a central level within Active Directory. <br>
There are five basic FSMO roles; Schema Master, Domain Naming Master, RID Master, PDC Emulator and Infrastructure Master. <br>
<br>
These roles are run by Domain Controllers at the Forest and Domain levels. <br>

- ### Trust
It means that one Domain environment trusts another Domain environment. Through trust relationships, the resources of one Domain environment can be accessed by users in the other Domain environment. <br>
These trust relationships can be unidirectional or bidirectional and are usually established between Domain environments within the Forest. <br>

- ### Login
Login is the authentication process of a user account. <br>
The user allows the system to recognise him/her by entering UserName and Password credentials. The process of checking and recognising the information entered by the system is done from Domain Controller computers. <br>
    • The user provides credentials. <br>
    • The information entered is checked by the Domain Controller. <br>
    • If the credentials provided are correct, authentication is performed and the logon process starts. <br>

- ### Logon
It is the login process of a user account after the authentication process. <br>
In this process, an Access Token consisting of information such as the identity and group of the user account is created while opening a session of the user. <br>
The user session is opened and authorisation and access from policies such as profile settings, network connections are completed. <br>
<br>
**Login** determines who the user account is, it does not start a session. <br>
**Logon** starts a session for the user account after login. <br>
<br>
        ◦ **Security ID (SID)** <br>
An information (username, computer) created in the domain environment SID is a unique identifier created for each user, group and computer object in the domain environment to be used in security and access controls. <br>
        ◦ **Access Token** <br>
A list of credentials and permissions assigned to a user account or a login process. This determines how and which resources a user can access the environment. <br>
        ◦ **Kerberos Ticket** <br>
        ◦ **Access Control List (ACL)** <br>
Access Control List is a list that holds who can access a resource such as a file, directory, network share and at what level.<br>
<br>
Logon process; <br>
    • Authentication is successfully completed (login) <br>
    • Kerberos Ticket and Access Token are created <br>
    • Access Control List is created <br>

- ### Kerberos Protocol and Kerberos Tickets
The Kerberos protocol is the predefined protocol for authentication in the Active Directory environment. <br>
It provides secure authentication of users and services as a centralised component. <br>
<br>
The Kerberos protocol provides the following functions; <br>
    • Authentication <br>
    •  Single Sign-On <br>
    •  Authorization <br>

- ### Kerberos Tickets
Once the user has authenticated, the user is issued a Ticket Granting Ticket (TGT). <br>
With this TGT, Service Ticket is provided for access to different services. <br>
<br>
Thus, there is no need to authenticate repeatedly while accessing different services and applications in the same session. Kerberos Tickets are used for this. <br>
Kerberos Tickets contain encrypted keys that prove the user's identity and session. <br>
<br>
Kerberos Tickets are time limited in validity. <br>
<br>
**TGT Duration:** The default validity period of the TGT ticket issued to the user upon logon is 10 hours. <br>
**Ticket Renewal:** Kerberos Tickets can be renewed. The renewal period is 7 days by default. <br>
The renewal validity period is used to renew the TGT when it expires without re-authentication. <br>
<br>
![alt text](images/kerberos.gif "Kerberos Service")
<br>
[from markwilson.co.uk](https://www.markwilson.co.uk/blog/2005/06/kerberos-authentication-explained.htm)
<br>
<br>
The default duration of a Kerberos ticket is 10 hours, and the maximum time the ticket is renewable is 7 days. <br>
If the ticket expires during the session, the Kerberos client automatically requests the KDC to renew the ticket and the session continues with a renewed ticket without interruption. <br>
If the maximum renewable period also expires, the user is asked to re-authenticate. <br>

- ### DNS
Active Directory includes its own DNS server, which manages the SRV records and other DNS entries required for AD to function. <br>
Typically, the DNS role is added to the Domain Controller (DC) when the domain is being set up. <br>
Active Directory uses dynamic DNS updates to automatically update the IP addresses of Domain Controllers and other services. <br>
<br>
Additionally, it manages DNS Zone records, which contain domain names and IP addresses. <br>

- ### Functional Level
A Functional Level refers to a specific version and set of features within an Active Directory environment. <br>
It determines the features available across the domain and which version supports them. <br>

- ### Domain Functional Level (DFL)
This refers to the specific functional level for each domain. It defines what features are supported by the Domain Controllers and other services within that domain. <br>

- ### Forest Functional Level (FFL)
This refers to the functional level across the entire forest. It sets the common features and functions shared by all domains within the forest. <br>
