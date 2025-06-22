# Tools/Resources

# Random:

### Tools:

- **SonarQube**
    
    **SonarQube** (formerly **Sonar**)[[3]](https://en.wikipedia.org/wiki/SonarQube#cite_note-3) is an [open-source](https://en.wikipedia.org/wiki/Open-source_software) platform developed by [SonarSource](https://en.wikipedia.org/wiki/SonarSource) for continuous inspection of [code quality](https://en.wikipedia.org/wiki/Software_quality) to perform automatic reviews with static [analysis of code](https://en.wikipedia.org/wiki/Static_program_analysis) to detect [bugs](https://en.wikipedia.org/wiki/Software_bug) and [code smells](https://en.wikipedia.org/wiki/Code_smell) on 29 [programming languages](https://en.wikipedia.org/wiki/Programming_language). SonarQube offers reports on [duplicated code](https://en.wikipedia.org/wiki/Duplicate_code), [coding standards](https://en.wikipedia.org/wiki/Programming_style), [unit tests](https://en.wikipedia.org/wiki/Unit_testing), [code coverage](https://en.wikipedia.org/wiki/Code_coverage), [code complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity), [comments](https://en.wikipedia.org/wiki/Comment_(computer_programming)), [bugs](https://en.wikipedia.org/wiki/Defensive_programming), and security recommendations.[[4]](https://en.wikipedia.org/wiki/SonarQube#cite_note-methodsandtools-4)[[5]](https://en.wikipedia.org/wiki/SonarQube#cite_note-sonarinaction-5)
    

- **K8sLens**, or simply **Lens**, is a popular open-source Kubernetes IDE that simplifies the management and monitoring of Kubernetes clusters. It provides a graphical interface to view, analyze, and troubleshoot your clusters, workloads, and other Kubernetes resources in a centralized and user-friendly way.
    
    ---
    
    ### **Features of K8sLens**
    
    1. **Cluster Management**:
        - Supports multiple Kubernetes clusters, allowing you to connect and switch between them easily.
        - Provides details about cluster nodes, resources, and configurations.
    2. **Resource Visualization**:
        - Displays live resource status, including Pods, Deployments, Services, ConfigMaps, Secrets, and more.
        - Offers detailed resource views, logs, and YAML configurations.
    3. **Built-in Terminal**:
        - Integrated terminal with `kubectl` preconfigured for the connected cluster.
        - You can run commands directly without additional setup.
    4. **Workload Monitoring**:
        - Provides real-time insights into workloads and their health.
        - Visualizes metrics, events, and logs.
    5. **Access Control**:
        - Allows users to interact with Kubernetes RBAC policies.
        - Facilitates role-based access management across different clusters.
    6. **Extensions**:
        - Lens supports extensions to enhance its functionality, including tools for observability, security, and more.
    
    ---
    
    ### **How to Install K8sLens**
    
    1. **Download Lens**:
        - Visit the [Lens official website](https://k8slens.dev/) to download the version for your operating system (Windows, macOS, or Linux).
    2. **Install Lens**:
        - Follow the installation steps for your OS (e.g., running the installer on Windows or using the `.AppImage` on Linux).
    3. **Connect a Cluster**:
        - After installation, open Lens and click **Add Cluster**.
        - Provide the kubeconfig file for your Kubernetes cluster. Lens will use this to connect.

### Resources:

- OVH:
OVH, legally OVH Groupe SA, is a French **cloud computing company** which offers VPS, dedicated servers and other web services. As of 2016 OVH owned the world's largest data center in surface area. As of 2019, it was the largest hosting provider in Europe, and the third largest in the world based on physical servers # Good policies for privacy
- osintframework.com
This is a website with osint tools catogerized in a neat format.
- oboxes
this is a site where they have ready made vms for vbox and vmware
- Exploitdb
Google’s database , main thing is to regularly check and read from there
- SwagLabs
saucedemo.com 
This is a web for testing
- admin-demo.nopcommerce.com
This is a website for testing
- [flaws.cloud](http://flaws.cloud) 
a ctf for learning cloud pentesting

> [https://coggle.it/diagram/YEO2fKW-ygmKbaL9/t/sysops-prime](https://coggle.it/diagram/YEO2fKW-ygmKbaL9/t/sysops-prime)
Diagram For Rhel
> 

# VA:

### Tools:

- **Masscan** is a high-performance network port scanner designed for rapid exploration of large IP ranges. It's renowned for its incredible speed, capable of scanning the entire internet in under six minutes.
- **Maltego**
Open-source intelligence and data visualization tool. Used for link analysis, entity extraction, and investigation.
- **Harvester** 
is a command-line tool designed for gathering information from public sources. It collects data like email addresses, subdomains, employees, and more from search engines, PKP keys, and Shodan.
- **Recon-ng** 
is a powerful, Python-based reconnaissance framework offering a wide range of modules for gathering information. It features a database for storing collected data, interactive help, and a modular structure for customization.
- **Nmap**
Network discovery, port scanning, OS detection, security auditing.
    
    **Explanation of Port Results
    Open**: The port is open and there is an application listening on it.
    **Closed**: The port is closed and there is no application listening on it.
    **Filtered**: The port is being filtered by a firewall or other network device and cannot be determined if it is open or closed.
    **Basic Syntax**
    `nmap [options] {target}`
    **Commonly Used Options and Commands**
    
    - **`-A`**: This is used to enable OS detection, version detection, script scanning, and traceroute in a single command. It provides detailed information about the target.
    - **`--script=default` OR `nmap -sC <ip>`**: This option runs the default set of scripts. These scripts include, but are not limited to:
    - **`D`**: This option is used for decoy scanning. It makes the scan appear to come from multiple IP addresses. 
    Example: `nmap -D RND:10 192.168.1.1`
    - **`S`**: This option specifies a spoofed source address.
    Example: `nmap -S 192.168.1.2 192.168.1.1`
    This makes the scan appear as if it is coming from 192.168.1.2.
    - **`f`**: This option fragments the packets, making it harder for firewalls to detect the scan.
    Example: `nmap -f 192.168.1.1`
    - `-g`: This command is used to spoof the destination port
    - **`sP`**: Ping scan, used to determine which hosts are up.
    Example: `nmap -sP scanme.nmap.org`
    - **`sS`**: SYN scan, the default and most popular scan option, less likely to be logged by firewalls.
    Example: `nmap -sS 192.168.1.1`
    - **`sU`**: UDP scan, used to scan for open UDP ports.
    Example: `nmap -sU 192.168.1.1`
    - **`sV`**: Service version detection, used to determine the version of services running on open ports.
    Example: `nmap -sV 192.168.1.1`
    - **`O`**: OS detection, used to determine the operating system of the target.
    Example: `nmap -O 192.168.1.1`
    - **`A**:` Aggressive scan, enables OS detection, version detection, script scanning, and traceroute.
    Example: `nmap -A 192.168.1.1`
    - **`p`**: Port selection, used to specify which ports to scan.
    Example: `nmap -p 22,80,443 192.168.1.1`
    - **`T`**: Timing template, used to adjust the timing of the scan (e.g., -T4 for faster scans).
    Example: `nmap -T4 192.168.1.1`
    - **`Pn`**: Treat all hosts as online, skip host discovery.
    Example: `nmap -Pn 192.168.1.1`
    - **`-script`**: Specifies a script to run during the scan.
    Example: `nmap --script=vuln 192.168.1.1`
    - **`oN`**: Output scan in normal format.
    Example: `nmap -oN output.txt 192.168.1.1`
    - **`oX`**: Output scan in XML format.
    Example: `nmap -oX output.xml 192.168.1.1`

- **ZAP** is a free and open-source web application security scanner. It helps find vulnerabilities in web applications and is designed for use by people with a wide range of security experience.
OWASP ZAP (Zed Attack Proxy)

### Resources:

- **Shodan**
Search engine for internet-connected devices. Discovers devices, services, and vulnerabilities by searching service banners.
- **Spyse**
is an OSINT platform that provides comprehensive information about websites, domains, and IP addresses. It offers tools for investigating online entities, gathering intelligence, and analyzing digital footprints.
- vulners
Vulnerability database enriched with millions CVE, exploits, articles, varied tools and services for vulnerability management against cybersecurity threats.  also has security news
- dnsdumpster
this is an online resource for enumerating sub-domains

# Hacking 101 & Incident Response + Network Pentesting:

## Tools:

- **GRR Rapid Response** 
is an incident response framework focused on remote live forensics. It involves a Python client (agent) installed on target systems and a Python server infrastructure to manage and communicate with these clients. GRR is used for collecting digital artifacts, performing live analysis, and investigating security incidents.

- **Rekall**
is a powerful, open-source framework for memory forensics. It allows analysts to extract and analyze digital artifacts from computer memory images. Rekall provides a flexible platform for developing custom plugins and scripts, enabling tailored investigations.

- **Netstat** (network statistics)
is a command-line tool that displays network connections (both incoming and outgoing), routing tables,
and various network interface and protocol statistics. It's invaluable for troubleshooting network issues, monitoring network activity, and understanding how a system is communicating over a network.
    - **`a`**: Displays all active connections and the listening ports.
        - Example: `netstat -a`
        - This shows all the connections that are currently active as well as the ports that are being listened to by the system.
    - **`t`**: Displays TCP connections.
        - Example: `netstat -t`
        - This shows only TCP connections.
    - **`u`**: Displays UDP connections.
        - Example: `netstat -u`
        - This shows only UDP connections.
    - **`l`**: Displays only listening ports.
        - Example: `netstat -l`
        - This shows all the ports that are listening for incoming connections.
    - **`n`**: Displays addresses and port numbers in numerical form.
        - Example: `netstat -n`
        - This shows IP addresses and port numbers instead of resolving them to hostnames and service names.
    - **`p`**: Displays the process ID (PID) and program name associated with each connection.
        - Example: `netstat -p`
        - This shows which processes are using which connections.
    - **`r`**: Displays the routing table.
        - Example: `netstat -r`
        - This shows the system's routing table, which tells how network traffic is directed.
    - **`i`**: Displays network interface statistics.
        - Example: `netstat -i`
        - This shows statistics for each network interface on the system.
    - **`s`**: Displays summary statistics for each protocol.
        - Example: `netstat -s`
        - This shows detailed statistics for each protocol, including packets sent and received, errors, and more.

### **Cmd Commands**

hostname = gives us the computer name running the shell # another way is echo %username%

whoami = to get the user name of the shell

whoami /priv = gives the privilages of the user

systeminfo = gives us a bunch of info about the computer

net users = to get all the users

net users <username> = to get more info about the user

net share =  It can be used to create, delete, modify, or display shared resources.

ipconfig /all = shows more info about the network

netsh =  to view and configure settings for network interfaces, such as IP addresses, subnet masks, default gateways, and DNS servers.

/? = show the info about the command # dir /? this will show the use and parameters for dir

netstat -ano = is a command that displays all active TCP connections and the TCP and UDP ports on which the computer is listening. It also shows the process ID (PID) of the process that created each connection or listening port.

WMIC = can be used to query for information about the operating system, hardware, software, and other resources. It can also be used to perform actions such as starting and stopping services, managing processes, and configuring devices.

list /format = to get the format in neet form

at = it is used to schedule a command, a script, or a program to run at a specified date and time. You can also use this command to view existing scheduled tasks.

netsh wlan show profile "network name" key=clear = to get the wifi password 

dir /a = shows a little more hidden files # in forensics to get more use tools like FTK Imager and KAPE  

attrib * = also used to show files and hidden files 

- **SpiderFoot** 
is an open-source intelligence (OSINT) automation tool designed to gather information about a target entity. It automates the process of querying multiple public data sources to build a comprehensive profile of the target.

- **Kansa** 
is a versatile, open-source, PowerShell-based incident response framework designed to efficiently collect and analyze data across multiple systems. It's a valuable tool for organizations to respond to security incidents effectively.

- **Foca**
A Tool for Metadata Analysis
**FOCA** is an open-source tool used to extract metadata and hidden information from documents.
It's primarily used in digital forensics and security investigations to uncover potential vulnerabilities and insights.

- **SearchDiggity** 
is a tool specifically designed for **Google Hacking Or Dorking**. It's part of the larger **Google Hacking Diggity Project**.

- **Zwardial: A Zoom Meeting Brute-forcer
zWarDial** is a tool specifically designed to **find unprotected Zoom meetings**. It exploits a vulnerability in Zoom's system where meetings can be accessed without a password if the meeting ID is known.
    
    How it works:
    
    Generates random meeting IDs: Zwardial creates a large number of random Zoom meeting IDs.
    
    Attempts to join meetings: It tries to join each generated meeting ID to see if it's accessible.
    
    Identifies unprotected meetings: If a meeting can be joined without a password, Zwardial reports the meeting ID.
    

- **WarVOX** 
is a suite of tools for exploring, classifying, and auditing telephone systems. Unlike normalwardialing tools, it works with the actual audio from each call and does not use a modem directly. This model allows the tool to find and classify a wide range of interesting lines, including modems, faxes, voice mail boxes, PBXs, loops, dial tones, IVRs, and forwarders. It provides the unique ability to classify all telephone lines in a given range, not just those connected to modems, allowing for acomprehensive audit of a telephone system.

- **InSSIDer** is a powerful Wi-Fi analysis tool designed to help you understand and optimize your wireless network environment. It provides valuable insights into the performance and security of your Wi-Fi network and those around you.
    
    Key features of InSSIDer:
    
    - **Visualizes Wi-Fi networks:** Displays a graphical representation of nearby Wi-Fi networks, including signal strength, channel, and security type.
    - **Identifies channel interference:** Helps you select the best Wi-Fi channel to avoid congestion and improve performance.
    - **Detects hidden networks:** Uncovers wireless networks that are not broadcasting their SSID (network name).
    - **Measures signal strength:** Shows you the strength of your Wi-Fi signal in different locations.
    - **Provides network details:** Displays information about each wireless network, including BSSID, MAC address, and encryption type.

- **Kismet** is a powerful, open-source tool for detecting wireless networks and devices. It functions as a network detector, packet sniffer, and intrusion detection system (IDS) for 802.11 wireless LANs.
    
    Key features of Kismet:
    
    - **Network detection:** Identifies both active and hidden wireless networks.
    - **Packet sniffing:** Captures and analyzes wireless traffic.
    - **Intrusion detection:** Monitors for suspicious network activity and potential threats.
    - **Versatility:** Works with a variety of wireless interfaces and can detect multiple wireless technologies beyond Wi-Fi.
    - **Flexibility:** Can be used in both passive and active modes.

- Netcat (nc) 
**Netcat**, often abbreviated as `nc`, is a versatile networking utility used for reading from and writing to network connections using TCP or UDP. It can be used for a variety of tasks, including port scanning, banner grabbing, file transfer, and even acting as a simple chat server or client.
    
    Common Uses and Options
    
    - **Port Scanning**:
        - **`nc -z -v <host> <port-range>`**: Scans the specified range of ports on a target host.
            - Example: `nc -z -v 192.168.1.1 20-80`
            - This scans ports 20 through 80 on the host 192.168.1.1.
    - **Listening on a Port**:
        - **`nc -l -p <port>`**: Listens on the specified port for incoming connections.
            - Example: `nc -l -p 1234`
            - This sets up a listener on port 1234, waiting for connections.
    - **Connecting to a Port**:
        - **`nc <host> <port>`**: Connects to a specified host on a specified port.
            - Example: `nc 192.168.1.1 1234`
            - This connects to port 1234 on the host 192.168.1.1.
    - **Transferring Files**:
        - **On the Receiving Side**: `nc -l -p <port> > received_file`
        - **On the Sending Side**: `nc <host> <port> < file_to_send`
            - Example:
                - Receiver: `nc -l -p 1234 > file.txt`
                - Sender: `nc 192.168.1.1 1234 < file.txt`
                - This transfers `file.txt` from the sender to the receiver.
    - **Simple Chat**:
        - **On Machine A**: `nc -l -p 1234`
        - **On Machine B**: `nc <Machine_A_IP> 1234`
            - Example: Start a chat between two machines on port 1234.
    - **Banner Grabbing**:
        - **`nc <host> <port>`**: Connect to a service to grab its banner.
            - Example: `nc example.com 80`
            - After connecting, type `HEAD / HTTP/1.0` and press Enter twice to see the web server's response.

- GTFOBins    -  Privilege escalation
https://gtfobins.github.io/
***GTFOBins*** is a curated list of Unix binaries that can be used to bypass local security restrictions in misconfigured systems

# WSTG:

### Resources:

- **Google + Dorking
Definition**: Google Dorking uses advanced search operators to find specific information that is not readily accessible. It can help locate vulnerable websites, sensitive data, or specific file types.
**Example**: Using `site:example.com filetype:pdf` to find all PDFs on a specific site.
Here are some important and useful Google Dorks:
    - **`site:`**: Limits the search to a specific website.
        - **Example**: `site:example.com` (Searches only within example.com).
    - **`filetype:`**: Searches for specific file types.
        - **Example**: `filetype:pdf site:example.com` (Finds PDF files on example.com).
    - **`intitle:`**: Finds pages with a specific word in the title.
        - **Example**: `intitle:login` (Finds pages with "login" in the title).
    - **`inurl:`**: Searches for URLs containing a specific word.
        - **Example**: `inurl:admin` (Finds URLs with "admin" in them).
    - **`cache:`**: Views Google's cached version of a page.
        - **Example**: `cache:example.com` (Shows Google's cached version of example.com).
    - **`allintext:`**: Finds pages with all the specified words in the text.
        - **Example**: `allintext:password filetype:log` (Finds log files with the word "password").
    - **`allintitle:`**: Searches for pages with all the specified words in the title.
        - **Example**: `allintitle:secure login` (Finds pages with both "secure" and "login" in the title).
    - **`inanchor:`**: Searches for text in the anchor (link) text.
        - **Example**: `inanchor:"click here"` (Finds pages where the link text is "click here").
    - **`link:`**: Finds pages that link to a specific URL.
        - **Example**: `link:example.com` (Finds pages linking to example.com).
    - **`related:`**: Finds sites similar to the specified URL.
        - **Example**: `related:example.com` (Finds sites similar to example.com).
    - **`info:`**: Provides information about a specific URL.
        - **Example**: `info:example.com` (Displays information about example.com).
    - **`password ext:txt OR ext:log OR ext:cfg`**: Searches for files that might contain passwords in text, log, or configuration files.
        - **Example**: `password ext:txt OR ext:log OR ext:cfg` (Finds files that might contain passwords).
    - **`index of`**: Finds directory listings that may contain files of interest.
        - **Example**: `index of /admin` (Finds directories named "admin" that might contain sensitive information).
    - To use multiple Google dorks in one search, you can simply combine them with logical operators like **`AND`**, **`OR`**, or **`-`** (for NOT). Here's how you can do it:
        - **Combining Dorks with AND**: By default, Google assumes an **`AND`** between search terms.
            - **Example**: `site:example.com filetype:pdf` (Searches for PDF files on example.com).
        - **Combining Dorks with OR**: Use **`OR`** to search for either of the terms.
            - **Example**: `site:example.com OR site:anotherexample.com filetype:pdf` (Finds PDFs on either example.com or anotherexample.com).
        - **Combining Dorks with NOT**: Use  before a term to exclude it from search results.
            - **Example**: `site:example.com filetype:pdf -intitle:report` (Finds PDFs on example.com but excludes those with "report" in the title).
        - **Grouping with Parentheses**: You can group dorks together using parentheses to control the logic.
            - **Example**: `(site:example.com OR site:anotherexample.com) filetype:pdf` (Finds PDFs on either example.com or anotherexample.com).
    
- **DuckDuckGo
Definition**: A privacy-focused search engine that doesn't track users. It’s useful for anonymous web searches without being targeted by ads based on your search history.
**Example**: Searching for topics without worrying about personalized search results.
- **Baidu
Definition**: The leading search engine in China, known for indexing Chinese web content. It’s useful for finding information within the Chinese internet ecosystem.
**Example**: Researching trends or content that is popular in China.
- **Yandex
Definition**: The most popular search engine in Russia, offering search capabilities in Russian and other languages. It’s often used for accessing content more relevant to Russian-speaking users.
**Example**: Finding Russian-language sites or regional data.
- **Shodan
Definition**: A search engine for Internet-connected devices, including servers, webcams, routers, and more. It’s commonly used by security professionals to discover vulnerable devices.
**Example**: Searching for IoT devices with default credentials or outdated software.
- **Internet Archive + Wayback Machine
Definition**: A digital archive of the internet, allowing users to view archived versions of web pages. It’s useful for seeing how websites looked in the past or retrieving content that’s been removed.
**Example**: Accessing a website's content from years ago to check for changes or recover lost information.
- https://sitereport.netcraft.com
This is an online resou for web fingerprinting
- viewdns.info
this is a site with many recon option for webs

### Tools:

- **CURL (Client URL)** 
is a command-line tool used to transfer data to or from a server, using various protocols such as HTTP, HTTPS, FTP, and more. It is widely used for testing and interacting with web applications, APIs, and other online resources.
    
    **Basic Usage**:
    
    - **GET Request**: Fetches a web page or API data.
        - **Example**: `curl https://example.com`
    - **POST Request**: Sends data to a server, often used with APIs.
        - **Example**: `curl -X POST -d "key1=value1&key2=value2" https://example.com/api`
    - **Saving Output to a File**: Downloads content and saves it locally.
        - **Example**: `curl -o filename.html https://example.com`
    - **Adding Headers**: Custom headers can be included in the request.
        - **Example**: `curl -H "Authorization: Bearer token" https://example.com/api`
    - **`I`**: Fetches the HTTP headers only, without the body of the response.
    Example: `curl -I http://example.com` # can be used for web fingerprinting

- **Nikto** is an open-source web server scanner that performs comprehensive tests against web servers to find vulnerabilities, security issues, and misconfigurations. It scans for various vulnerabilities such as outdated software, dangerous files, and potential security issues.
**Common Nikto Options and Flags**
    - **`h`**: Specifies the target host to scan.
        - Example: `nikto -h http://example.com`
        - This sets the target host for the scan. Replace `http://example.com` with the URL or IP address of the web server you want to scan.
    - **`p`**: Specifies a port to scan, if different from the default HTTP/HTTPS ports (80/443).
        - Example: `nikto -h http://example.com -p 8080`
        - This scans the specified port (8080) on the target host.
    - **`T`**: Specifies the number of concurrent threads for scanning.
        - Example: `nikto -h http://example.com -T 10`
        - This uses 10 threads for scanning, which can speed up the process.
    - **`e`**: Includes a specific test or set of tests to perform.
        - Example: `nikto -h http://example.com -e xss`
        - This includes tests for cross-site scripting (XSS) vulnerabilities.
    - **`C`**: Specifies the configuration file to use for custom settings.
        - Example: `nikto -h http://example.com -C /path/to/config_file`
        - This uses the specified configuration file for the scan.
    - **`o`**: Specifies the output file for the scan results.
        - Example: `nikto -h http://example.com -o output.txt`
        - This saves the scan results to `output.txt`.
    - **`ShowCode`**: Displays the HTTP status codes in the output.
        - Example: `nikto -h http://example.com -ShowCode`
        - This shows the HTTP status codes for each test performed.
    - **`v`**: Enables verbose output, providing more detailed information during the scan.
        - Example: `nikto -h http://example.com -v`
        - This increases the verbosity of the output.

- **Whois** is a command-line tool used to query and retrieve information about domain names, IP addresses, and autonomous systems from the Whois database. It provides details such as domain ownership, registration dates, contact information, and more.

- **ffuf** (Fuzz Faster U Fool) 
is a fast and flexible web fuzzer designed for discovering hidden resources, endpoints, and files on web servers. It is particularly useful in security assessments and penetration testing for finding potential vulnerabilities and misconfigurations.
Example: `ffuf -u http://example.com/FUZZ -w /path/to/wordlist.txt -o results.txt`

- sslscan
a tool for ssl enumeration