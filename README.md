# DNSMAP
Thinking...
> 
> Alright, the user is asking about Dnsmap, another Kali tool, after previously inquiring about Dnsenum. Let me recall what I know about Dnsmap. It's used for subdomain brute-forcing, similar to some features in Dnsenum but perhaps simpler or more focused on that specific task.
> 
> First, I need to explain what Dnsmap does. It's a tool designed to discover subdomains by brute-forcing using a wordlist. The primary function is to find hidden or non-obvious subdomains. Unlike Dnsenum, which does more comprehensive DNS enumeration, Dnsmap is specialized in subdomain brute-forcing.
> 
> Installation: Even though Kali comes with many tools pre-installed, it's possible Dnsmap isn't included by default. I should check and mention the installation command. From what I remember, it's available in the Kali repos, so 'sudo apt install dnsmap' would work.
> 
> Basic usage would involve running dnsmap followed by the target domain. The simplest example is 'dnsmap example.com'. But they might also want to use a custom wordlist, specify output files, or adjust the wait time between requests to avoid detection.
> 
> Common options include -w for specifying a wordlist, -r to save results to a file, and -t to set a delay between queries. The built-in wordlist is probably in /usr/share/dnsmap/wordlist_TLAs.txt or similar, but users can provide their own.
> 
> Examples: The user wants examples. So a basic scan, one with a custom wordlist, delayed requests, and output to a file. Also, maybe an example of using the internal wordlist if no external one is specified.
> 
> Output: When run, Dnsmap shows discovered subdomains along with their IP addresses. If using a custom wordlist, it might find more subdomains. The output file would list these in a structured format.
> 
> Potential mistakes: Users might forget to specify a wordlist if they intend to use one, or not realize the default wordlist is limited. Also, not using a delay (-t) might lead to aggressive scanning that could be detected.
> 
> Ethical considerations again: Emphasize that unauthorized scanning is illegal. Dnsmap is for legitimate security assessments.
> 
> Troubleshooting: If the command isn't found, install dnsmap. If no subdomains are found, maybe the wordlist is too small or the domain has strong protections.
> 
> Sample output structure: Show the command line execution, each subdomain found with its IP, and the completion message.
> 
> Need to differentiate Dnsmap from Dnsenum. While both do subdomain brute-forcing, Dnsmap is more focused on that single task, whereas Dnsenum does broader DNS enumeration (MX records, zone transfers, etc.).
> 
> Also, mention that using a larger wordlist can yield better results but takes longer. Users might want to use tools like amass or sublist3r in conjunction for more comprehensive results.
> 
> Finally, wrap it up in a clear, structured format with examples and outputs as before. Make sure the commands are accurate and the explanations are concise.
> 


**Dnsmap** is a subdomain brute-forcing tool in Kali Linux designed to discover hidden subdomains of a target domain using wordlists. Below is a guide on its usage, examples, and sample outputs.

---

### **Installation**
Dnsmap is pre-installed in Kali Linux. If missing, install it with:
```bash
sudo apt update && sudo apt install dnsmap
```

---

### **Basic Syntax**
```bash
dnsmap <target-domain> [options]
```

---

### **Common Options**
| Option          | Description                                                                 |
|-----------------|-----------------------------------------------------------------------------|
| `-w <file>`     | Use a custom wordlist (default: built-in list).                             |
| `-r <file>`     | Save results to a file.                                                    |
| `-t <ms>`       | Set delay (in milliseconds) between requests to avoid detection.          |
| `-i <ip>`       | Ignore IPs (e.g., to skip false positives).                                |
| `--ip`          | Show IP addresses of discovered subdomains.                               |

---

### **Examples**

#### **1. Basic Subdomain Brute-Forcing**
```bash
dnsmap example.com
```
**Output**:
```
dnsmap 0.36 - DNS Network Mapper by pagvac (gnucitizen.org)

[+] Searching for subdomains in example.com using built-in wordlist
[+] Sorting results by IP address...

[+] 10 subdomains found:

www.example.com
IP address #1: 93.184.216.34

mail.example.com
IP address #1: 93.184.216.35

ftp.example.com
IP address #1: 93.184.216.36

... (truncated)
```

---

