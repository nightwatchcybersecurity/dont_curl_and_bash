# List of projects providing direct downloads for execution
This page provides two lists:
- List of projects that do not provide a way to verify integrity of a download via cryptography
- And a list of projects that do

# Projects WITHOUT cryptographic verification
Definition of the fields appearing below:
   * ***Name*** - name/link to the project
   * ***Description*** - short description
   * ***Download URL*** - link to the project's download page
   * ***Other ways to install*** - project documentation on installing the tool in a more secure way
   * ***Mitigations*** - documentation on [possible mitigations](METHODS.MD)
   * ***Known issue*** - link to a public bug report regarding improving verification of downloads

| Name | Description | Download URL | Other ways to install | Mitigations | Known issue? |
|------|-------------|-----------------------|--------------|--------------|---
| [gcloud cli](https://cloud.google.com/sdk/gcloud) | Cloud management tool | https://cloud.google.com/sdk/docs/install#linux | [Package managers](https://cloud.google.com/sdk/docs/install) | Checksums published on the install page or use package managers  | 1167780 |

# Projects using cryptographic verification
Definition of the fields appearing below:
   * ***Name*** - name/link to the project
   * ***Description*** - short description
   * ***Download URL*** - link to the project's download page
   * ***Other ways to install*** - project documentation on installing the tool in a more secure way
   * ***Verification Methods*** - information about [how to verify downloads](METHODS.MD)

| Name | Description | Downloads | Other ways to install | Verification Methods |
|------|-------------|-----------------------|--------------|--------------|
| [aws cli](https://docs.aws.amazon.com/cli/index.html) | Cloud management tool | https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html |  | [PGP signature](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html#v2-install-linux-validate) |
| [CMake](https://cmake.org/) | Build system for C/C++ | https://cmake.org/download/ | [Docs](https://cmake.org/install/) | [PGP-signed checksum](https://cmake.org/install/#download-verification) |
| [Maven](https://maven.apache.org/) | Build system for Java | https://maven.apache.org/download.cgi | APT / RPM | [PGP signature](https://infra.apache.org/release-signing#verifying-signature) |

# Feedback and changes
Please use the GitHub issue tracker to provide feedback and suggestions:
https://github.com/nightwatchcybersecurity/dont_curl_and_bash
