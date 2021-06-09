# List of projects using the CURL / BASH pattern
This page provides two lists:
- List of projects that do not provide a way to verify integrity of a download via cryptography
- And a list of projects that do

# Projects WITHOUT cryptographic verification
Definition of the fields appearing below:
   * ***Name*** - name/link to the project
   * ***Description*** - short description
   * ***Script URL*** - URL(s) of the bootstrap scripts
   * ***Mitigations*** - documentation on possible [possible mitigations](METHODS.MD)
   * ***Known issue*** - link to a public bug report regarding improving verification of downloads

| Name | Description | Script URL | Mitigations | Known issue? |
|------|-------------|------------|-------------|--------------|
| [azure cli](https://docs.microsoft.com/en-us/cli/azure/) | Cloud management tool | https://aka.ms/InstallAzureCli | Use package managers |  |
| [chef](https://docs.chef.io/chef_install_script/) | Configuration management tool | https://omnitruck.chef.io/install.sh |  |  |
| [codecov](https://about.codecov.io/) | Code coverage tool | https://codecov.io/bash | [Checksums](https://docs.codecov.io/docs/about-the-codecov-bash-uploader#validating-the-bash-script) | [Yes](https://about.codecov.io/blog/validating-the-bash-script-on-ci/)  |
| [dell system update](https://linux.dell.com/repo/hardware/dsu/) | Firmware update tool | https://linux.dell.com/repo/hardware/dsu/bootstrap.cgi |  |  |
| [dotnetcore install script](https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-install-script) | Language runtime | https://dot.net/v1/dotnet-install.sh | Package managers |  |
| [firebase cli](https://firebase.tools/) | Cloud management tool | https://firebase.tools/ |  Github releases | 189149887 |
| [fusionauth installer](https://fusionauth.io/docs/v1/tech/installation-guide/fast-path/) | Authentication and authorization tool | [link](https://raw.githubusercontent.com/FusionAuth/fusionauth-install/master/install.sh) | Package managers, uses direct GitHub download| [Yes](https://github.com/FusionAuth/fusionauth-issues/issues/1159) |
| [gcloud cli](https://cloud.google.com/sdk/docs/downloads-interactive) (script) | Cloud management tool | https://sdk.cloud.google.com | Use package managers or PGP-signed binaries |  |
| [heroku cli](https://devcenter.heroku.com/articles/heroku-cli#download-and-install) | Cloud management tool | https://cli-assets.heroku.com/install.sh | Use package managers |  |
| [homebrew](https://brew.sh/) | Package manager for MacOS | [link](https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh) | Uses direct Github download | [Yes](https://wwws.nightwatchcybersecurity.com/2021/04/30/security-of-homebrew-bootstrap-process/)  |
| [ibm cloud cli](https://cloud.ibm.com/docs/cli?topic=cli-getting-started) | Cloud management tool | https://ibm.biz/idt-installer  | Use direct GitHub download |  |
| [jfrog cli installer](https://jfrog.com/getcli/) | Developer tools | https://getcli.jfrog.io/ | Use direct GitHub download | |
| [magento cloud cli](https://devdocs.magento.com/cloud/reference/cli-ref-topic.html) | Cloud management tool | https://accounts.magento.cloud/cli/installer |  |   |
| [mattermost repo setup](https://docs.mattermost.com/help/getting-started/light-install.html#installation) | Collaboration platform | https://deb.packages.mattermost.com/repo-setup.sh |  |   |
| [nextcloud web installer](https://nextcloud.com/install/#instructions-server) | Collaboration platform | https://download.nextcloud.com/server/installer/setup-nextcloud.php | Use PGP-signed binaries |  |
| [nvm](https://github.com/nvm-sh/nvm#installing-and-updating) | Node.js version manager | [link](https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh) | Uses direct Github download |  |
| [pi-hole installer](https://docs.pi-hole.net/main/basic-install/) | Privacy tool | https://install.pi-hole.net | Clone repository | [Yes](https://pi-hole.net/2016/07/25/curling-and-piping-to-bash/) |
| [pip](https://pip.pypa.io/en/stable/) | Package manager for Python | https://bootstrap.pypa.io/get-pip.py | Use package managers | [Yes](https://github.com/pypa/get-pip/issues/41) |
| [platform.sh](https://docs.platform.sh/development/cli.html#installation) | Cloud management tool | https://platform.sh/cli/installer | Use direct GitHub download |  |
| [poetry](https://python-poetry.org/docs/#installation) | Package manager for Python | [link](https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py) | Uses direct Github download |   |
| [Rust](https://www.rust-lang.org/) & [Cargo](https://doc.rust-lang.org/cargo/) | Rust language and Cargo package manager | https://sh.rustup.rs | Use package managers or standalone installers  | [Yes](https://github.com/rust-lang/rustup/issues/2029) |
| [saucectl](https://docs.saucelabs.com/testrunner-toolkit/installation/index.html#installing-saucectl) | Testing tool | https://saucelabs.github.io/saucectl/install | Direct GitHub download | |
| [scoop](https://scoop.sh/) | Windows installer tool | https://get.scoop.sh/ | Direct GitHub download | |
| [sdkman](https://sdkman.io/install) | Environment management tool | https://get.sdkman.io/ | | | 
| [veracode sca agent (sourceclear)](https://help.veracode.com/r/c_sc_ci_script) | Security scanner | https://download.sourceclear.com/ci.sh | | | 

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
| [salt bootstrap](https://github.com/saltstack/salt-bootstrap) | Configuration management tool | https://bootstrap.saltproject.io | Package managers | Checksums |
| [volta](https://docs.volta.sh/guide/getting-started) | NodeJS Tool manager | https://get.volta.sh | | Checksums |

# Feedback and changes
Please use the GitHub issue tracker to provide feedback and suggestions:
https://github.com/nightwatchcybersecurity/dont_curl_and_bash
