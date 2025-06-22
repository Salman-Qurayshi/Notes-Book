# Offensive

## VA

- **A vulnerability assessment is a systematic process of identifying, quantifying, and prioritizing weaknesses in an information system.** It's essentially a security checkup for your digital assets.
- **Vulnerability management** is the ongoing process of identifying, assessing, prioritizing, and mitigating vulnerabilities in an organization's systems, applications, and networks. It's a proactive approach to security that aims to prevent cyberattacks by addressing weaknesses before they can be exploited.
1. Identify Vulnerabilities
2. Assess Vulnerabilities # Evaluating the potential impact of each vulnerability and assigning a risk score.
3. Treat Vulnerabilities

****
- 01 Scope out the Engagement 
# know what you want to do and how much will you go or do it.
02 Perform a Risk Assessment & Threat Modelling
# Determine threats to the system, and find weaknesses that could be exploited by threats 
03 Know the physical and logical assets in scope
# Discovery phase e.g  Identify hardware components like servers, routers, switches, and endpoint devices etc.
04 Scan the assets
# 
05 Validate the findings
06 Prepare a Remediation Plan
07 Reporting to the Senior Management
08 Repeat the Cycle every three months or as per your business requirements or after every major change
09 Keep comparing the data and learn to measure your VA program and Follow CMMI
- Responsibilities

![Untitled](Offensive%202193e043159d81d58cf8f6c2d7bf497f/Untitled.png)

- 

## Hacking 101 & Incident Response + Network Pent:

- **Incident Response (IR)** is a structured approach to managing and mitigating the impact of a security breach or other disruptive event. It involves a series of coordinated actions to identify, contain, eradicate, recover from, and learn from security incidents.
    
    **Key phases of incident response:**
    
    - **Preparation:** Developing incident response plans, defining roles and responsibilities, conducting training, and establishing communication protocols.
    - **Identification:** Detecting and recognizing an incident, gathering initial information, and activating the incident response team.
    - **Containment:** Isolating the affected systems or networks to prevent further damage and data loss.
    - **Eradication:** Eliminating the root cause of the incident and removing any malicious components.
    - **Recovery:** Restoring systems and data to normal operations while implementing preventive measures.
    - **Lessons Learned:** Analyzing the incident to identify weaknesses, improve processes, and prevent future occurrences.
- **IANA** stands for **Internet Assigned Numbers Authority**
    
    It's essentially the global manager of the internet's address book.
    
    **What does it do?**
    
    **IP Address Allocation:** IANA oversees the distribution of IP addresses (both IPv4 and IPv6) to regional registries.
    
    **Domain Name System (DNS) Root Zone Management:** It manages the top level of the DNS hierarchy, ensuring that domain names resolve correctly to IP addresses. 
    
- **Computer Security Incident Response Team** (CSIRT)
- **Word Web Bugs**
 are **documents that can be used to track attackers by creating a callback when opened, which reveals the attacker's IP address**. They can be used for cyber deception classes and don't require Microsoft Word to be open or macros to be enabled. There are two document templates for Word Web Bugs: web_bug.doc and web_bug.html.
- **write blocker** 
is a hardware or software device that prevents data from being written to a storage device.
When you connect a storage device (like a hard drive or USB stick) to a system through a write blocker, the device can be read, but any attempts to write data back to it are blocked.
It ensures that the original data remains intact during the forensic investigation process. This is crucial for maintaining the integrity of digital evidence.
So, while write blockers primarily protect data, they also facilitate the creation of accurate and reliable copies for forensic investigations
- **drive duplicator**
is a hardware device designed to create exact copies of data from one storage device to another.
Unlike write blockers, drive duplicators allow data to be written to the target device.
- **Null routing** 
also known as blackholing, is a network technique where traffic to a specific IP address or range is intentionally dropped or discarded. It is commonly used as a defense mechanism against Distributed Denial of Service (DDoS) attacks
- **War dialing** 
is an outdated but still potentially dangerous technique where an attacker systematically dials a large number of phone numbers in search of unprotected modems.
Once a modem is found, the attacker can potentially gain access to the connected system.
    
    **How it works:**
    
    - A computer program is used to dial phone numbers automatically.
    - If a modem answers, the program attempts to establish a connection.
    - If successful, the attacker can try to exploit vulnerabilities in the system.
- **War driving**
is a similar concept, but instead of phone lines, it targets wireless networks. An attacker drives around searching for unsecured Wi-Fi networks, often using a laptop or smartphone equipped with specialized software.
    
    **How it works:**
    
    - A vehicle is equipped with a wireless network adapter.
    - Software scans for accessible Wi-Fi networks.
    - Once found, the attacker can attempt to connect and exploit vulnerabilities.
