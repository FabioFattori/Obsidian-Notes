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
## Chapter 2
### Symmetric Encryption
Is the most common encryption in use since Giulio Cesare.
![[Pasted image 20260612151254.png]]
There is two requirements to use secure Symmetric encrypt:
- the use of a secure encryption algorithm
	  Which means that the attacker should not be able to decrypt ciphertext or find the key even if he is in possession of a number of ciphertext associated with their respective plaintext output.
- the sender and receiver must have got the key in a secure way and must keep it secure
	If this is not respected the entire communication is readable therefor the mechanism is useless
#### General Attacks Approaches to Symmetric Encryption
- ***Cryptanalysis***
	> Which relies on some characteristics of the algorithm being used and, could not be utilized, some knowledge of the general characteristics of the plaintext sent or some pairs of plaintext-cyphertext.
	
	This attacks tries to deduce/decrypt a specific cyphertext content or the secret key used in the communication.
- ***Brute force attack***
	On average a brute force algorithm must try half of the number of possible keys to discover the actual key used.
	Not only that but some type of automatic analysis/recognition must be created to make the process bearable and sustainable for the attacker (the attacker cannot "check by hand" each possible result to see if the cyphertext is turned into plaintext or garble \[random chars\]).
	So there's more to this attack that may seems, to supplement the brute-force approach, some degree of knowledge about the expected plaintext is needed, and some means of automatically distinguishing plaintext from garble is also needed.
#### Symmetric Block Encryption Algorithms
Most commonly used symmetric algorithms.
> They divide the plaintext input into fixed length blocks and then cypher them.

3 major algorithms are provided:
- DES (Data Encryption Standard)
- Triple DES
- AES (Advanced Encryption Standard)
![[Pasted image 20260612162727.png]]
##### DES
It's the most old algorithm and the most studied of them all.
Two concerns:
1. Possibility of cryptanalysis attack to DES algorithm, which is proven not possible cause over the years numerous attempt where made and not even one has succeeded.
2. Length of the key, which for todays computer is a big problem.
   56 bits keys just simply not cut it and can be disclosed in about an hour (see table), now days is prefered the use of triple DES or AES both of which have a key which is, at least, doubled in sized compared to DES.
![[Pasted image 20260612163625.png]]
##### Triple DES
> This algorithm actually is DES but applied 3 consecutive times to the input.

This simple implementation resolved the primary concern of DES, so the brute force attack is now not desirable from the attacker part and the cryptanalysis is still not possible (this was true also for DES).
A concern is resolved but it comes with two problems/drawbacks, which are:
- ***Software implementation of the algorithm is sluggish***, the DES was made for 1970 hardware and does not produce efficient code therefor we can clearly see that reproducing 3 times the same not optimized code can be ***very time consuming***.
- ***Block size***, DES utilize a block size of 64 bits which, for reasons of efficiency and security, is not enough, a ***longer block is desirable***.
##### AES
NIST redacted a contest to find out a worthy successor to DES and 3DES by enstablishing some minimal requirements for the algorithm:
- Block length of 128 bit
- Key length of 128,192 or 256 bits
- Computational efficiency and flexibility
##### Practical Security Issues (ECB)
To encrypt the plaintext message it must be broken up into blocks first, and each of them must be encrypted alone.
The simplest approach to do so is called Electronic CodeBook mode (ECB)
![[Pasted image 20260612184115.png]]
Which:
- first breaks down the message into n blocks (which are called ***P*** in the image)
- then each of them are encrypted with the same key making the ***C*** blocks, whose can be sent in the network.

> The problem is that ECB for lengthy messages is not secure, a cryptanalyst can recognize and exploit regularities in the plaintext to ease, therefor be able to, decrypt messages.

To overcome these vulnerability for lengthy message a number of techniques were developed called ***nodes of operations***.
#### Stream Cyphers
This type of cyphers operate and encrypt with a much smaller unit than blocks, in fact they can encrypt one byte at a time, even one bit at a time.
![[Pasted image 20260612185209.png]]
They operate as follows:
- the key is given to the encryptor to generate a semi-random 8-bit long number in binary which is called the ***keystream***
- an element/unit of the plaintext is given to the encryptor
- the XOR bit operation is done between the unit of the stream and the keystream
- and so on until the entire stream is encrypted.

|            | Blocks                 | Stream                                      |
| ---------- | ---------------------- | ------------------------------------------- |
| Advantages | The keys can be reused | Typically faster and has a leaner code base |
They are equal in terms of what they bring to the table, they shine in different contexts based on the data to encrypt and the use cases.
### Message Authentication and Hash Functions
#### One Way Hash Function
> a hash function accepts a variable-size message M as input and produces a fixed-size message digest H(M) as output.

There are many ways which a message can be authenticated using the hash function, here's a few:
- Symmetric encryption for message digest
  ***IF*** it is assured that only the sender and the receiver shares the key, the authenticity is assured.![[Pasted image 20260612191241.png]]
- public-key encryption for message digest
  ![[Pasted image 20260612191454.png]]
  Which has ***two advantages***:
  1. it provide a digital signature and message authentication
  2. doesn't require any key transmission 
