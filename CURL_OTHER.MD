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

| Name | Description | Mitigations | Known issue? |
|------|-------------|-------------|--------------|
| [alibaba cloud cli](https://github.com/aliyun/aliyun-cli)| Cloud management tool | Package managers  |  |
| [dropbox daemon](https://www.dropbox.com/install-linux) | Cloud storage | Package managers |  |
| [gcloud cli](https://cloud.google.com/sdk/gcloud) (binaries) | Cloud management tool | Checksums published on the install page or use package managers  | 1167780 |

# Projects using cryptographic verification
Definition of the fields appearing below:
   * ***Name*** - name/link to the project
   * ***Description*** - short description
   * ***Download URL*** - link to the project's download page
   * ***Other ways to install*** - project documentation on installing the tool in a more secure way
   * ***Verification Methods*** - information about [how to verify downloads](METHODS.MD)

| Name | Description | Downloads | Other ways to install | Verification Methods |
|------|-------------|-----------------------|--------------|--------------|
| [aws cli](https://docs.aws.amazon.com/cli/index.html) | Cloud management tool | https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html |  | [PGP signature](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html#v2-install-linux-validate) |
| [bitwarden cli](https://bitwarden.com/help/article/cli/) | Password manager | https://github.com/bitwarden/cli/releases/download/v1.16.0/bw-linux-1.16.0.zip | Package managers | Checksums |
| [CMake](https://cmake.org/) | Build system for C/C++ | https://cmake.org/download/ | [Docs](https://cmake.org/install/) | [PGP-signed checksum](https://cmake.org/install/#download-verification) |
| [codeclimate](https://github.com/codeclimate/codeclimate#anywhere) | Code Quality toop | https://github.com/codeclimate/codeclimate | | Homebrew or docker |
| [digital ocean cli](https://docs.digitalocean.com/reference/doctl/) | Cloud management tool | https://docs.digitalocean.com/reference/doctl/how-to/install/ | Package managers | Checksums on GitHub |  |
| [Maven](https://maven.apache.org/) | Build system for Java | https://maven.apache.org/download.cgi | APT / RPM | [PGP signature](https://infra.apache.org/release-signing#verifying-signature) |
| [Wordpress](https://wordpress.org/download/releases/) | Blogging / CMS Platform |  |  | Checksums |
| [WP CLI](https://make.wordpress.org/cli/handbook/guides/installing/) | Wordpress CLI | https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar |  | Checksums and PGP |

# Feedback and changes
Please use the GitHub issue tracker to provide feedback and suggestions:
https://github.com/nightwatchcybersecurity/dont_curl_and_bash
