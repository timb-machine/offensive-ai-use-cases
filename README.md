# offensive-ai-use-cases

## Principles

* Information not publicly available stays private
* Never discuss symbols or code unless you can already find it on the Internet
* There may well be licensing implications to consider with code

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
* Avoid custome specifics beyond what is public

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