> these two approaches are preferred instead of the ones which encrypt all the message cause they are faster.

> ***BUT*** there are other approaches that are EVEN BETTER cause:![[Pasted image 20260612192356.png]]

Here's one:
- Keyed hash function ![[Pasted image 20260612192535.png]]
  This approach consist of the assumption that both parties have a secret value ***K*** which is incorporated in the hash function itself, the message transmitted is interpolated to this _K_ two times as shown in the picture above, this is done to make it more secure (if it was only at the start or at the end it was less secure).
  >Because the secret key itself is not sent, it should not be possible for an attacker to modify an intercepted message.
  > 	As long as the secret key remains secret, it should not be possible for an attacker to generate a false message.
#### Secure Hash Function
> A Hash Function (***H***) is a way to produce a fingerprint of a file, message or block of data.
##### Hash Function Requirements
To be useful a hash function must be:
- applicable to a block of data of _any_ size
- it must produce an output of a fixed length
- it's execution must be relatively light so that it makes hardware and software implementation practical
- for any implementation _h_, given a _x_ it is true that H(_x_) = _x_.
  Those hashing function are called ***one-way*** or ***preimage resistant***.
- For any given _x_, is computationally infeasible to find _y_ != _x_ with H(_y_) = H(_x_).
  This property is called ***second preimage resistant*** or ***weak collision resistant***.
- It is computationally infeasible to find any pair (x, y) such that H(x)= H(y).
  A hash function with this property is referred to as ***collision resistant*** or ***strong collision resistant***.

> The first three are requirements for a more practical and simple application of the function

> The fourth is a requirements cause if the communication has a secret value and the function utilized is not one-way an attacker can easily discover said secret value (the attacker has the message _M_ and the H(_KMK_) so he can easily invert the function and extract the value _K_).

> The fifth, weak collision resistant, is important so that no message can have the same hash, this prevent the loss of data integrity cause an attacker could easily intercept a message and send a message with that same hash, in fact substituting the legittimate message to a fake/damaging message.
> The same could be said for the sixth.

##### Security of the Hash Functions
As with symmetric encryption, there are two approaches to attacking a secure hash function: cryptanalysis and brute-force attack.
![[Pasted image 20260612214822.png]]
160 bits hash now days appears more likely to be broken by a brute force attack.
##### Secure Has Function Algorithms
NIST initially released SHA-1 (Secure Hash Algorithm), weakness were found so they had to release a new version called SHA-2 which had 3 different algorithms: SHA-256, SHA-384 and SHA-512, the numbers represent the length of the output hash.
SHA-1 and SHA-2 have essentially the same internal structures, so in 2015 NIST decided to release SHA-3 as an alternative to SHA-2 algorithms.
##### Hash Applications
Hash can be used in:
- message authentication
- creation of digital signatures of things (fingerprints)
- passwords
	  So that the clear text password is not stored, and when an attempt of login occurs the stored hash and the attempt password hash are compared.
	  This require at least the preimage resistant, and possibly the second preimage resistant
- Intrusion detection
	  Storing the hash of a resource can tell us if that resource has been modified cause upon edit that same file will have a different hash than the stored one.
	  This require at least a weak collision resistance.
### Public Key Encryption
> Finds use in message authentication and key distribution

#### Structure
> Public-key algorithms are based on mathematical functions rather than on simple operations on bit patterns, such as are used in symmetric encryption algorithms

The main difference from symmetric cryptographic algorithms is that PKE is asymmetric, so it envolves two different keys.
> These technique is just and alternative path rather than a substitution to symmetric encryption, it's not straight up better or worse than symmetric, it has his strong point and his weak point as well as symmetric.

A PKE scheme has the following structure and parts involved:
![[Pasted image 20260612225213.png]]
- Plaintext (equal meaning to symmetric scheme)
- Encryption algorithm
- Public and Private key
	  One of which is provided as input with the plaintext to the encryption algorithm.
	  The public key is used for encryption, cause the content is exiting the local system and is going in to the 'public'(network).
	  The private key is used for decryption.
- Cyphertext
	  Output of the Encryption algorithm which depends on the plaintext and the key provided (public and private key creates different cyphertext).
- Decryption Algorithm.
In general a communication is initialized and carried on as follows:
1. Each user generates a pair of keys used for encryption and decryption of messages
2. Each user now put the public key in a public register or accessible file to permit other to communicate with him, in fact the public key of a specific receiver ***NEEDS*** to be used to _encrypt_ the message so that the designated receiver can accept and understand said message.
3. When the receiver receive the message he utilize his private key.
   No other user can decrypt the message except the designated user.
> With these scheme confidentiality is provided as long as users keep their private key secure and local.

> At any time a user can change is key by just generating a new pair and providing the public key to others.

If we would have a system directed towards data integrity and authentication we would use the following scheme:
![[Pasted image 20260612230617.png]]
> The only change is the key used for encryption and decryption