#### **2. Use a Custom Wordlist**
```bash
dnsmap example.com -w /usr/share/wordlists/subdomains-top1mil.txt -r results.txt
```
**Explanation**:
- `-w`: Specifies a custom wordlist (e.g., `subdomains-top1mil.txt`).
- `-r`: Saves results to `results.txt`.

---

#### **3. Add Delay Between Requests**
Slow down scanning to evade detection:
```bash
dnsmap example.com -t 500
```
**Explanation**:
- `-t 500`: Adds a 500ms delay between requests.

---

#### **4. Filter Out Specific IPs**
Ignore results resolving to `192.168.1.1`:
```bash
dnsmap example.com -i 192.168.1.1
```

---

### **Sample Output File (results.txt)**
The `-r` flag generates a file like:
```
www.example.com (93.184.216.34)
mail.example.com (93.184.216.35)
ftp.example.com (93.184.216.36)
...
```

---

### **Key Features**
- **Subdomain Discovery**: Brute-forces subdomains using wordlists.
- **Flexible Wordlists**: Supports custom wordlists for targeted scans.
- **Stealth Mode**: Adjustable delays (`-t`) to avoid triggering alarms.

---

### **Ethical Note**
- Only use Dnsmap on domains you own or have explicit permission to scan.
- Unauthorized subdomain enumeration may violate laws or policies.

---

### **Troubleshooting**
- **No Subdomains Found?** Try a larger wordlist (e.g., `subdomains-top1mil.txt`).
- **Command Not Found?** Install Dnsmap with `sudo apt install dnsmap`.
- **False Positives?** Use `-i` to ignore specific IPs.

---

### **Comparison with Dnsenum**
- **Dnsmap**: Focused on subdomain brute-forcing with wordlists.
- **Dnsenum**: Broader DNS enumeration (MX records, zone transfers, etc.).

---

For comprehensive subdomain discovery, combine Dnsmap with tools like **Amass** or **Sublist3r**.
                        ALTERNATIVE
`dnsmap` is a tool used for DNS enumeration and brute-forcing subdomains. It helps in gathering information about a target domain by discovering subdomains. Here's a brief overview of common `dnsmap` commands and examples:

### Installation
If `dnsmap` is not already installed on your Kali Linux, you can install it using:

```bash
sudo apt-get install dnsmap
```

### Basic Usage
The general syntax for using `dnsmap` is:

```bash
dnsmap [options] <domain>
```

### Common Commands and Examples

1. **Basic Subdomain Enumeration**
   To enumerate subdomains of a domain, use:

   ```bash
   dnsmap example.com
   ```

2. **Using a Custom Wordlist**
   If you have a custom wordlist, specify it with the `-w` option:

   ```bash
   dnsmap -w /path/to/wordlist.txt example.com
   ```

3. **Verbose Output**
   For more detailed information during the scan, use the `-v` option:

   ```bash
   dnsmap -v example.com
   ```

4. **Specify DNS Server**
   To use a specific DNS server for the queries, use the `-r` option:

   ```bash
   dnsmap -r 8.8.8.8 example.com
   ```

5. **Output to a File**
   To save the results to a file, use the `-o` option:

   ```bash
   dnsmap -o output.txt example.com
   ```

6. **Brute-Force Mode**
   To enable brute-forcing, you can set a timeout with the `-t` option (timeout in seconds):

   ```bash
   dnsmap -t 2 -w /path/to/wordlist.txt example.com
   ```

### Example Scenarios

- **Finding Subdomains with Default Wordlist:**
  ```bash
  dnsmap example.com
  ```

- **Using a Custom Wordlist and Saving Results:**
  ```bash
  dnsmap -w /usr/share/wordlists/dirb/common.txt -o results.txt example.com
  ```

### Summary
`dnsmap` is a versatile tool for DNS enumeration. Using the options effectively allows you to customize the scan according to your needs. Always ensure you have permission to perform such scans on the target domain.


                                 ALTERNATIVE
`dnsmap` is a DNS enumeration tool used for discovering subdomains and other DNS-related information. Here are some commands and examples on how to use `dnsmap` in Kali Linux:

### Installation

If `dnsmap` is not installed, you can install it via the package manager:

```bash
sudo apt update
sudo apt install dnsmap
```

