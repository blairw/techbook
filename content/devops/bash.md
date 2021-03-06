---
Title: bash
---

*&larr; back to [DevOps](%base_url%/?devops)*

# bash

No sensible DevOps environment is complete without some sort of bash terminal. Just on Windows you need to install Cygwin.

## aria2c

It's like `wget` (download stuff from the internet) but vastly superior.

Availability:

- [Linux](%base_url%/?devops/linux) - yes, using your package manager
- [Mac](%base_url%/?devops/mac) - yes, using Homebrew
- [Windows](%base_url%/?devops/windows) - yes, using Cygwin

Usage:

```bash
aria2c <switches> <file>
```

Switches:

- `ftp-proxy` - This is required when you can only connect to the server through a proxy server or VPN. Example:

    ```
    --ftp-proxy=i.wish.i.had.a.proxy.server.blairwang.id.au:8080
    ```

- `load-cookies` - This loads cookies from a web browser like Firefox - very handy if you're downloading from a site that uses cookies to authenticate a restricted download.

    ```
    --load-cookies="/Users/wblair/Library/Application Support/Firefox/Profiles/if9f1yrl.default/cookies.sqlite"
    ```

## find

### Get full paths for all files in a folder

Adapted from [Matthew Scharley](https://stackoverflow.com/questions/246215/how-can-i-list-files-with-their-absolute-path-in-linux)

```
find `pwd` -type f -name "*.jpg"
```

## sed

```bash
sed -i -e 's/^.*static let TAG.*$//g' *.swift
```

## find

- Search and destroy all instances of a file (or search string for file) - e.g. delete all instances of the [Mac](?mac) `.DS_Store` file:

    ```
    find . -type f -name ".DS_Store" -exec rm {} \;
    ```

    So you might as well also kill `Thumbs.db` from Windows XP:

    ```
    find . -type f -name "Thumbs.db" -exec rm {} \;
    ```

## Pretty PS1

**PS1** (said to stand for **Prompt String 1**) is the string that appears before every typed command.

The PS1 string below has been designed to be a shade of blue that works well on both black and white backgrounds. Put it in `~/.bash_profile` and `~/.bashrc` for each user who wants it.

```bash
export PS1="\[\033[38;5;39m\][\u@\h \t \W]\[$(tput sgr0)\]\[\033[38;5;15m\] \[$(tput sgr0)\]"
```

Example:

![ps1-demo.png](%base_url%/assets/images/ps1-demo.png)