In a system like this in fact, we can assure that a message decrypted by the public key of user A was certainly sent by user A (Authentication) and also only user A would be able to edit the message that was decrypted by his public key (data integrity).
#### Applications for Public Keys Cryptosystems
- digital signatures
- symmetric key distribution 
- encryption of secret keys
Of course there are some algorithms which are the best/usable for some applications and not usable for others, here's a quick view:
![[Pasted image 20260612231228.png]]
#### Requirements for PKE
- It must be computationally easy for a party(user) to generate a pair of keys (_PU_ public and _PR_ private)
- It must be computationally easy for a sender the generation of cyphertext to send to a receiver => E(_PU,M_) = _C_
- It must be computationally easy for a receiver decrypting a cyphertext with his private key to get the plain text message => _M_ = D(_PR, C_) = D(_PR_, E(_PU,M_))
- It must be computationally infeasible for an attacker, known the _PU_, to derivate/extract the _PR_
- It must be computationally infeasible for an attacker, known the _PU_ and the cyphertext, _C_, get the message _M_.
Now we can add a sixth requirements which, although useful, is not needed for all the applications:
- Either of the two related keys can be used for encryption, with the other used for decryption.
  _M_ = D(_PU_, E(_PR, M_))= D(_PR_, E(_PU, M_))
#### Asymmetric Encryption Algorithm
##### RSA
> since invented this algorithm reigned supreme as the most widely used approach for the public key encryption

> RSA is a block cipher in which the plaintext and cyphertext are integers between 0 and _n_ - 1 for some _n_.

Currently, a 1024-bit key size (about 300 decimal digits) is considered strong enough for virtually all applications.
##### Diffie-Hellman Key agreement/exchange
> the first algorithm for public key encryption, still used today for some key exchange techniques.

> The purpose of the algorithm is to enable two users to securely reach agreement about a shared secret that can be used as a secret key for subsequent symmetric encryption of messages.
   The algorithm itself is limited to the exchange of the keys.
##### Digital Signature Standard (DSA)
Proposed by NIST.
The DSS makes use of SHA-1 and presents a new digital signature technique, the Digital Signature Algorithm (DSA).
> The DSS uses an algorithm that is designed to provide only the ­ digital signature function. Unlike RSA, it cannot be used for encryption or key exchange.

##### Elliptic Curve Cryptography
The majority of systems uses RSA, the problem is that the number of bits for the secure RSA has increased over the years increasing also the computing time and processing load over the applications.
> Elliptic Curve Cryptography is a more recent algorithm which is competing with RSA:
> is better than RSA based on the fact that utilizes less bits so the processing overhead is far less impeding.

> It's only problem is that it is too new, it does not have the fame ,years and consolidation that RSA has, so people still does not trust it.

### Digital Signature and Key Management
#### Brief Overview so far
public-key algorithms are used in a variety of applications.
In broad terms, these applications fall into two categories:
- digital signatures 
- key management and distribution
	which can be divided in: 
	- the secure distribution of public keys
	- the use of public key encryption to distribute secret keys
	- the use of public key encryption to generate temporary keys used for message encryption
### Digital Signatures
> Digital Signature is a technique to authenticate user in a communication.

> A digital signature is a result of cryptographic transformation of data which can authenticate a source, assure data integrity and signatory non-repudiation.

So the signature is a data dependent bit pattern, generated from a file, message or any other form of block of data which an agent utilizes as an input to a function.
Another agent can verify that:
1. the data block has been signed by the alleged signer
2. the data block has not been altered since the signing

FIPS define the following algorithms to generate/handle digital signatures:
- Digital Signature Algorithm (DSA)
	Based on a logarithm so that is not feasible to brute force.
- RSA Digital Signature Algorithm
- ECC Digital Signature Algorithm
Each of them have the following generic structure:
![[Pasted image 20260613011917.png]]
> These technique ***DOES NOT*** provide confidentiality, even if the message is encrypted, cause the message can be disclosed by simply decrypt the message using sender public key.

#### Public Key Certificates
This approach has a major weakness/vulnerability of inpersonification:
> Each users can broadcast their public key to make other users be able to 'speak' with him, this is convenient but an attacker can impersonificate a user, that has already communicated his public key, by communicating a new key that the attacker himself generated, so until the impersonificated user discover the forgery, the attacker can receive all of the messages directed to the victim cutted out from the communication.

This problem solution are public key certificates.
> The certificate is essentially a public key and, a user ID and a sign of an authorized and trusted third party entity.
> The certificate provides some additional informations about the third party entity and the duration of validity of the certificate.
##### Certificate Authorities - how a Certificate is Made
> The trusted third entity is a Certification Authority (CA) trusted by the users community.

The creation of a certificate is initialized by a user, which presents his public key to the CA and receive a signed certificate from them.
![[Pasted image 20260613014400.png]]
6. then the CA returns the signed certificate to the user who can start to utilize it.
##### How a Certificate is Validated by other Users
![[Pasted image 20260613014537.png]]
Here's an example of how the certificate is validated by users during communication:
![[Pasted image 20260613013854.png]]
#### Digital Envelopes
> This technique can be used to protect a message without needing to first arrange for sender and receiver to have the same secret key.