- **What is Simple Network Management Protocol (SNMP)?**
Simple Network Management Protocol (SNMP) is an application-layer protocol for monitoring and managing network devices on a local area network (LAN) or wide area network (WAN).
The purpose of SNMP is to provide network devices, such as routers, servers, and printers, with a common language for sharing information with a network management system (NMS).
SNMP's client-server architecture has the three following components:
    1. an SNMP manager;
    2. an SNMP agent; and
    3. a management information base (MIB).
    
    The SNMP manager acts as the client, the SNMP agent acts as the server and the MIB acts as the server's database. When the SNMP manager asks the agent a question, the agent uses the MIB to supply the answer.
    

## WSTG

- **Passive Testing
Definition**: Observing and gathering information about a web application without interacting with it in a way that could alter its state.
**Example**: Monitoring network traffic, reviewing source code, or analyzing HTTP responses.
- **Active Testing**
    
    **Definition**: Actively interacting with a web application to discover vulnerabilities by sending requests and observing how the application responds.
    
    **Example**: Running SQL injection attacks, submitting forms with malicious input, or using automated tools like OWASP ZAP or Burp Suite to test security.
    

In essence, **passive testing** is about collecting data without affecting the application, while **active testing** involves probing the application for weaknesses by directly engaging with it.

### **Information Gathering**

- **Definition**: Collecting data about the target web application, its infrastructure, and technologies used.
- **Example**: Discovering subdomains, server details, or finding out what software is running.

### **Configuration and Deployment Management Testing**

- **Definition**: Checking for misconfigurations and insecure settings in the web application and its deployment environment.
- **Example**: Identifying default credentials, exposed admin interfaces, or unnecessary services running.

### **Identity Management Testing**

- **Definition**: Evaluating how the application manages user identities and accounts.
- **Example**: Testing the registration process, password policies, and user account recovery mechanisms.

### **Authentication Testing**

- **Definition**: Assessing the mechanisms that verify user identity.
- **Example**: Testing for vulnerabilities in login forms, multi-factor authentication, and session tokens.

### **Authorization Testing**

- **Definition**: Verifying that users can only access resources and actions they are allowed to.
- **Example**: Checking for horizontal and vertical privilege escalation issues.

### **Session Management Testing**

- **Definition**: Analyzing how the application handles user sessions and session tokens.
- **Example**: Testing for session fixation, session hijacking, and secure cookie settings.

### **Input Validation Testing**

- **Definition**: Ensuring that the application correctly validates and sanitizes user input to prevent attacks like SQL injection or XSS.
- **Example**: Submitting malicious input to see if it is correctly handled or blocked.

### **Error Handling**

- **Definition**: Reviewing how the application handles errors and whether sensitive information is exposed.
- **Example**: Triggering errors and analyzing the messages for information leaks.

### **Cryptography**

- **Definition**: Assessing the use and implementation of cryptographic functions.
- **Example**: Checking SSL/TLS configurations, encryption of sensitive data, and secure storage of keys.

### **Business Logic Testing**

- **Definition**: Testing the application’s workflows to ensure they function as intended and are secure.
- **Example**: Trying to bypass payment steps or manipulate discounts.

### **Client-side Testing**

- **Definition**: Examining how the client-side (browser) code is handled, including JavaScript and HTML.
- **Example**: Testing for DOM-based XSS, CSRF tokens, and secure storage of data in the browser.

### **API Testing**

- **Definition**: Testing the security and functionality of Application Programming Interfaces (APIs) used by the web application.
- **Example**: Checking for broken authentication, improper rate limiting, and data exposure through APIs.

- **Web fingerprinting** 
is the process of identifying unique characteristics and behaviors of a web application or a website to determine its underlying technologies, frameworks, content management systems (CMS), and versions. This technique is often used in the reconnaissance phase of penetration testing or security assessments. # you can use tools like curl, nikto, nmap, firefox dev mode, nc, etc
- **Identify Application Entry Points** 
is a crucial step in security assessments and penetration testing. It involves locating all the points through which users or systems can interact with an application. Understanding these entry points helps in assessing the security posture of the application and identifying potential vulnerabilities.
**Application Entry Points**:
    - **Definition**: Points where users or systems input data into the application. These can be forms, APIs, URLs, file uploads, etc.
    - **Examples**: Login forms, search bars, contact forms, RESTful APIs, file upload fields.

