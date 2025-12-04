# ylog

**ylog** is your personl log to track your work, commands, and any notes straight from the terminal.

It provides a structured way to capture:

* **Daily logs** (what you did today)
* **Notes** (organized by topics, automatically forming documentation)
* **Command history snippets** (searchable, contextual)
* **Search across everything** (maybe)

## Features

### Daily Activity Logging

```
ylog "Investigated container startup delays"
```

All logged entries are chronologically organized.

### Topic-Based Notes

```
ylog note k8s "Kubelet eviction threshold notes"
```

Notes accumulate into topics, which can later be exported as standalone documentation in Markdown.

```
ylog note k8s:cni:cilium '`k8s-cilium-exec.sh` script can be used to run `cilium-dbg` status on all nodes.'
```

For example, the note above will be placed in the k8s markdown note file, under the cilium header which is nested below cni.

### Command History Capture

Store useful command snippets so you can recall them later:

```
# Capture common commands
ylog cmd "ylog cmd "openssl x509 -in cert.pem -text -noout"

# Capture last command
ylog cmd !!

# Capture command from history line 123
ylog cmd !123

# And few others
ylog cmd !432 !531
```

These commands will be stored in a dedicated file for each executable (binary, script, etc) for quick search/reference.

### Universal Search (TBD)

Everything ylog captures can be searched with grep. Is it worth implementing?

```
# Search all ylog
ylog search "git rebase"

# Search only in the git note under reset
ylog search -n tcpdump "

# Search only commands
ylog search -c "git reset"
```

## Installation

```
git clone https://github.com/gmherb/ylog
cd ylog
make install
```

This will build and install the `ylog` binary.
