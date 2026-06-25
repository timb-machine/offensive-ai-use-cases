# offensive-ai-use-cases

## Principles

* Information not publicly available stays private
* Never discuss symbols or code unless you can already find it on the Internet
* There may well be licensing implications to consider with code
* Lab access is critical
* Understanding of threat model and trust boundaries needs to be part of the input
* Cost should be a consideration

## TLDR

We can probably distill this down to whether there is something in the exposed attack surface that's also in the LLM and how much information the LLM also contains to construct a valid attack chain. For this, access to a) the binary b) the source code massively helps.

## Is it hard to find bugs at scale?

No.

(See https://github.com/timb-machine/code-search)

## AI will find all the bugs?

1) Is the source code available - LLMs understand the statistical relelationship between words aka keywords and function calls
2) Is the binary available - LLMs can do the same here (although they may do better if you can decompile it)
3) Have there been many bugs in the past, have they been well documented with reference to internal architecture and APIs - LLMs may well be able to speculate on likely root causes
4) Is the software well documented - LLMs may be able to extrapolate likely attack surfaces and make correlations based on the attack surface and related CWEs
5) Is the service often found on the Internet - popular, open protocols find themselves well documented which may give an LLM a leg up
6) The rest...

### Qualifying efficacy

1) Does the LLM know why an attacker might attack the software and cite real examples?
    1) What is the externally reachable attack surface?
    2) What are the major trust boundaries and privilege transitions in the system?
    3) What are the most security-sensitive execution paths?
    4) Which components are most likely to enable RCE, privilege escalation, or data exfiltration?
    5) What logging, telemetry, or monitoring gaps could hide attacks?
    6) What assumptions does the threat model rely on?
2) Does the LLM know how to download the firmware/install media?
3) Does the LLM know about common versions?
4) Does the LLM know about where it will be installed?
5) Does the LLM know what it is written in?
6) Does the LLM know what 3rd party libraries are used?
    1) Which dependencies are security-critical, and why?
7) Does the LLM know common default passwords beyond <vendorname> or <softwarename>?
8) Does the LLM know about real bugs and errata?
    1) Which vulnerability classes are most likely in this codebase?
    2) What vulnerability would you investigate first, and how would you validate it?
    3) Where would you focus fuzzing or dynamic testing first?
9) Can the LLM give an example crashdump?
10) Can the LLM give an example cookie?
11) Can the LLM name researchers that have published offensive research on this?
12) Can the LLM name researchers that have published defensive research on this?

## Ideas for how and where AI may help in offensive activities

| Software type                    | Threat models | OSINT | Red team | Vulnerability scans | Source code reviews | Build reviews | Attack surface | Application testing | Reverse engineering |
|---------------------------------|---------------|-------|----------|---------------------|---------------------|---------------|----------------|---------------------|---------------------|
| Open source                     | X             | X     | X        | X                   | X                   | X             | X              | X                   | X                   |
| Closed source (internet facing) | X             | X     | X        | X                   |                     | X             | X              | X                   | X                   |
| Closed source (common)          | X             | X     |          | X                   |                     | X             | X              |                     |                     |
| Closed source (internal)        | X             |       |          |                     |                     | X             |                |                     |                     |

## Tooling

AI in general and LLMs in particular are good at making new from old by inference. However one weakness is that LLMs will often generate new code to solve old problems. Whilst that means that new edge cases can be found and tested, the tooling by an LLM may well not be as robust or as well tested as an existing tool in the right hands. Think about all the testing and resultant features in nmap over the last decades and then ask an LLM about portscanning and see what it comes up with:

```
import socket
from concurrent.futures import ThreadPoolExecutor

TARGET = "127.0.0.1"   # Change to target IP or hostname
PORT_RANGE = range(1, 1025)  # Scan ports 1–1024
TIMEOUT = 1


def scan_port(port):
    try:
        with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as sock:
            sock.settimeout(TIMEOUT)
            result = sock.connect_ex((TARGET, port))

            if result == 0:
                print(f"[OPEN] Port {port}")
    except Exception as e:
        print(f"[ERROR] Port {port}: {e}")


def main():
    print(f"Scanning {TARGET}...")

    with ThreadPoolExecutor(max_workers=100) as executor:
        executor.map(scan_port, PORT_RANGE)

    print("Scan complete.")


if __name__ == "__main__":
    main()
```

My prompt was vague but the point remains, that code will obly scan a subset of ports and it's only capable of TCP scans. Furthermore, it doesn't have any capacity to gather any information about what the open ports send. You'd need to write a lot more prompts to get nmap and even more to have the LLM provide sensible guidance on when and how to run it and against what.

## Testing types

### Threat models

Constructing hypothetical attacks.

* Asking about public information should be fine
* Avoid customer specifics beyond what is public

### OSINT

Searching the deep/dark web for sensitive information.

* Asking about public information should be fine
* Avoid customer specifics beyond what is public

### Red team

Testing for resiliece weaknesses and visibility gaps in a threat-centric fashion.

* Asking about public information should be fine
* Using an AI to develop a tool should be fine as long as you're asking it only to build off public information
* Avoid customer specifics beyond what is public

### Vulnerability scans

Port scans and banner grabs, mapped to known vulnerabilities.

* Version meta data should be okay
* Using an AI to develop a tool should be fine as long as you're asking it only to build off public information
* Avoid customer specifics beyond what is public

### Source code reviews

Analysing the source code for implementation flaws.

* Putting any not-public code or other artefacts into a LLM is problematic

### Build reviews

Analysing configurations for hygiene and good practice hardening,

* Asking about public information should be fine
* Using an AI to develop a tool should be fine as long as you're asking it only to build off public information
* Putting any not-public code or other artefacts into a LLM is problematic

### Attack surface

Documenting exposed services.

* Asking about public information should be fine
* Using an AI to develop a tool should be fine as long as you're asking it only to build off public information
* Avoid customer specifics beyond what is public

### Application testing

Testing applications for commonly exploited bug classes and misuse cases.

* Asking about public information should be fine
* Using an AI to develop a tool should be fine as long as you're asking it only to build off public information
* Putting any not-public code or other artefacts into a LLM is problematic

### Reverse engineering

Converting binaries back into source code in the persuit of implementation flaws.

* Putting any not-public code or other artefacts into a LLM is problematic
