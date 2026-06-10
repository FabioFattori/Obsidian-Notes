## Chapter 1 
### Definition of computer security
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
- **Moderate** => 