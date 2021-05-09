# "Friends Don't Let Friends CURL and BASH"
The [recent covecov.io breach](https://about.codecov.io/security-update/) exposes a glaring security hole at
the core of software development. It's the fact that many projects we use everyday are bootstraped
in an unsafe manner - via CURL and BASH. That means a script directly downloaded from the Internet is piped
directly into shell like this:
```
curl https://www.example.com/install.sh | bash
```
Or downloaded and executed like this:
```
curl https://www.example.com/install.py
python install.py
```
## Why is that a problem?
There is no way to tell if the file being downloaded and executed has not been modified by a hacker.
This can lead to ***"supply chain attacks"***. Or, in the words
of [Mr. Weasley](https://harrypotter.fandom.com/wiki/Arthur_Weasley): ***"Never trust anything
that can think for itself if you can't see where it keeps its brain."***

This happens for several reasons:
- If scripts/releases are not downloaded directly from the original source, it allows an attacker to modify them
in other places such as build systems and webservers without touching the original source code.
- Even for artifacts downloaded directly from source code repositories, there are usually many contributors with
commit rights vs. only a handful of people who push out releases. This gives attackers more targets - BUT also
raises the risk of such commits being discovered.

Here are some recent examples in the wild:
- A web server serving an install script gets hacked (for ex. [codecov.io breach](https://about.codecov.io/security-update/))
- Software vendor's build system gets compromised (for ex. [SolarWinds](https://www.solarwinds.com/sa-overview/securityadvisory))
- An attacker gets unauthorized access to a repo and makes commits (for ex. [PHP](https://news-web.php.net/php.internals/113838))

## What can I do?
***<ins>If you a project maintainer or a software tool company</ins>***:
- ***Consider digitally signing releases/bootstrap scripts, AND providing easy instructions to users
  regarding how to verify signatures. The big guys all do it ([Apache](https://www.apache.org/info/verification.html),
  [NodeJS](https://github.com/nodejs/node#verifying-binaries), etc)***
- Offer a way to install your tools via existing package managers with digital signatures
- Consider running automated checks to make sure your releases still match the source code
- If you are offering direct downloads from your source code, you may want to look into protected branches
so fewer contributors have access to the "release" branch (similar to convential release management)  
  
Of course, these are general suggestions and every project is different. What may work for one, may not work for
someone else.

***<ins>If you are a software developer</ins>***:
- ***If the release/script you want to use is digitally signed, then
  [verify the signature before or use other mitigations](METHODS.MD) to make sure it wasn't modified***
- Consider using a versioned release or installing via a package manager with digital signatures
  instead of a shell script or direct download
- Be aware of what you are doing before installing something off the Internet onto your desktop/laptop/server/phone and
  review the code you are about to run

# The purpose of this repo
The goal of this repo is to provide a list of projects that use this pattern along with information
on how to use them securely. The following resources are provided:
- [CURL_AND_BASH.md](CURL_AND_BASH.md) - list of projects using the "curl | bash" pattern
  and how to verify their downloads
- [CURL_OTHER.md](CURL_OTHER.md) - list of projects using "curl" to download binaries for execution but without
  piping to shell, and how to verify their downloads
- [METHODS.md](METHODS.md) - general instructions about how to verify digital signatures of downloads and mitigation
options when signatures are not available

# Related projects
Some of our projects related to this issue:
- [icetrust](https://github.com/nightwatchcybersecurity/icetrust) - a tool
  that can be used to verify downloads via checksums or PGP. There are also two
  example dashboards that show this tool in action by actively monitoring 
  several well known projects using curl/bash patterns:
    * [icetrust_dashboard](https://icetrust_dashboard.nightwatchcybersecurity.com/)
    * [icetrust_uptime](https://icetrust_uptime.nightwatchcybersecurity.com/)
- 
- [release_auditor](https://github.com/nightwatchcybersecurity/release_auditor) -
  tool for detection of modified Github releases
  (see [our blog post here](https://wwws.nightwatchcybersecurity.com/2021/04/25/supply-chain-attacks-via-github-com-releases/))

# License
Information in this repo is licensed under the [CC-BY 4.0 license](LICENSE) - more
information [available here](https://creativecommons.org/licenses/by/4.0/).

# Feedback and changes
Please use the GitHub issue tracker to provide feedback and suggestions:
https://github.com/nightwatchcybersecurity/dont_curl_and_bash

You can also send emai to ***research /at/ nightwatchcybersecurity [dot] com***

***NOTE:*** Before suggesting adding a project to the lists in this repo, please inform them of these security
issues so they can have an opportunity to address it.