![[Pasted image 20260613110513.png]]
### Random and Pseudorandom Numbers
The use of random numbers is common in security systems to generate keys.
Those applications rise two requirements which can be incompatible from each other:
- Randomness 
	A number is random if it respects these two validation points:
	- Uniform distribution => the frequency of appearance of each digit in the generated number should be approximately the same
	- Independence => No digits/value in the generate number can be inferred by the others digits/value.
	There are many tests to verify that a number respects the uniform distribution, but there are none to verify independence.
	The common strategy is to apply a number of tests such that the confidence is strong.
	> As are things today, random number are used as follows:
	> "if a problem is too hard or time-consuming to solve exactly, a simpler, shorter approach based on randomization is used to provide an answer with any desired level of confidence."
- Unpredictability
	> In applications such as reciprocal authentication and session key generation, the requirement is not so much that the sequence of numbers be statistically random, but that the successive members of the sequence are unpredictable
#### Random VS Pseudorandom
For pseudorandom number we intend:
> random numbers (whose respects the requirements above) generated by an algorithm which is deterministic.

## Chapter 3
### Digital User Authentication Principles
> Digital user authentication is the procedure of establishing confidence in a user identities that are presented electronically to an information system.

The system, after a user identifies/authenticate himself, can determine which functions can the user do.
#### Means of Authentication
There are four ways the user can utilize to authenticate himself, each of them can be used solely or combined to others:
- Something that the individual knows
	Like a password or pin that he  has to provide to the system.
- Something the individual possess
	Like electronic keycards and also smart cards:
	This type of authenticator is called ***token***.
- Something the individual is(static biometrics)
	Authentication via retina or fingerprint.
- Something the individual does(dynamic biometrics)
	Something like handwriting recognition or also type rhythm.
> All of these methods have problems like theft of a password or token by an attacker, or again the individual losses the password or token.

>  With respect to biometric authenticators, there are a variety of problems, including dealing with false positives and false negatives, user acceptance, cost, and convenience.

>Multifactor authentication is a term which is referred to the systems that combine two or more of the means of authentication, which makes them considered as more secure.

#### Password Based Authentication
Generically to authenticate a user an ID and a password is requested by the system.
The password is compared to the stored password of the ID, if they match the user is logged in.
The ID, on the other hand, provides security as follows:
- The ID determines whether the user is authorized to gain access to a system.
	In some systems, only those who already have an ID filed on the system are allowed to gain access.
- The ID determines the privileges assigned to that ID
	Some IDs maybe be superuser or admin which have more privileges than a normal user.
	Some systems may also have a guest user which have an even more restricted list of privileges, if it even have any.
- The ID is used in a discretionary access control
##### The Vulnerability of Passwords
> Typically, a system that uses password-based authentication maintains a password file indexed by user ID.
> These file contain one-way hashes of the password.

- Offline dictionary attack
	Typically the file is protected by strong access controls, but some hackers can bypass them and get the file, once the file is collected they compare each hash to hashes of common passwords and if they find a match they will have the ID and the password to gain access to the victim account.
	> The countermeasures consists of more access controls to the file itself and/or intrusion detection mechanisms combined with a rapid reissuance of the passwords.
- Specific account attack
	It essentially is a brute force attack in which each possible password is tried until the correct one is discovered.
	> The countermeasure is an account lockout mechanisms which take place after a number of tries, typically 5.
- Popular password attack
	This one is also a brute force attack done to a number of IDs trying each popular password known to the attacker.
	> The Countermeasure is to limit the user choice for the password to the not popular passwords known.
- Password guessing against a specific user
	This attack consists in the attacker gaining some knowledge of the user and/or the security policy of the system whose can help him to infer the password of that specific user.
	> The countermeasure is to enforce the password security policies to make the passwords hard to guess, for example a policy rule can be that passwords must be changed after a period of time from their initialization.
- Workstation hijacking
	An attacker waits until a logged in workstation is inactive to jump in.
	> A countermeasure is to logout the workstation after a period of time of inactivity.
- Exploiting user mistakes
	Such as not changing default passwords of systems.
	> The countermeasure is to do some user training.
- Exploiting multiple password use
	If in a network multiple devices share the same password, the disclosure of it will cause a major damage to the system.
	> The countermeasure could be to update the security policy to forbid the use of equal or similar already used passwords in different devices/applications
- Electronic monitoring
	If a password is communicated across a network to log on to a remote system, it is vulnerable to eavesdropping. Simple encryption will not fix this problem, because the encrypted password is, in effect, the password and can be observed and reused by an adversary.
Even if the password system has all of this vulnerabilities it is still used cause smart cards cost more and are less practical to carry around and use expecialy if there is more than one.
And further, the other mechanisms rather cost more or have major risks than the password has.
##### The Use of Hashed Passwords
***Initialization of the password***
In operating systems (UNIX) the password is hashed with a salt value, which can be a pseudorandom number or a random number.
Once the algorithm finishes execution (which is slow on purpose to prevent/thwart attacks) the hashed value and the plaintext salt value are saved in the password file:
![[Pasted image 20260613225555.png]]

***Login attempt***
On login the provided ID is searched in the password file and the hashing function is runned with salt retrieved from the password file and the provided password, if the hashes match the login is valid.
![[Pasted image 20260613225805.png]]
> The salt value serves these three purposes:
> 	1. Just by looking at the password file, two equal password does not have the same hash.
> 	2. It greatly increase the difficult of an offline dictionary attack
> 	3. It becomes nearly impossible to find out whether a person with passwords on two or more systems has used the same password on all of them.