- **Fuzzing** 
is a software testing technique used to identify vulnerabilities and bugs by providing unexpected or random input data to a program. The goal is to find issues that occur when the program encounters unusual or malformed data.
**Definition**:
**Fuzzing**: A testing method where the application is subjected to a large amount of random, malformed, or unexpected data inputs to identify crashes, memory leaks, or other unintended behaviors.
# you can use tools like burpsuite’s intruder, ffuf, dirbb, dirbuster etc
- **HTTP methods** 
are used to specify the desired action to be performed on a resource in an HTTP request. Each method corresponds to a different type of operation, and they play a critical role in web communication. 
Here’s an overview of the common HTTP methods:
    
    ### Common HTTP Methods
    
    - **GET**: Retrieves data from a server at the specified resource.
        - **Usage**: Requesting a webpage or API data.
        - **Example**: `GET /index.html`
    - **POST**: Submits data to be processed by the server, often resulting in a change or creation of a resource.
        - **Usage**: Submitting form data, uploading files.
        - **Example**: `POST /submit-form`
    - **PUT**: Updates or creates a resource at the specified URL.
        - **Usage**: Updating existing resources or creating new resources with a specific ID.
        - **Example**: `PUT /resource/1`
    - **DELETE**: Removes the specified resource from the server.
        - **Usage**: Deleting a resource, such as a user account or file.
        - **Example**: `DELETE /resource/1`
    - **PATCH**: Partially updates a resource. Unlike PUT, which replaces the entire resource, PATCH only updates the specified parts.
        - **Usage**: Making partial updates to a resource.
        - **Example**: `PATCH /resource/1`
    - **HEAD**: Retrieves the headers of a resource without the body. This is useful for checking metadata or status.
        - **Usage**: Checking if a resource exists, or to obtain headers.
        - **Example**: `HEAD /index.html`
    - **OPTIONS**: Describes the communication options for the target resource. It often returns the methods supported by the server.
        - **Usage**: Discovering available methods and capabilities of a server.
        - **Example**: `OPTIONS /resource`
    - **CONNECT**: Establishes a tunnel to the server identified by the target resource, typically used with proxies.
        - **Usage**: Setting up a network connection, often used in HTTPS.
        - **Example**: `CONNECT www.example.com:443`
    - **TRACE**: Performs a diagnostic trace of the request path. It is used to see how a request is processed by intermediaries.
        - **Usage**: Debugging and diagnostics.
        - **Example**: `TRACE /resource`

- **DNS (Domain Name System)** 
is a hierarchical system that translates human-readable domain names into IP addresses, allowing browsers and other network services to locate and connect to websites and other resources on the internet.
    
    
    ### Key Concepts of DNS
    
    1. **Domain Names**: Human-readable addresses like `example.com` that are easier to remember than IP addresses.
    2. **IP Addresses**: Numerical addresses (e.g., `192.0.2.1`) that computers use to identify each other on a network.
    3. **DNS Records**: Entries in a DNS database that provide information about a domain, such as its IP address or mail server. These records are stored in DNS zones.
    4. **DNS Query**: A request made by a client (like a web browser) to a DNS server to resolve a domain name into an IP address.
    5. **DNS Resolver**: A server that receives DNS queries and responds with the requested information. It typically forwards requests to other DNS servers if it doesn't have the answer.
    6. **DNS Zone**: A portion of the DNS namespace managed by a specific organization or administrator. It contains DNS records for domains within that portion.
    
    ### Important DNS Records
    
    - **A Record (Address Record)**:
        - **Purpose**: Maps a domain name to an IPv4 address.
        - **Example**: `example.com. A 192.0.2.1`
    - **AAAA Record**:
        - **Purpose**: Maps a domain name to an IPv6 address.
        - **Example**: `example.com. AAAA 2001:db8::1`
    - **CNAME Record (Canonical Name Record)**:
        - **Purpose**: Aliases one domain name to another. Useful for redirecting multiple domain names to a single domain.
        - **Example**: `www.example.com. CNAME example.com.`
    - **MX Record (Mail Exchange Record)**:
        - **Purpose**: Specifies mail servers responsible for receiving email for the domain.
        - **Example**: `example.com. MX 10 mail.example.com.`
    - **NS Record (Name Server Record)**:
        - **Purpose**: Specifies authoritative DNS servers for the domain. Indicates where the domain's DNS records are managed.
        - **Example**: `example.com. NS ns1.example.com.`
    - **SOA Record (Start of Authority Record)**:
        - **Purpose**: Provides information about the domain's DNS zone, including the primary DNS server, the administrator's email, and timing information for zone updates.
        - **Example**: `example.com. SOA ns1.example.com. admin.example.com. 2024080701 3600 1800 1209600 86400`
    - **PTR Record (Pointer Record)**:
        - **Purpose**: Maps an IP address to a domain name (reverse DNS lookup). Used for reverse DNS lookups.
        - **Example**: `1.0.192.in-addr.arpa. PTR example.com.`
    - **TXT Record**:
        - **Purpose**: Stores arbitrary text data, often used for verification purposes (e.g., SPF records for email authentication).
        - **Example**: `example.com. TXT "v=spf1 include:_spf.example.com ~all"`
    - **SRV Record (Service Record)**:
        - **Purpose**: Specifies the location of servers for specific services within a domain.
        - **Example**: `_sip._tcp.example.com. SRV 10 60 5060 sipserver.example.com.`
