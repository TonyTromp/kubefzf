# kubefzf

A fuzzyfind (fzf) menu system that replaces or improves most of your daily kubernetes interactions.

## Why
For most using kubernetes comes in the following stages of agony
- using 'kubectl' command while thinking about using linux aliases
- using 'aliases' for kubectl wishing you have more control over the input/output
- writting your own interface, which is what i present here...

## Using it
- Install the common Terminal enhancements: zsh, powershell, nerdfont and fzf <- most important
- git clone this project.
- profit


## What does it

- podadmin: shows all pods in your current namespace: exec, view logs, describe, set pod image, restart, delete.
- svcadmin: shows all services in your current namespace: port forward, edit service, describe, view endpoints.

