# offensive-ai-use-cases

## Principles

* Information not publicly available stays private
* Never discuss symbols or code unless you can already find it on the Internet
* There may well be licensing implications to consider with code
* Lab access is critical
* Understanding of threat model and tust boundaries needs to be part of the input
* Cost should be a consideration

## AI will find all the bugs?

1) Is the source code available - LLMs understand the statistical relelation ship between words aka keywords and function calls
2) Is the binary available - LLMs can do the same here (although they may do better if you can decompile it)
3) Have there been many bugs in the past, have they been well documented with reference to internal architecture and APIs - LLMs may well be able to speculate on likely root causes
4) Is the software well documented - LLMs may be able to extrapolate likely attack surfaces and make correlations based on the attack surface and related CWEs
5) Is the service often found on the Internet - popular, open protocols find themselves well documented which may give an LLM a leg up
6) The rest...

## Ideas for how where AI may help in offensive activities

| Sofware type                    | Threat models | OSINT | Red team | Vulnerability scans | Source code reviews | Build reviews | Attack surface | Application testing | Reverse engineering |
|---------------------------------|---------------|-------|----------|---------------------|---------------------|---------------|----------------|---------------------|---------------------|
| Open source                     | X             | X     | X        | X                   | X                   | X             | X              | X                   | X                   |
| Closed source (internet facing) | X             | X     | X        | X                   |                     | X             | X              | X                   | X                   |
| Closed source (common)          | X             | X     |          | X                   |                     | X             | X              |                     |                     |
| Closed source (internal)        | X             |       |          |                     |                     | X             |                |                     |                     |

## Testing types

### Threat models

* Asking about public information should be fine
* Avoid customer specifics beyond what is public

### OSINT

* Asking about public information should be fine
* Avoid customer specifics beyond what is public

### Red team

* Asking about public information should be fine
* Using an AI to develop a tool should be fine as long as you're asking it only to build off public information
* Avoid customer specifics beyond what is public

### Vulnerability scans

* Version meta data should be okay
* Using an AI to develop a tool should be fine as long as you're asking it only to build off public information
* Avoid customer specifics beyond what is public

### Source code reviews

* Putting any not-public code or other artefacts into a LLM is problematic

### Build reviews

* Asking about public information should be fine
* Using an AI to develop a tool should be fine as long as you're asking it only to build off public information
* Putting any not-public code or other artefacts into a LLM is problematic

### Attack surface

* Asking about public information should be fine
* Using an AI to develop a tool should be fine as long as you're asking it only to build off public information
* Avoid customer specifics beyond what is public

### Application testing

* Asking about public information should be fine
* Using an AI to develop a tool should be fine as long as you're asking it only to build off public information
* Putting any not-public code or other artefacts into a LLM is problematic

### Reverse engineering

* Putting any not-public code or other artefacts into a LLM is problematic