- **Session Fixation** 
is a type of attack where an attacker tricks a user into authenticating a session identifier (session ID) that is already known to the attacker. Once the user logs in, the attacker can then hijack the session and gain unauthorized access to the user's account without having to know the user's credentials.
    
    ### How Session Fixation Works
    
    1. **Attacker Creates a Session**: The attacker initiates a session with the target web application and obtains a session ID.
    2. **Victim Uses the Session**: The attacker tricks the victim into using the attacker's session ID. This can be done through methods such as sending the session ID in a URL, embedding it in a link, or placing it in a hidden form field.
    3. **Victim Authenticates**: The victim logs in to the web application, and their session is authenticated with the session ID that the attacker knows.
    4. **Attacker Gains Access**: Since the session is now authenticated, the attacker can use the same session ID to access the victim's account without needing to log in.

- **Cross-Site Request Forgery (CSRF)** 
is a type of web security vulnerability where an attacker tricks a user into performing actions on a web application in which the user is authenticated, without their knowledge or consent. Essentially, the attacker exploits the trust that a web application has in the user's browser.
    
    ### How CSRF Works
    
    1. **User Authentication**: The user logs into a web application, and the session is authenticated with a session ID or token stored in the browser (often in cookies).
    2. **Malicious Request**: The attacker creates a malicious request to the web application. This request could be anything that the user is allowed to perform, such as changing account details, making a purchase, or transferring funds.
    3. **User Interaction**: The attacker tricks the user into executing the malicious request, typically by embedding the request in a link, image, or form on a website or through an email.
    4. **Unintended Action**: Since the user is already authenticated, the web application processes the request as if it were initiated by the user, leading to unintended actions being performed.
    
    ### Example of a CSRF Attack
    
    Suppose a user is logged into a banking application. The attacker sends the user an email with a link to an image that, when loaded, makes a GET request to the banking application to transfer money from the user's account to the attacker's account. Because the user is already authenticated, the bank processes the request, and the transfer occurs without the user's consent.
    

- **Insecure Direct Object Reference (IDOR)** 
is a type of access control vulnerability that occurs when an application provides direct access to objects or resources based on user-supplied input, without properly validating the user's authorization to access those objects. This can allow attackers to manipulate input parameters to access unauthorized data or perform unauthorized actions.
    
    ### How IDOR Works
    
    1. **Direct Access to Resources**: An application allows users to directly access resources (like files, records, or account details) by specifying an identifier in the URL, query string, or request body.
    2. **Lack of Authorization Checks**: The application does not properly check whether the user is authorized to access the resource identified by the provided identifier.
    3. **Manipulation by Attackers**: An attacker modifies the identifier to point to a resource they do not have permission to access. If the application does not enforce proper authorization checks, the attacker gains access to the unauthorized resource.
    
    ### Example of an IDOR Attack
    
    Suppose a web application allows users to view their order details by visiting a URL like
    `https://example.com/order?id=12345`
    
    If the application does not verify that the currently authenticated user is the rightful owner of the order with ID `12345`, an attacker could change the URL to:
    
    `https://example.com/order?id=12346`
    
    If order `12346` belongs to another user, and the application doesn't enforce proper access controls, the attacker could view that user's order details.
    

- **SQLMap** 
is an open-source penetration testing tool used to automate the detection and exploitation of SQL injection vulnerabilities in web applications. It allows security professionals and ethical hackers to test the security of web applications by identifying and exploiting SQL injection flaws, which can lead to unauthorized access to databases and sensitive data.
    
    ### SQLMap Flags
    
    - **`u`**: Specifies the target URL.
    - **`-dbs`**: Enumerates all databases.
    - **`D`**: Specifies the target database.
    - **`-tables`**: Enumerates tables in a specified database.
    - **`T`**: Specifies the target table.
    - **`-dump`**: Dumps data from the specified table.
    - **`-batch`**: Runs in non-interactive mode, using default answers to all prompts.
    - **`p`**: Specifies the vulnerable parameter to test for SQL injection.
    - **`v`**: Sets the verbosity level of output (0-6).
    - Example:
    `sqlmap -u "http://example.com/vulnerable.php?id=1" -D <database_name> -T <table_name> --dump`