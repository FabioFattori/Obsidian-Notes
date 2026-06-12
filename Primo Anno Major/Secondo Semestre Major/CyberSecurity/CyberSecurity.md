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
- Interception => this type of attack refers to the networks so that any devices in a LAN (example) can receive a copy of a packet that needs to reach a determinate destination.
- Inference => an unauthorized entity can understand and there for come to knowing some confidential information by utilizing a database with limited access or by looking at the network traffic.
- Incapacitation => [Availability Attack] the entire system can be incapacitated, not only a component/service of it.
- Corruption => [System Integrity Attack] 
- Misappropriation => DoS attacks falls in to this topic cause the attack it selfs overflows the network there for the CPU of the asset.
- Misuse => Attacks which need another successfull attack before, such as gaining authorized login data or a back door to the asset, a Misuse attack consists in having the access to a asset and disabling all or some of their security functions.
### Assets Categories/Components Attacks
![[Pasted image 20260611161803.png]]
#### Hardware
The biggest thread to this category is Availability as the hardware is the most vulnerable to attacks and the least component protected from automated controls.
Other threats are involuntary or deliberate damage to it, as well as theft, those harmful threads can lead to losses of confidentiality and availability.
Physical and administrative protections and protocols need to be implemented limit the losses.
#### Software
Viruses and malware are also a thread to the software whose can deny the service to the user (availability) or alter the functions and/or services of it (integrity/authenticity).
A more severe problem which has no definitive solution now days is the protection to piracy, which means that a software is copied and used without the consent of it's makers, this thread can also lead to other thread like integrity (example: the pirate software is impersonating the legitimate software to access unauthorized information and data).
#### Data
For underlying data we means confidential and private data which can be retrieved or calculated from statistics databases or displayed information.
This problem is exacerbated by the increasing desire to combine data sets.
In many cases, matching several sets of data for consistency at different levels of aggregation requires access to individual units. 
Thus, the individual units, which are the subject of privacy concerns, are available at various stages in the processing of data sets.
#### Communication Lines and Networks
Two types of attacks:
- Passive 
	Those types are made for understanding, analyze and extract data from a network or line.
	Typically the objective of those attacks are:
	- Get the content of the message transmitted
	- Analyze the traffic
		  This is done when the message are encrypted thus the content is unavailable, so the opposer try to deduct the nature of the communication and maybe understand what the two hosts are saying by observing the ***length of messages*** and ***who*** is transmitting them.
	> These types of attacks are **difficult to detect** only ***based on their nature***, the asset, the information system **is not harmed or modified in any way**; even messages are not touched, making it almost impossible to the sender or the receiver to know if said message has been read by others.
	> So the emphasis here is to ***prevent*** instead of cure the problem.
- Active
	These involves into the alteration of the data stream or the creation of a false data stream (message).
	- Replay 
		  Consists of a capture of data unit (ex: message) and the following retransmission of it to obtain an unauthorized behavior/effect (ex: login into an account or logout of a user from his account).
	- Masquerade
		Takes place when an entity pretends to be another entity.
		An example can be the man in the middle attack, even tho the MITM is a much more complex and elaborate attack.
		This form of attacks usually includes one or more other forms of attacks, cause this one alone doesn't do much except create a loss of confidentiality and authenticity.
	- Modification of messages 
		Loss of data integrity.
	- Denial of Service
		This attack can have a ***specific target***, so that the victim cannot be reached by other nodes in the network, or can have an ***entire network***.
	> Active attacks are quite the opposite from Passive attacks when it comes to handling them.
	> Passive cannot be detected but there are many ways to prevent them, Active attacks cannot be prevented absolutely  but can me detected there for resolved, which act as a form of deterrent so it ALSO function as prevention.

### Fundamental Security Design Principal
- Economy of mechanism
	This principal consists in demanding that the design of the security mechanisms of software and hardware is as simple as possible to enhance change/fixing time to the mechanism itself.
	Also a complex mechanism is more likely to have security flaws and therefor to have exploitable parts that a hacker can utilize.
- Fail-safe defaults
	Means that access decision should be handled by permission rather than exclusion.
	This is made so that if a function in the system has a error in it a permission system tend to fail rather than consent the access to that functionality. (for example the token system of sanctum is handed precisely like that)
- Complete mediation
	Means that if an access action must be made, the permission of the user ***MUST*** be checked directly by the access control and not by a local cache.
	***Example*** a user logs in and can see his files, some of them he can only read and some of them he can edit, once he tries to open one a request to the access control must be made to verify his permission towards that file in order to find if he can read it or can also edit it.