### Basic Usage

The basic syntax for `dnsmap` is:

```bash
dnsmap [options] <domain>
```

### Common Commands and Examples

1. **Simple Subdomain Enumeration**

   To enumerate subdomains for a domain:

   ```bash
   dnsmap example.com
   ```

2. **Using a Custom Wordlist**

   To use a custom wordlist for subdomain enumeration:

   ```bash
   dnsmap -w /path/to/your/wordlist.txt example.com
   ```

3. **Specifying DNS Server**

   To specify a DNS server to query:

   ```bash
   dnsmap -s 8.8.8.8 example.com
   ```

4. **Saving Output to a File**

   To save the results to a file:

   ```bash
   dnsmap example.com -o output.txt
   ```

5. **Verbose Output**

   For more detailed output, you can use the verbose option:

   ```bash
   dnsmap -v example.com
   ```

### Example

Here’s a complete example where you enumerate subdomains for `example.com`, use a custom wordlist, specify a DNS server, and save the output:

```bash
dnsmap -w /path/to/wordlist.txt -s 8.8.8.8 example.com -o results.txt -v
```

### Conclusion

`dnsmap` is a powerful tool for DNS enumeration. Make sure to use it responsibly and only on domains you have permission to test.


                                  ALTERNATIVE
  DNSMap is a DNS reconnaissance tool that can be used to gather information about a target domain's DNS infrastructure. Here are some common DNSMap commands and examples on Kali Linux:

**Basic Usage**

`dnsmap <domain_name>`

Example: `dnsmap google.com`

This command will perform a basic DNS reconnaissance on the specified domain, including resolving the domain to IP addresses, identifying mail servers, and detecting potential subdomains.

**Options**

* `-r` or `--recursive`: Perform a recursive DNS scan, which can help identify more subdomains.

Example: `dnsmap -r google.com`

* `-s` or `--subdomains`: Only scan for subdomains, without performing a full DNS reconnaissance.

Example: `dnsmap -s google.com`

* `-m` or `--mx`: Only scan for mail servers (MX records).

Example: `dnsmap -m google.com`

* `-n` or `--no- recursion`: Disable recursive DNS scanning.

Example: `dnsmap -n google.com`

* `-t` or `--threads`: Specify the number of threads to use for the scan.

Example: `dnsmap -t 10 google.com`

* `-o` or `--output`: Save the output to a file.

Example: `dnsmap google.com -o output.txt`

**Advanced Usage**

* `dnsmap -r -s -m google.com`: Perform a recursive DNS scan, scan for subdomains, and identify mail servers.
* `dnsmap -n -t 5 google.com`: Perform a non-recursive DNS scan, using 5 threads.
* `dnsmap -o output.txt google.com`: Save the output to a file named "output.txt".

**Other Examples**

* `dnsmap -r -s -m -t 10 google.com`: Perform a comprehensive DNS reconnaissance on google.com, using 10 threads.
* `dnsmap -n -s -m microsoft.com`: Perform a non-recursive DNS scan on microsoft.com, scanning for subdomains and mail servers.

**Tips and Tricks**

* Use the `-r` option carefully, as it can generate a large amount of traffic and may cause issues with the target domain.
* Use the `-t` option to adjust the number of threads according to your system's resources and the target domain's size.
* Use the `-o` option to save the output for later analysis or to use as input for other tools.
* DNSMap can be used in conjunction with other tools, such as Nmap or Dig, to gather more comprehensive information about a target domain.

Remember to always use DNSMap and other reconnaissance tools in a legal and ethical manner, and to respect the target domain's privacy and security.



                                              ALTERNATIVE
DNSmap is a tool used in Kali Linux for subdomain enumeration, primarily used by pentesters during the information gathering phase. It works by brute-forcing subdomains using a built-in wordlist or a user-supplied wordlist.

Here's a breakdown of common `dnsmap` commands and examples:

**Basic Usage**

*   **`dnsmap <target-domain>`**: This command uses dnsmap's built-in wordlist to find subdomains for the specified target domain. For example: `dnsmap targetdomain.foo`

**Options**

