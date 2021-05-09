# How to verify downloads and what to do they are not signed?
This page provides information regarding how to verify signed downloads, and mitigation options when signatures
are not possible/available. None of these are perfect.

We also have some related tools:
- [icetrust](https://github.com/nightwatchcybersecurity/icetrust) - a tool
  that can be used to verify downloads via checksums or PGP. There are also two
  example dashboards that show this tool in action by actively monitoring 
  several well known projects using curl/bash patterns:
    * [icetrust_dashboard](https://icetrust_dashboard.nightwatchcybersecurity.com/)
    * [icetrust_uptime](https://icetrust_uptime.nightwatchcybersecurity.com/)

# Verification methods for signed downloads
## Code signing
Some operating systems (Windows, MacOS, etc) offer ability to digitally sign a given script or package with
a digital certificate issued by a CA, similar to TLS. However, there have been instances of 
rogue/stolen certificates, so it is best to verify that a specific CA or certificate was used ("pinning").

### Authenticode on Windows
Authenticode is a code signing technology used by Windows applications. To verify a download or script signed
in this fashion, run the following PowerShell command and verify the subject name of the signing certificate:
```
Invoke-WebRequest https://www.example.com/install.exe -OutFile install.exe
(Get-AuthenticodeSignature -FilePath install.exe).SignerCertificate | Format-List
```

## PGP signatures
The most secure approach currently used is PGP signatures. This is usually done by a project maintainers who signs
the release/tool, generating a separate file containing a signature ("detached signature"). Given a known key,
PGP can be used to verify the signature. Here are examples on how to verify such signatures
with [GnuPG](https://www.gnupg.org/).

### Using a static file containing keys
If you are using a static file with keys, those must be downloaded and imported into GPG - ideally before
you start using the software. Note, that this modifies the keyring kept by GPG on your local system and you should
periodically check if the keys expired or were revoked. Doing this during the install is also possible, but you
run the chance of the keys being compromised if they are hosted on the same server.

To download and import the keys:
```
curl https://keys.example.com/keys.txt
gpg --import keys.txt
```

Once imported, here is an example of how to verify a download:
```
curl https://www.example.com/install.sh
curl https://www.example.com/install.sh.sig

gpg --verify install.sh.sig install.sh
```

### Using a key ID and key server
Some projects may provide a key ID and keyserver name, allowing you to import the keys from a public
keyserver. Be aware that these can be poisoned.

As with the previous example, the keys must be imported into GPG - ideally before
you start using the software. Note, that this modifies the keyring kept by GPG on your local system and you should
periodically check if the keys expired or were revoked. Doing this during the install is also possible, but you
run the chance of the keys being compromised if the key ID you are using is from a webpage hosted on the 
same server.

To import the key:
```
gpg --keyserver pgp-server.example.com --recv-keys 12345E12345
```

To verify a download, proceed with the same steps as above.

## PGP-signed checksums
Similar to same as above, except that a file with checksums is generated then digitally signed.
To verify, you first confirm that the PGP signature on the checksums file is correct then re-run
the checksums and make sure they match. Slightly more convoluted to verify but accomplishes
the same goal - same caveats apply as the PGP approaches above.

### Using a static file containing keys

To download and import the keys:
```
curl https://keys.example.com/keys.txt
gpg --import keys.txt
```

Once imported, here is an example of how to verify a download:
```
curl https://www.example.com/install.sh
curl https://www.example.com/checksums.txt
curl https://www.example.com/checksums.txt.sig

gpg --verify checksums.txt.sig checksums.txt
grep install.sh checksums.txt | sha256sum -c -
```

### Using a key ID and key server

Example of how to import a key:
```
gpg --keyserver pgp-server.example.com --recv-keys 12345E12345
```

To verify a download, proceed with the same steps as above.

### Important note about cryptography and keys
_In all methods using cryptography, one must get copies of the public keys securely, either by a PGP key ID from a PGP
keyserver  or from a file published by the project maintainers. Approaches using public CA infrastructure rely
on the list of root CAs available within a particular platform, but if pinning is used, you must obtain
the certificate or its fingerprint securely - usually via a static file._

_Users should be aware that a static file with keys or certificate information can also be changed
by an attacker and PGP 
keyservers [can be poisoned](https://gist.github.com/rjhansen/67ab921ffb4084c865b3618d6955275f). Rogue
and stolen code signing certificates have also been used in the wild._

## Mitigations for unsigned downloads
Some idea for mitigations if the tool/project you are using is not digitally signed

### Package managers / Releases
Many project offer their tools as a package within a platform or language specific package manager
such as apt, rpm, npm, maven, nuget, etc. Because those go through a release process, they may be somewhat safer
than a web server, BUT there have been many instances of attacks in that space as well. Using a package
manager with digital signatures may be helpful.

Another spin on this approach is using an official release packaged by a project as opposed to something on
a webserver. But attackers can change those as well.

### Checksums/Hashes
Some projects publish a separate file containing hashes/checksums calculated by a tool like ***shasum***.
If they are hosted on the same server as the main download, it is trivial for an attacker to modify this file
but attackers often fail to do so. Therefore, this approach is more secure if the checksums published
a different server/website - away from the script/release they are protecting. This forces an attacker to
hack into two different web servers - something much hard to accomplish.

Here is an example of how to verify a download with checksums:
```
curl https://www.example.com/install.sh
curl https://server2.example.com/checksums.txt

grep install.sh checksums.txt | sha256sum -c -
```

### Comparing against source code
You may try to compare the download against the original source code, however this isn't trivial if the script
or tool in question is built or assembled from multiple files. Reproducible builds are a hard problem to solve.
And you might as well download straight from source instead of some intermediate server.

However, if you want to compare against the source, it would look like this:
```
curl https://www.example.com/install.sh
curl -O source.sh https://git.example.com/install.sh

diff source.sh install.sh
```

### Direct source code download
Some projects bootstrap via a direct download from their source code repositories. This avoids attacks on web
servers but doesn't solve for attacks involving unauthorized repository access. Nevertheless, since most
projects have multiple contributors, an malicious commit would be detected  fairly quickly. Additionally,
if protected branches are used, access to the "release" branch can be locked down to a fewer set of contributors.
Nevertheless, it is still risky.

A direct source code download may look like this:
```
curl https://source.example.com/project/HEAD/install.sh
```
     
# Feedback and changes
Please use the GitHub issue tracker to provide feedback and suggestions:
https://github.com/nightwatchcybersecurity/dont_curl_and_bash