- Open design
	Means that the algorithms and security mechanism should be open source rather than secret, so that experts and user can see them and familiarize with them.
	Keys and password should be secret but not the way that these variables are handled.
- Separation of privileges
	This principal means that a service should have the privileges in order to execute ***his and only his tasks***, it shouldn't have other privileges.
	This protects our system in way that if an attack occurs to that specific service, only it tasks are harmed (it his actually a mitigation of the potential damage that the attack actually does).
- Least privilege
	This principal his connected to the Separation of privileges, this one refers to the users of the system saying:
	> A user should have the least set of privileges to operate/execute his task.
	
	There is also a temporary aspect to this principal:
	A administrator or a user with higher privileges should have a longer set of privileges in specific times to execute sporadic tasks, once those tasks are finished and therefor some privileges are not needed anymore they should be revoked from the user as them being there are a possible security flaw.  
- Least common mechanism 
	Means that design should minimize shared functions (software and hardware) between users.
	This approach enhance mutual security and permits an easier check on undesirable security implications, making also less users depend on common software/hardware.
- Psychological acceptability
	This Principal implies that security mechanism and protocols should not be interfering with the users workflow.
	The mechanism should be transparent or at best a little obscuring to the user, if these is not respected the user may be tempted to turn off the protection.
	So the mechanism should be:
	> Transparent and not burdensome, and also it should reflect the mental model of protection that the user has so it enhance the work of the user, making him do less errors.
- Isolation
	This principal refer to 3 separate parts:
	- public and critical systems
		  Those two ***should*** be separate and isolated from each other to prevent information disclosure or tampering.
		  Also if the information have an high sensitivity or criticality those systems can be isolated physically and/or logically:
		  ***Physical isolation*** may include and ensure that there are no connections between public information and critical information.
		  ***Logical Isolation*** imply that there are some layers of security services between the public system and the critical one, so that the two are isolated.
	- Processes and files of users should be isolated from other file and processes of other users
		  Now days the OS do this automatically, separating them in memory.
	- Security mechanism should be isolated so that the access to them is prevented
		  Example => in the access control service the cryptographic software (sub-service) is isolated from the rest of the access control service so that the keys are not disclosed and/or tampered. 
- Encapsulation
	can be viewed as a specific form of isolation based on object-oriented functionality. Protection is provided by encapsulating a collection of procedures and data objects in a domain of its own so that the internal structure of a data object is accessible only to the procedures of the protected subsystem and the procedures may be called only at designated domain entry points.
- Modularity
	Refers to the development of the security functions and to the use of a modular architecture for the security mechanism.
	In these way upgrading/changing some modules doesn't required to change ALL the mechanism but just a module of it, making the mechanism itself much more upgradable and expandable in the development time.  
- Layering (_defense in depth_)
	Refers to the use of multiple, overlapping procedures and mechanism of defense to access resources and assets, so that if an attacker breach one of the mechanism the entire system is not left unprotected.
- Least astonishment
	Means that a program/user interface should responds and behave in a way that the user is less astonished as possible from the security mechanism that is acting underneath of it.
### Attack Surfaces and Attack Trees
#### Attack Surfaces
> List of the reachable and exploitable vulnerabilities of a system, so it's the points breachable by the attackers.

Examples:
![[Pasted image 20260611220904.png]]
Attack surface categories are:
- Network attack surfaces
	In this category there are vulnerabilities found in the network(WAN,LAN or/and the Internet) such as protocols vulnerabilities.
- Software attack surfaces
	Vulnerabilities in softwares, applications and utilities.
- Human attack surfaces
	Vulnerabilities created by insiders and outsiders.
> Making an attack surface analysis means analyzing where and which vulnerabilities are present in the system.
> Finding them is important for the developers and the analysts to reduce the attack surface by implementing security mechanisms making the attackers job more difficult.
> Also this analysis is useful to prioritize testing and streghteting in specific areas of the system.

![[Pasted image 20260611222014.png]]
The use of layering, or defense in depth, and attack surface reduction complement each other in mitigating security risk.
#### Attack Trees
An attack tree is a data structure that represents and collect a series of potential techniques for exploiting vulnerabilities of a system.
It's represented as a tree so it's composed of nodes and leaf which have different meaning:
- Root Node: the security incident which is the goal of the attackers (like have access to an account)
- Branches and subnotes: ways by which the attacker can reach his goal.
  Each subnode define a subgoal that the attacker needs to achieve to be able to attempt to reach the primary goal.
	 Each subnote that is not a leaf is either a:
	- AND-node => each node(goal) of the branch must be achieved/completed to be able to go to the following sets of nodes
	- OR-node => at least one node must be achieved
	Also branches can be labeled to give some additional infos of the 'path' represented by the branch such as cost or difficulty.