###### Threads to the UNIX Scheme
1. A password cracker (password guesser program) can be run on a logged in machine, the attacker could run thousands of tries with little resource consumption.
2. If the attacker gains a copy of the password file, he can run the password cracker on his machine and with some reasonable time crack the password that he wants.
##### UNIX Implementations (algorithms)
- crypt(3)
	> Is a encryption routine which utilizes the DES algorithm to encrypt a password of up to 8 char long.
	> 1. The password is converted into a 56 bit long value used as input to an encryption routine.
	> 2. The salt is 12 bit long which is used to convert the DES encryption algorithm to a one-way hash function.
	> 3. The modified DES algorithm is executed with a data input consisting of a 64-bit block of zeros.
	> 4. The DES is executed 25 times on the input
	
	Now this is shit, insecure and slow as fuck, but sometimes required (the scheme) for compatibility.

- Now the standard for UNIX systems is MD5:
![[Pasted image 20260613233057.png]]
- Also there is Bcrypt:
	![[Pasted image 20260613233247.png]]
	Also there is a cost value, which is a configuration parameter for the hashing algorithm, which determinate how slowdown the computation of the algorithm must be.
	For administrators passwords this can come in handy.
##### Password Cracking of User-Chose Passwords
###### Traditional Approaches
The standard way to crack a password is to have a dictionary of possible passwords and the system password file.
Foreach password in the dictionary it must be hashed with each available salt in the password file and then try to see if the result hash matched the file one.
If no matches are found the program could try some variations of the words in the registry.
> an alternative way, called ***rainbow table***, is to create a file with each possible passwords, and foreach of them he generates an hash foreach possible salt value.
> This approach is more space consuming than time consuming.
> FreeBSD and OpenBSD should be secure from this attack, windows was cracked in 14 seconds lol.
> The countermeasure for this attack is to handle a longer sized salt and hash so that the attacker must use too much space.

Attackers to mitigate this countermeasure started to guess common passwords, cause users, if given the choice, tend to use small passwords (from 6 to 8 char long) which can be easily guessed.
##### Modern Approaches
Now days the situation hasn't changes that much.
User are doing a better job at choosing their passwords, but even the attackers have been doing some improvements:
- The utilization of GPUs has boosted by a LOT the password cracking programs
- The a model for password generation using the probabilities of letters in natural language, in fact A probabilistic Context free grammar has been created boosting by a lot the password generation and cracking algorithms.
#### Password File Access Control
> One way to prevent password attack is to deny the access to the password file except to a privileged user, so that the attacker must know the password of the designated user to gain access to the password file.

> Often the hashes of the password and the IDs are in a separate file, which is called ***shadow password file***

Even with all of these security measures the following vulnerabilities remains:
- Many systems, including most UNIX systems, are susceptible to unanticipated break-ins.
	Which means that the attacker can exploit an application and break-in the system long enough to extract a copy of the password file
- An accident of protection may render the password file visible
- The utilization of the same password in two separate systems, if one is exploited also the other is in danger.
- A lack of physical security
	For example there is a recovery backup in a separated hard disk, an attacker can access it to make a copy of the password file
- Instead of capturing the system password file, another approach to collecting user IDs and passwords is through sniffing network traffic.
##### Password Selection Strategies
Our goal is to eliminate guessable passwords while allowing the user to select a password that is memorable.
The techniques are as follows:
- User Education
	Is the most unlikely to succeed based on the fact that the users may straight up ignore the guidelines, or it can be high turnover, whose make the technique useless.
	Nonetheless, providing some knowledge to the users is a step forward to a more secure system.
- Computer-generated passwords
	Are generally the least accepted ways from the users, they could find the provided password difficult to memorize and then be tempted to write it down, making the entire process quite useless.
- Reactive password checking
	Consists in the run on to the system of a password cracker to discover the weak/guessable password, once one is discovered it is deleted and the associated user notified.
	It has some drawbacks:
	>  the most important is the fact that is resource intensive to say the least, and the entire strategy is in a disadvantage compared to an attacker machine which can run at full CPU percentage the cracker.
	
	> And second, while doing the check, some guessable password remains in the system for an unspecified time, during which they can be cracked by an attacker.
- Complex password policy
	It's like the reactive password checking, except the fact that the check is done at the initialization of the password and not periodically.
	> This enhance the entire procedure guiding the user to a more secure and memorable password.

##### Rule Enforcement
![[Pasted image 20260614011752.png]]
The first one has been found as less guessable by password crackers and more easy to digest for users, but this rule alone is not sufficient for a strong secure policy, it's suggested to also utilize something like complex password policy technique.
##### Password Checker
> Very shitty approach but okay

It envolves in storing a dictionary of black listed words whose cannot be used in the password.
- It is space consuming, VERY consuming
- it is also time consuming, keep in mind that we are searching in an immense dictionary, and also if we want to check the combination of words the numbers of consumed space and time just go up.
#### Token Based Authentication
> Objects that a user possesses for the purpose of user authentication are called tokens.

