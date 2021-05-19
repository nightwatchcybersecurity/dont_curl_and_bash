# List of projects using the CURL / BASH pattern
This page provides two lists:
- List of projects that do not provide a way to verify integrity of a download via cryptography
- And a list of projects that do

# Projects WITHOUT cryptographic verification
Definition of the fields appearing below:
   * ***Name*** - name/link to the project
   * ***Description*** - short description
   * ***Script URL*** - URL(s) of the bootstrap scripts
   * ***Other ways to install*** - project documentation on installing the tool in a more secure way
   * ***Mitigations*** - documentation on possible [possible mitigations](METHODS.MD)
   * ***Known issue*** - link to a public bug report regarding improving verification of downloads

| Name | Description | Script URL | Other ways to install | Mitigations | Known issue? |
|------|-------------|-----------------------|--------------|--------------|---
| [azure cli](https://docs.microsoft.com/en-us/cli/azure/) | Cloud management tool | https://aka.ms/InstallAzureCli | [Package managers](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) | Use package managers |  |
| [codecov](https://about.codecov.io/) | Code coverage tool | https://codecov.io/bash | [Node](https://github.com/codecov/codecov-node), [Python](https://github.com/codecov/codecov-python) and [Ruby](https://github.com/codecov/codecov-ruby) | [Checksums](https://docs.codecov.io/docs/about-the-codecov-bash-uploader#validating-the-bash-script) | [Yes](https://about.codecov.io/blog/validating-the-bash-script-on-ci/)  |
| [dotnetcore install script](https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-install-script) | Language runtime | https://dot.net/v1/dotnet-install.sh | [Package managers](https://docs.microsoft.com/en-us/dotnet/core/install/) | Package managers |  |
| [fusionauth installer](https://fusionauth.io/docs/v1/tech/installation-guide/fast-path/) | Authentication and authorization tool | [link](https://raw.githubusercontent.com/FusionAuth/fusionauth-install/master/install.sh) | Package managers | Uses direct GitHub download | [Yes](https://github.com/FusionAuth/fusionauth-issues/issues/1159) |
| [gcloud cli](https://cloud.google.com/sdk/docs/downloads-interactive) (script) | Cloud management tool | https://sdk.cloud.google.com | [Package managers/binaries](https://cloud.google.com/sdk/docs/install#installation_instructions) | Use package managers or PGP-signed binaries |  |
| [heroku cli](https://devcenter.heroku.com/articles/heroku-cli#download-and-install) | Cloud management tool | https://cli-assets.heroku.com/install.sh | [Package managers](https://devcenter.heroku.com/articles/heroku-cli#download-and-install) | Use package managers |  |
| [homebrew](https://brew.sh/) | Package manager for MacOS | [link](https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh) | [Docs](https://docs.brew.sh/Installation) | Uses direct Github download | [Yes](https://wwws.nightwatchcybersecurity.com/2021/04/30/security-of-homebrew-bootstrap-process/)  |
| [ibm cloud cli](hhttps://cloud.ibm.com/docs/cli?topic=cli-getting-started) | Cloud management tool | https://ibm.biz/idt-installer  | | Use direct GitHub download |  |
| [magento cloud cli](https://devdocs.magento.com/cloud/reference/cli-ref-topic.html) | Cloud management tool | https://accounts.magento.cloud/cli/installer |  |  |   |
| [pip](https://pip.pypa.io/en/stable/) | Package manager for Python | https://bootstrap.pypa.io/get-pip.py | [OS packages](https://pip.pypa.io/en/stable/installing/) | Use package managers | [Yes](https://github.com/pypa/get-pip/issues/41) |
| [platform.sh](https://docs.platform.sh/development/cli.html#installation) | Cloud management tool | https://platform.sh/cli/installer |  | Use direct GitHub download |  |
| [poetry](https://python-poetry.org/docs/#installation) | Package manager for Python | [link](https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py) |  | Uses direct Github download |   |
| [Rust](https://www.rust-lang.org/) & [Cargo](https://doc.rust-lang.org/cargo/) | Rust language and Cargo package manager | https://sh.rustup.rs | [Docs](https://forge.rust-lang.org/infra/other-installation-methods.html) | Use package managers or standalone installers  | [Yes](https://github.com/rust-lang/rustup/issues/2029) |
| [scoop](https://scoop.sh/) | Windows installer tool | https://get.scoop.sh/ | | Direct GitHub download | |
| [sdkman](https://sdkman.io/install) | Environment management tool | https://get.sdkman.io/ | | |  |

# Projects using cryptographic verification
Definition of the fields appearing below:
   * ***Name*** - name/link to the project
   * ***Description*** - short description
   * ***Script URL*** - URL(s) of the bootstrap scripts
   * ***Other ways to install*** - project documentation on installing the tool in a more secure way
   * ***Verification Methods*** - information about [how to verify downloads](METHODS.MD)

| Name | Description | Script URL | Other ways to install | Verification Methods |
|------|-------------|-----------------------|--------------|--------------|
| [chocolatey](https://chocolatey.org/) | Package manager for Windows | https://chocolatey.org/install.ps1 | [Docs](https://docs.chocolatey.org/en-us/choco/setup#more-install-options) | [Authenticode](https://docs.chocolatey.org/en-us/information/security#chocolatey-binaries-and-the-chocolatey-package) |
| [nix](https://nixos.org/manual/nix/stable/) | Package manager for Linux/MacOS/Windows | https://nixos.org/nix/install | [Source](https://nixos.org/manual/nix/stable/#ch-installing-source) | [PGP signature](https://nixos.org/download.html#nix-verify-installation) |
| [pnpm](https://pnpm.io/) | Package manager for NodeJS | https://get.pnpm.io/v6.js | [Docs](https://pnpm.io/installation) | [PGP-signed checksum](https://github.com/pnpm/get#verifying-files) |
| [RVM](https://rvm.io/) | Tool for managing Ruby environments | https://get.rvm.io | [Docs](https://rvm.io/rvm/install) | [PGP signature](https://rvm.io/rvm/security) |

# Feedback and changes
Please use the GitHub issue tracker to provide feedback and suggestions:
https://github.com/nightwatchcybersecurity/dont_curl_and_bash