- Leafs: the end nodes, whose represent the many ways an attacker can initiate the attack, the are like paths for the attacker to follow to reach his goal.

> Attack trees are made by analyst to document attack patterns and highlight key vulnerabilities of systems.
> Also these trees can lead both the design of systems and applications, and the choice and strength of countermeasures.
> Standard organizations such as CERT provide some common trees to create a basic knowledge on attack patterns.

#### Example
![[Pasted image 20260612003614.png]]
![[Pasted image 20260612003719.png]]
> with these knowledge the analysts can know assess the risks of each attack and by using the principals listed before [[#Fundamental Security Design Principal]] they can plan some strategies to lower the risks of the attacks.

### Computer Security Strategy
A comprehensive security strategy involves three aspects:
- Specification/policy => what is the security scheme supposed to do?
- Implementation/mechanism => how it does it?
- Correctness/assurance => does it do it correctly?
#### Security Policy
The development of a security policy is the first step in devising and engineering security services and mechanisms.
It may have various definition such as:
> at the least, a security policy is an informational description of desired system behavior.
> In that description could be referenced minimum requirements for availability, integrity and confidentiality.

or 
> a security policy is a formal statement of rules and practices that specify or regulate how a system or organization provides security services to protect sensitive and critical system resources.

The first one is more light and defines a different type of security policy, the second one on the other hand define a more strict and formal policy; anyways both of them are correct, highlighting how security policies can have the same name but represent different things.
##### Development of a Security Policy
During the development a security manager must consider the following factors:
- The value of the asset being protected
- The vulnerabilities of the system
- The possible attacks that can be made to the asset (attack trees can be useful here)
Also the manager must keep in mind the following trade-offs:
- Ease of use VS Security
	Typically the introduction of security mechanisms in an application tend to lower the ease of use of said application, let's say for example the utilization of login + rechapta, the login requires that the user ***MUST*** remember the username/email and password and also the rechapta slows down the user to assert that he is not a bot.
	Or again let's take for example virus-checking software reduces available processing power and introduces the possibility of system crashes or malfunctions due to improper interaction between the security software and the operating system.
- Cost of security VS cost of failure and recovery
	The security mechanisms and functions are not only a cost during development time, but are also a passive cost just to maintain them up so the managers are called to decide which is better between maintaining them or spend money after a failure occurs to recover from it.
	The possibilities are countless and are influenced by the possible attacks that the system can suffer from, the value of the asset and the confidentiality/privacy level of the information that could possibly be exploited.
> Those trade-offs says loud and clear how the definition and implementation of a security policy is business decision that can be influenced by the legal minimal requirements imposed by the law.
#### Security Implementation
The implementation involves 4 different courses of action:
- ***Prevention***
	This is not ideal for some threads, but there is a numerous of which that prevention is a reasonable goal to resolve them, let's take for example the utilization of a secure cryptographic algorithm to encrypt transmission messages, the possible attacks on confidentiality are prevented to happen.
- ***Detection***
	Absolute protection is not always possible, but the detection of an attack is a much more practical way to handle those thread that cannot be solved.
- ***Response***
	This is an action which can take place when an attack is detected.
	Let's say that a DoS is taking place, it is detected then a response is to possibly block the host/hosts whose are making the attack to prevent further damage to the assets.
- ***Recovery***
	An example of recovery is the use of backup systems, so if data integrity is compromised, a prior, correct copy of the data can be reloaded.
#### Assurance and Evaluation
Consumers of the security system wants that it works as intended(Grazie al cazzo).
That is, security consumers want to feel that the security infrastructure of their systems meet security requirements and enforce security policies.
So this take us to:
- ***Assurance***
	Attribute of a security system which indicates how a security policy is enforced by the system itself.
	> Assurance is used to and embodies two different aspects, system design and system implementation.
	> It deals with the questions, “Does the security system design meet its requirements?” and “Does the security system implementation meet its specifications?”.
	
	It Is expressed by a degree of confidence, so it's not that formal as it seems, but it can be pretty useful to assure the consumers.
- ***Evaluation***
	Is a process of examination of an application or system to evaluate it based on a specific criteria.
	Evaluation involves testing and may also involve formal analytic or mathematical techniques. 
	> The central thrust of work in this area is the development of evaluation criteria that can be applied to any security system and that are broadly supported for making product comparisons. 