Here we discuss cards (che schifo porco il tuo dio)
![[Pasted image 20260614013426.png]]
##### Memory Cards
> these type of cards function as mere data storage devices.

Memory cards usually store the security code, some card may have a chip which can store more than just the code.
These type of cards can be used as a physical access control to rooms.
> Memory card, in order to be used, must be presented with their associated password or PIN, which ensure more security than the password or PIN alone.

***Drawbacks***
- Requires special reader
	This increases the cost of using the token and creates the requirement to maintain the security of the reader’s hardware and software
- Token loss
	A lost token temporarily prevents its owner from gaining ­ system access.
	Thus, there is an administrative cost in replacing the lost token. 
	In addition, if the token is found, stolen, or forged, then an adversary need only determine the PIN to gain unauthorized access
- User dissatisfaction
##### Smart Cards
A wide variety of devices qualify as smart tokens.
These can be categorized along four dimensions that are not mutually exclusive:
- Physical characteristics => smart tokens comes with a microprocessor 
- User interfaces => smart tokens comes with a manual interface, such as a keypad, or a miniscreen
- Electronic interface 
	Smart tokens requires an interface to communicate with the reader/writer device, it can have one or both of the following:
	- Contactless 
	- Contact
- Authentication protocol
	3 categories of protocols:
	1. Static => the user must authenticate himself to the token, and then the token authenticate the user to the reader
	2. Dynamic password generator => the reader system and the token are syncronized and periodically they generate a random password which must be inserted manually or electronically 
	3. Challenge-Response => 
		   In this case, the computer system generates a challenge, such as a random string of numbers.
		   The smart token generates a response based on the challenge.
		   For example, public-key cryptography could be used and the token could encrypt the challenge string with the token’s private key.
> Now, smart cards, this type of smart token has the appearance of a credit card, has an electronic interface, and may use any of the type of protocols just described.

Smart cards has ROM, EEPROM and RAM
![[Screenshot 2026-06-14 alle 01.46.56.png]]
> Each time the card is inserted into a reader, a reset is initiated by the reader to initialize parameters such as clock value. 
> After the reset function is performed, the card responds with answer to reset (ATR) message. This message defines the parameters and protocols that the card can use and the functions it can perform.
> The terminal may be able to change the protocol used and other parameters via a protocol type selection (PTS) command.
> The card’s PTS response confirms the protocols and parameters to be used.
> The terminal and card can now execute the protocol to perform the desired application.

#### Biometric Authentication
> A biometric authentication system authenticate a user via his static and dynamic biometrics, utilizing pattern recognition

Compared to passwords and token is more expensive and also has yet to mature.
##### Physical Characteristics Used in Biometric Applications
- Facial characteristics 
	The most common approach is to define position and shapes of key elements of the face.
	An alternative approach is to use an infrared camera to produce a face thermogram that correlates with the underlying vascular system in the human face.
- Fingerprints
	In practice, automated fingerprint recognition and matching system extract a number of features from the fingerprint for storage as a numerical surrogate for the full fingerprint pattern.
- Hand geometry 
	This system memorize the geometry of the hand such has shape and length of the fingers
- Retinal pattern
	The pattern formed by veins beneath the retinal surface is unique and therefore suitable for identification
- Iris
	Same as the retinal but with the iris.
- Signature
	A hand signature is unique, the complexity here is that each signature from the same individual has some difference from each other
- Voice
	Same compliance here of the signature.
![[Pasted image 20260614021045.png]]
##### Operation of a Biometric Authentication System
At initialization a user must be ***enrolled***, which means registered to the system.
> When the user present his biometric data (example fingerprint), the system collect that data and extract features (number or sets of numbers) that can be stored in the database representing this unique biometric characteristic which is called ***user template***.
![[Pasted image 20260614021424.png]]

Once enrolled the system can identify or verify the user (based on the use case of the system)

***Verification***
Verification requires the PIN or password and the biometric data
![[Screenshot 2026-06-14 alle 02.18.30.png]]

***Identification**
Requires only the biometric data
![[Pasted image 20260614022005.png]]

## Second Module - AI Security
### Integrity
> Data integrity means that informations are not changed or deleted in an unauthorized or unwanted way through out their lifecycle

For ML:
- No data poisoning => training data is not altered
- model integrity => model parameters are not altered
### Confidentiality
> Ensures that only the authorized entities can access and/or edit sensitive data

### Privacy
> is the right of individuals to exercise control on which and what data is collected, processed and shared

![[Pasted image 20260614170723.png]]
![[Pasted image 20260614175030.png]]
### Fairness
> It means that information systems and algorithms must treat in an equal way all users and data subjects, preventing discriminatory outcomes and ensuring balanced resource allocation across the network.

![[Pasted image 20260614170939.png]]
### The Trust Problem
Systems cannot be automatically trusted, therefor they must be evaluated along two axes:
![[Pasted image 20260614171139.png]]
![[Pasted image 20260614171313.png]]

