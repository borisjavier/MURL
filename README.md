# MURL
A DOMAIN REGISTRAR SERVICE FOR THE METANET AND THE MURL PROTOCOL 

Introduction 

Having domain names as used on the internet is desirable for marketing purposes, branding or just to enjoy the advantages of having an easy to remember name on the internet. 

This is the main reason why vanity addresses as specified in section 2.2 of the Metanet Protocol’s original document are not the best solution to solve the problem of assigning Domain names on the Metanet. 

As said in the original document: “It is envisaged that many protocols may be developed for locating on-chain resources, such as the ‘b://’ and ‘c://’ protocols already in use. In the same way that the is an umbrella protocol flag for all on-chain Metanet data, it is envisaged that a generalised resource location protocol ‘mnp://’ for the Metanet can be used as an umbrella locator by linking domain names to node identifiers 𝐼𝐷𝑛𝑜𝑑𝑒.” 

The MURL protocol is a sub-protocol of the Metanet protocol to allow the standardization of TLD, domain names, and subdomains in the Metanet, allows mapping 1-1 for domain names and node identifiers and most importantly, constitutes proof of ownership for domain names. 

Although it seems obvious from the Metanet protocol's original document until now there is no way to acquire a domain on the Metanet and have it working in a browser. It is as if the creator of the Metanet protocol left this simple issue for someone else to solve. 

This document can be interpreted as the technical standard for the registration of domain names in the Metanet and complementary information to section 2.2 of the Metanet original document. 

 

 1. The Protocol 

Below the Metanet protocol, there’s another flag, the sub-protocol flag, the purpose of this one is to create ways to structure important information so that the Metanet becomes an easy and useful protocol. One of the most important tasks of this sub-protocol should be to allow DNS resolvers to query for domain names mapped to Metanet node IDs. 

In the known DNS system, the domain names are mapped against IP addresses, in the Metanet the same thing is valid, but domain names are mapped against Node Identifiers; There is an authoritative DNS server which in our case is the Blockchain itself, and there are DNS Root Nameservers and TLD Nameservers. In the Metanet, these two are replaced by anyone running a BSV node with the ability to serve as a Domain Name library 24 X 7 X 365 hours, the purpose of these servers is to maintain a record of all Domain Names – Node Identifiers pairs and keeping it updated with new info in the Metanet, taking advantage of the MURL flag as an index. 

 

1.1 Domain names and TLD (Top Level Domains) 

In the known internet, there are TLD Nameservers and for some reason, TLDs are important, for the sake of easiness of usage and keeping this friendly costume, the Metanet keeps the Domain-TLD structure, however, there is a key difference in the way these “last names” are chosen. Anyone can choose his own TLD freely or create a new one if he wants.  In time what we will see is people using certain TLDs more than others, some becoming more popular and others going to oblivion. Anyway, in the Metanet, there is the freedom to choose whatever TLD the user wants to choose. 

2. Domain Name Registration Process 

2.1 Identity Verifier 

To register a new domain name in compliance with all the regulations there is a need for an identity registrar, as a private agent, I can use the Metanet and a service provider like Google GCP (Google Cloud Platform) or any other.  The database, whether it is Blockchain-based or server-based, must save the basic data like name, address, city, country, phone, and most of all, the encrypted version of the private key associated with this real identity.  One function can decrypt and obtain the private key which will be used to sign the property of the Domain name, or any other information as the SmartNotes (stable coin on BSV), Smart Contracts, Future contracts, etc... 

2.2 Registration process 

Using HTML5 standard form and a simple serverside script (using one of the bitcoin libraries available like planter, bitcoinfiles, etc...), the information is recorded in a Metanet node with the sub-protocol flag and a signature as follows: 

<Metanet Flag> <Pnode> <TxIDparent>  

<MURL flag> <A. domain> <B. complete-path> <C. node identifier> <A&B&C signed> <Bitcoin owner address> 

  

The <MURL> flag comes behind the <𝑇𝑥𝐼𝐷𝑝𝑎𝑟𝑒𝑛𝑡> and is comprised of the following elements: 

<MURL> <A. Domain> <B. Complete path> <C. Node Identifier> <A&B&C Signed> <Bitcoin Owner Address> 

Where 

<A. Domain> is the domain name with TLD included e.g. myaawesomesite.com, 

<B. Complete path> is the MURL, e.g. myawesomesite.com/jokes/january/women, 

  

2.3 Ownership Verification 

In Section 2.2, there is a paragraph saying “Since Metanet domains already come with a permissions system (the public key) there is no need to issue a certificate to prove ownership.”, it is the case for vanity addresses, however, alternatively to vanity addresses there can be Domain names assigned by the Authoritative Nameserver, in our case, the Blockchain itself. If we are to register a 1-1 record of domain names in the Blockchain, then we need to guarantee the ownership of these domain names and it can be done by signing the domain plus the MURL plus the node identifier with the private key of the owner, also we must record the owner address to verify ownership afterward. 

Let’s say someone attempts to register an already taken domain, the registrar must verify if the private key of the one who tries to get this domain is the same as the one who signed the original property of this domain.  It may be done easily using the sign / verify methods of the bsv library. 

2.4 Subdomains and endpoints 

The metanet protocol itself is capable of tracking folders and files (endpoints), as the document says: “if we are able to associate an entity with an 𝐼𝐷𝑛𝑜𝑑𝑒, then we can construct MURLs to locate resources simply by following a path down a Metanet tree of nodes associated with the root 𝐼𝐷𝑛𝑜𝑑𝑒.” In the case of subdomains, a new registry must be done using the MURL protocol. 

3. Mapping MURL to Node Identifiers. 

Using the Metanet protocol together with the MURL protocol together the browser can make the request, as usual, there is a DNS resolver which receives the request from the browser (if the MURL is not cached in the browser) and queries the Domain name server (The Metanet itself), to map the nodes containing the information that the user is querying. 

4. Authorithy 

Since MURL is a protocol, many actors may come and build their own systems to assign new domains to node identifiers. The huge advantage of having this record standardized in a single protocol is that no matter how many players are in the game of assigning new domain names to the record, there is only one record. 

5. Cost of Domain Names.  

Competence between these players determine the price of domain names, however, even though supply and demand may cause these prices to grow or decrease, they must be considerably cheaper than in normal internet: Once the property of a domain name is signed by the owner, there is property while the owner of the identity holds control of the account where the private key is. 

6. Browser and DNS Resolver compatibility  

Once we have a working database to let a BIND (Berkeley Internet Name Domain)-like software act as a DNS resolver we have two more challenges ahead: First is how is this DNS resolver going to act to bring Node identifiers instead of IP addresses and the second is, once the Node identifier is resolved, how is the OP_RETURN information going to be "translated" to browser valid source code. The first one is as easy as it can be: BIND 9 software (https://www.isc.org/bind/), which is the most widely used to resolve DNS doesn't specify that in the IP space cannot be a different identifier, however, when dealing with Domain Names, the software has a filter called FQDN (Fully Qualified Domain Name), this could be a problem if it assumes these names are always preceded by HTTP or https protocols. This is open-source software so, if it is limited to these two protocols then a patch should be made to allow the program to differentiate between HTTP and MNP protocols to avoid name collisions from the beginning.
The second challenge is once the resource is found, how is the browser going to interpret the source comprised in the OP_RETURN payload: This solution may be achieved at the browser level, I have a great suspect that Maxthon browser has already a built-in feature to decode this content and let the native browser see valid source code.
