# CyberSecurity
## Chapter 1
### Definition of Computer Security
> **Computer Security** is a _collection_ of **measures** and **controls** that ensures confidentiality, integrity and availability of information system assets including hardware, software, firmware, and information being processed, stored, and communicated.

- Confidentiality: this term actual aggregate two related concepts:
	- Data Confidentiality => Assures that private or confidential data/information is not made available or disclosed to unauthorized individuals.
	- Privacy => Assures that individuals control or influence what information related to them may be collected and stored and by whom and to whom that information may be disclosed.
- Integrity: also this aggregate two related concepts: 
	- Data Integrity => Assures that information and programs are changed only in a authorized and specified manner.
	- System Integrity => Assures that a system performs its intended function in an unimpaired manner, free from any unauthorized manipulation of said system.
- Availability => Assures that system work promptly and service is not denied to authorized users.
These tree concepts forms what is called the CIA Triad as if those concepts are the fundamental objectives of computer security for data, information and information systems.
_FIPS 199_, which is an organization who defines standards for computer security, defines them as follows:
- Confidentiality
	- **_What it means?_** 
		Preserving authorized restrictions on information access and disclosure, including means for protecting personal privacy and proprietary information.
	- ***What is a loss?***
		Is an unauthorized disclosure of information.
- Integrity
	- **_What it means?_** 
		Guarding against improper information modification or destruction, including ensuring information nonrepudiation and authenticity.
	- ***What is a loss?***
		Is the unauthorized modification and/or destruction of an information.
- Availability
    - **_What it means?_**  
        Ensuring timely and reliable access to and use of information.
    - **_What is a loss?_**  
        Is the disruption of access to or use of an information or an information system.
Also two more concepts need to be introduced: 
- Authenticity
	The property of being genuine and being able to be verified and trusted.
	This means to be sure that a communication, message or transmission is valid and come from an authorized user which says who is he to begin with.
- Accountability
	Which means that actions made by an entity are traced and associated to that specific entity.
	This means that system should trace and log each actions to permit to identify security breaches and trace which entity made that action.
	This concepts supports nonrepudiation, deterrence, fault isolation, intrusion detection and prevention and after-action recovery and legal support.
#### Loss Rating
A loss in any of the objective listed above has a rating based on the service itself:
- **Low** => the following loss could cause some annoyance to the users of said service and could cause little to no harm to the organization business, operation, assets and/or individuals.
- **Moderate** => those type of losses could be expected to have a serious adverse effect on the organization business, operation, assets and/or individuals.
  1. The organization primary operation can still be continued although a severe disturbance/slowness can be felt.
  2. A significant damage can be done to the organization assets.
  3. Significant financial loss.
  4. Significant harm to the individuals (NOT life threatening)
- **High** => those losses could be expected to have a severe and/or catastrophic adverse effect on the organization.
### Terminology
![[Screenshot 2026-06-10 alle 21.58.49.png]]
![[Screenshot 2026-06-10 alle 22.14.01.png]]
System Resource / Asset: 
The asset of a computer system can be categorized as follows:
- Hardware => computer system, data storage, data communication and data processing devices.
- Software => OS, applications and utilities of a computer system.
- Data => files, databases and security related data such as password files.
- Communication Facilities and Networks => LAN and WAN links, bridges, routers exc...

> Our concern about the system resources are their **vulnerabilities**, such as:
- Corruption, a system in this state does the wrong things or gives the wrong answers.
- Leaky, a leaky system is a system where an unauthorized user access some or all information which are not his.
- Unavailability or Slowness, a state in which the system or network become impractical or impossible to use.

In other words:
> Corresponding to the various types of vulnerabilities to a system resource are ***threats*** that are capable of exploiting those vulnerabilities.
> A threat represents a potential security harm to an asset.
> An ***attack*** is a threat that is carried out (threat action) and, if successful, leads to an undesirable violation of security, or threat consequence.
> The agent carrying out the attack is referred to as an attacker or ***threat agent***.

> Finally, a countermeasure is any means taken to deal with a security attack.
> Ideally, a countermeasure can be devised to prevent a particular type of attack from succeeding. 
> When prevention is not possible, or fails in some instance, the goal is to detect the attack then recover from the effects of the attack. 
> A countermeasure may itself introduce new vulnerabilities. 
> In any case, residual vulnerabilities may remain after the imposition of countermeasures. 
> Such vulnerabilities may be exploited by threat agents representing a residual level of risk to the assets. 
> Owners will seek to minimize that risk given other constraints.

#### Attack Classification
![[Screenshot 2026-06-10 alle 22.23.49.png]]

### Threads and Attacks
![[Pasted image 20260611152416.png]]
- Interception => this type of attack refers to the networks so that any devices in a LAN ()