*   **`-w <wordlist-file>`**:  Specifies a custom wordlist file to use for brute-forcing. If you don't provide this option, DNSMAP will use the default file. Example: `dnsmap targetdomain.foo -w wordlist.txt`
*   **`-r <regular-results-file>`**: Saves the results to a text file. If you only provide a path, dnsmap will create a unique filename with a timestamp. Example: `dnsmap targetdomain.foo -r /tmp/`
*   **`-c <csv-results-file>`**: Saves the results in CSV format. Example: `dnsmap targetdomain.foo -c /tmp/results.csv`
*   **`-d <delay-millisecs>`**:  Sets a delay in milliseconds between DNS requests. This can be useful to avoid interfering with your own internet connection or to avoid triggering rate limiting on the target's DNS servers. The delay value is a *maximum* random value. Example: `dnsmap targetdomain.foo -d 300` (sets a maximum delay of 0.3 seconds).
*   **`-i <ips-to-ignore>`**:  Filters out false positives by ignoring specific IP addresses.  Example: `dnsmap targetdomain.foo -i 10.55.206.154,10.55.24.100`

**Examples**

*   **Subdomain bruteforcing using a user-supplied wordlist and saving the results:**

    `dnsmap targetdomain.foo -w wordlist.txt -r /tmp/domainbf_results.txt`
*   **Subdomain bruteforcing with a delay, saving results in regular and CSV format, filtering IPs, and using a user-supplied wordlist:**

    `dnsmap targetdomain.foo -d 800 -r /tmp/ -c /tmp/ -i 10.55.206.154,10.55.24.100 -w ./wordlist_TLAs.txt`

**Important Notes**

*   `dnsmap` is intended for use during the information gathering/enumeration phase of security assessments.
*   It's a good practice to use the `-d` option to add delays between requests, especially if you experience bandwidth issues.
*   Be aware that `dnsmap` relies on brute-forcing, so it may produce false positives if the target domain uses wildcards.


---
![server_inject_icon](https://pfst.cf2.poecdn.net/base/image/0e8698a6e80a985ec6d5f4d175c17866cee4b502ac78ccea3d02bb90fdca0b9f?w=100&h=33)
Related searches:
+ [dnsmap kali commands](https://www.google.com/search?q=dnsmap+kali+commands&client=app-vertex-grounding-quora-poe)
+ [dnsmap kali examples](https://www.google.com/search?q=dnsmap+kali+examples&client=app-vertex-grounding-quora-poe)




                                             ALTERNATIVES
The `dnsmap` tool is a DNS enumeration and network reconnaissance tool that can be used to gather information about a target domain. Here are some common `dnsmap` commands and examples on Kali Linux:

1. **Perform a basic DNS enumeration**:
   ```
   dnsmap target.com
   ```
   This command will perform a basic DNS enumeration on the target domain `target.com`.

2. **Specify a wordlist for subdomain discovery**:
   ```
   dnsmap target.com -w /path/to/wordlist.txt
   ```
   This command will use the specified wordlist (`/path/to/wordlist.txt`) to perform subdomain discovery on the target domain.

3. **Enable verbose output**:
   ```
   dnsmap target.com -v
   ```
   This command will provide more detailed output, including the IP addresses associated with each discovered subdomain.

4. **Perform a zone transfer**:
   ```
   dnsmap target.com -z
   ```
   This command will attempt to perform a zone transfer on the target domain, which can reveal additional information about the domain's DNS configuration.

5. **Specify a custom DNS server**:
   ```
   dnsmap target.com -d 8.8.8.8
   ```
   This command will use the specified DNS server (`8.8.8.8`) instead of the default system DNS server.

6. **Save the results to a file**:
   ```
   dnsmap target.com -o results.txt
   ```
   This command will save the enumeration results to the file `results.txt`.

7. **Bypass robot.txt restrictions**:
   ```
   dnsmap target.com -b
   ```
   This command will bypass the `robots.txt` file, which may otherwise prevent `dnsmap` from accessing certain subdomains.

8. **Perform a brute-force attack on a specific subdomain**:
   ```
   dnsmap target.com -s subdomain.target.com
   ```
   This command will perform a brute-force attack on the specific subdomain `subdomain.target.com`.

These are just a few examples of the `dnsmap` commands you can use on Kali Linux. Remember to use these tools responsibly and only on domains you have permission to test.





                                              