***Does AI improve the current situation in terms of confidentiality, privacy ecc...?***
Lol no, it actually creates more problems:
![[Pasted image 20260614171709.png]]
### Use Cases (this Shit Can Possibly Be skipped)
#### Smart Transportation Systems
![[Pasted image 20260614171827.png]]
##### Security Objectives of the Service
![[Pasted image 20260614171923.png]]
#### How Objectives Can Be Made in Practice
We have different options to choose from, each has pros and cons:
1. Central entity maintains crowdsourced data
	- cons
		  users loss data sovereignty, in fact the data controller keeps all the users data, it can alter in any way it likes the data and users must rely on it.
2. Keep data locally and distribute on request
	- pros
		Data sovereignty is maintained
	- cons
		Users devices must be always reachable and it's required from them more processing power, storage and communication capabilities
3. use a ledger(registro) to register data
	- pros
		rather simple implementation which keeps data integrity and traceability 
	- cons 
		latency, approach only available with small sized data 
4. use decentralized file systems 
	Need to 
	- ensure data integrity
	- control who has access to data 
	- ensure data persistence 
	> an usable approach can be the utilization of Content based addressing instead of location based addressing, so the data are organized in separate locations based on the content of the data itself.

	 Hash pointers (DLTs) are used, this approach now has the following pros:
	 - Fast data upload to the DFS
	 - is Possible to remove/edit data
	 - latency is much reduced by the utilization of DLTs to upload hashes.
	***But how do we provide access control?***
	> by utilizing DFS (Decentralized File System) and encryption
	
	***But how is data decrypted?***
	two possibilities:
	1. Central authorization server that provides keys to decrypt 
	2. secure-by-contract through a private ledger 
		![[Pasted image 20260614174028.png]]
		which has the following pros:
		- decentralization of keys custidy
			- no single point of failure
			- mitigate privacy leakage
		- transparency
			auditability of access permissions to data
	
	***But how is data persistence provided?***
	![[Pasted image 20260614174341.png]]
##### What Really Matters
![[Pasted image 20260614174522.png]]
### Problems and Techniques Identified so far
![[Pasted image 20260614175259.png]]
#### Threads and Actors
![[Screenshot 2026-06-14 alle 17.54.47.png]]
#### AI as a Tool for Security
![[Screenshot 2026-06-14 alle 17.55.37.png]]
### Adversarial Example
![[Pasted image 20260614175907.png]]
> Adversarial example are test-time inputs intentionally crafted to cause a neural network to make incorrect predictions while appearing natural to human observers.

Features:
- Modified by a legit input of the model
- Not seeable from a human perspective 
- Transferable across different models 
- Efficient to compute
Adversarial examples make ML-enabled systems unavailable or unreliable in critical applications.
#### Malware Detection Evasion
> Attack: Add bytes to Android APK to evade detection 
   Result: Malicious app classified as benign 
   Impact: System compromise, data theft 
   Key Metric: 85% attack success

![[Pasted image 20260614180225.png]]
#### Speech (Mis)Recognition
![[Pasted image 20260614180533.png]]
#### Adversarial Patch to Bounding Box
![[Pasted image 20260614180607.png]]
### Adversarial Attacks: Domains and Impacts
![[Pasted image 20260614181020.png]]
> Attackers with direct or indirect model access can deliberately break system safety guarantees

#### Why This Attack Matter
![[Pasted image 20260614181211.png]]
This reveals that ML models don't learn human-like features but they rely on non-robust patterns.
So Robustness ≠ Accuracy.
### Type of Adversarial Attacks
![[Pasted image 20260614193517.png]]
![[Pasted image 20260614193535.png]]
![[Pasted image 20260614193552.png]]
#### Adversary Goal
![[Pasted image 20260614193818.png]]
##### Misconceptions about NNs
Adversarial examples discovery shown and invalidated the following concepts about NNs:
- Individual neurons learn to detect specific semantic features
- Small input perturbations produce small changes in predictions
  ![[Pasted image 20260614194252.png]]
#### FGSM: Fast Gradient Sign Method
![[Pasted image 20260614194456.png]]
![[Pasted image 20260614194758.png]]
![[Pasted image 20260614194547.png]]
> Regarding computational cost this method is extremely efficient cause it's a single gradient computation

##### Transferability
> Adversarial examples crafted on one model often fool other models

This it's a big deals cause:
- Blackbox attacks become feasible without knowing the target model
- a Single attack can compromise multiple systems.
- This type of attack is not limited to neural networks
##### No Randomness
![[Pasted image 20260614212730.png]]
> The vulnerability is NOT random noise tolerance, but exploitation of specific decision boundary orientations

#### Why AE Exists?
Multiple factors contribute, no single explanation:
- Geometry of decision boundaries
- Non-robust feature learning => models learns from any features present in the image and AEs are seen as features to the model
- High-dimensional optimization => AEs exists in low density regions of the data, which the model during training has never seen 
- Distribution shift => AEs are a shift in data distribution compared to the normal data given to the model
#### PGD (Projection Gradient Descent) Attack
![[Pasted image 20260614214218.png]]
![[Pasted image 20260614214233.png]]
![[Screenshot 2026-06-14 alle 21.42.50.png]]
#### Why Transferability Occurs?
![[Pasted image 20260614215032.png]]
![[Pasted image 20260614215042.png]]
![[Pasted image 20260614215105.png]]
> XOR reveals the map of the perturbation applied to the image, it's not random noises but instead a symmetrical pattern.

