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
## Chapter-2: Active Directory Concepts
If you want to get to grips with the overall structure of an Active Directory (AD) or Samba AD environment, it's really important to understand the basic concepts. <br>

### Forest
In Active Directory, a forest is the top-level logical structure. <br>
A forest can have more than one domain, and they're all connected to each other with a trust relationship. All the domain environments in the forest use the same Global Catalog and Schema.

### Schema
This defines the object types and their properties that are shared at the forest level and used in all domain environments.

### Global Catalog
This contains a copy of all domain environment objects in the forest and provides quick access when searched.

### Site
In an Active Directory environment, a site is basically a physical network structure. <br>
Usually, you'll find that networks in different geographical locations are defined as a site. <br>
**Site Link:** It's the tool you use to set up connections for replication traffic between each site.
