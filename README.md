#### Step 1: Google Dorking

Altoro Mutual wants to ensure that private information that is unavailable on their public website cannot be found by searching the web. 

- For example, Altoro Mutual does not mention their executive remembers on the website. Using Google, can you identify who the Chief Executive Officer?

	The CEO of Altoro Mutal is Karl Fitzgerald.

- How can this information be helpful to an attacker?

	This could be usefull for social enginerring in a phishing attempt. 

#### Step 2: DNS and Domain Discovery

The reconnaissance phase of a penetration test is possibly the most important phase of the engagement. Without a clear understanding of your client's assets, vulnerabilities can go unnoticed and later exploited. 

- Navigate to `centralops.net`. 

- Enter the IP address for `demo.testfire.net` into Domain Dossier and answer the following questions based on the results:

  1. Where is the company located? 

	Testfire is in Sunnyvale, CA 94085

  2. What is the NetRange IP address?  

	The net range is 65.61.137.64 - 65.61.137.127

  3. What is the company they use to store their infrastructure? 

	Rackspace Backbone Engineering (C05762718)

  4. What is the IP address of the DNS server? 

	The DNS IP is 65.61.137.117

#### Step 3: Shodan

Using Shodan and the information gathered from Google Dorking, find any other useful information that can be used in an attack.

- Navigate to [shodan.io](https://www.shodan.io/). 

- Run a scan against the IP address of the DNS server for `demo.testfire.net`. 

  - What open ports and running services did Shodan find? 

	The open ports are 80, 443, and 8080. 
	The running services are Apache Tomcat and Coyote JSP engine (version 1.1)

#### Step 4: Recon-ng

Altoro Mutual is also concerned about cross-site scripting attacks, which can cause havoc on their website. Verify whether or not Altoro Mutual is vulnerable to XSS by completing the following:

- Install the Recon module `xssed`. 
- Set the source to `demo.testfire.net`. 
- Run the module. 

Is Altoro Mutual vulnerable to XSS?

### Step 5: Zenmap

Your client has asked that you help identify any vulnerabilities with their file-sharing server. Using the Metasploitable machine to act as your client's server, complete the following:

- Use Zenmap to run a service scan against the Metasploitable machine. 
  
  - **Bonus:** In the same command, output the results into a new text file named `zenmapscan.txt`. 

    
- Use Zenmap's scripting engine to identify a vulnerability associated with the service running on the 139/445 port from your previous scan.


- Once you have identified this vulnerability, answer the following questions for your client:
  1. What is the vulnerability? 

	The Vunerability is SMB 3 (samba)

  2. Why is it dangerous? 

	This vunerability allows attakcer to uploas a shared library on the server to execute it. 

  3. What are your recommendations for the client to protect their server? 

	 To mitiage block port 445. 