#### Adversarial Training
> An attacker doesn't need model access, he can train his surrogate model locally then generate and test AEs and they likely will work thanks to transferability

![[Pasted image 20260614215607.png]]
> This makes the model more robust to the attack, but has a drawback: some of the accuracy on benign data is lost to gain robustness

This is the standard approach against attacks, but is not sufficient alone.
##### Randomized Smoothing
![[Pasted image 20260614215928.png]]
![[Pasted image 20260614220053.png]]
![[Pasted image 20260614220151.png]]
> The training is done with noised data 

![[Pasted image 20260614220415.png]]
### Privacy Leakage & Security in Generative AI and LLM
#### Privacy in AI Systems: Threat Models and Regulations
![[Pasted image 20260614220937.png]]
![[Pasted image 20260614221157.png]]
#### LLMs
![[Pasted image 20260614221351.png]]
##### Few Shot Learning
![[Pasted image 20260614222500.png]]
##### Zero Shot Privacy
![[Pasted image 20260614222700.png]]
#### Frase Della Vita Porcodio
> An aligned language model is helpful and harmless

for harmless we mean that if you ask him how to build a bomb, he will not respond.
for helpful we intend that he responds to you with useful and correct answers.
![[Pasted image 20260614233639.png]]
#### Agentic AI Systems
> An agent is an autonomous entity capable of perceiving its environment and acting upon it in order to achieve its objectives

![[Pasted image 20260614233802.png]]
decompose task → invoke tools → synthesise results → generate response
#### The ReAct Architecture
![[Pasted image 20260614234036.png]]
![[Pasted image 20260614234049.png]]
> Each service tool invocation may contain all the data of the context window of the agent, for this reason it is considered what follows:
> Transmitting patient data to a third-party search API — even inadvertently — may constitute a reportable data breach under both GDPR and HIPAA

#### Differential Privacy
![[Pasted image 20260614234438.png]]
![[Pasted image 20260614234523.png]]
![[Pasted image 20260614234538.png]]
### Small Language Models in Healthcare
> SLMs are Language models with parameter counts typically ranging from ~100M to ~7B, deployable on consumer-grade hardware

![[Pasted image 20260614234655.png]]

***Why there is this need?***
![[Pasted image 20260614234737.png]]
> The privacy guarantee of local inference breaks the moment the agent invokes an external tool

#### The Paradox of Privacy
![[Pasted image 20260614235152.png]]

So the question is:
> Can small language models, operating under zero-shot privacy instructions, reliably filter sensitive patient information from tool invocations?

#### The Four Stage Pipeline
![[Pasted image 20260614235330.png]]
##### Stage 1
> creates synthetic personas with contextual information and sensitive facts

![[Pasted image 20260614235507.png]]
##### Stage 2
> Attack prompt is An input query designed to elicit sensitive information from an agentic model by exploiting its tool-calling capabilities. 
> Attacks may be intentional or unintentional.

5 threats vectors:
![[Pasted image 20260614235721.png]]
##### Stage 3
> A tool is an external interface identified by a unique ID, a brief description, and a function signature (input parameters and output format)

The tools can be:
- safe <-> which are internal services
- unsafe <-> tools than exit the local area of services
##### Stage 4
LLM-as-a-judge approach.
> A large, high-accuracy LLM receives the sensitive facts extracted during persona generation and the actual tool call input produced by the agent, and determines whether leakage occurred.

###### Attack@1 Metric
> it measures the probability that at least one generation results in a privacy violation
![[Pasted image 20260615000246.png]]

#### The Prof Has Run Some Tests (who Gives a shit) but Something Was Discovered
![[Pasted image 20260615000515.png]]
Tested prompt systems:
![[Pasted image 20260615000554.png]]
![[Pasted image 20260615000656.png]]
#### Quindi per Concludere Dio Cane
![[Pasted image 20260615000948.png]]
![[Pasted image 20260615000956.png]]![[Pasted image 20260615001008.png]]

> ***Language models are neither secure nor private***

## Tutorial 1
Every host that is connected to a network has an exposed attack surface
#### NMAP tool
> The network mapper (nmap) is an open-source tool that has been specifically designed for discovering the host/devices that are connected to a specific network and to probe their exposed attack surface.

With it we can discover hosts connected to a networking by sending packets with a specific protocol like ICMP, TCP or UDP 
##### netdiscover tool 
Similar to nmap, this tool can be used to discover hosts connected to a network, but this tool in particular can discover them in a ***passive*** way.
> It doesn't send packets with a protocol, but it start listening to the network traffic.
> This can be done cause many protocols, like DHCP, are based on broadcast.

##### port scanner
> nmap can be used to scan ports of a discovered host.
> It essentially finds which services are listening to network sockets and are accessible from outside the specific host.

##### Vulnerabilities scanning 
> nmap has also some scripts which can tests and check for well known vulnerabilities in a discovered host softwares.

An example of script that can be installed is the one that can do a brute force attack to an exposed service by trying a series of frequently used usernames and passwords.
