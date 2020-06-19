

<img src="https://raw.githubusercontent.com/cloudfoundry/logos/master/CF_Icon_4-colour.png" alt="CF logo" height="100" align="left"/>

# Cloud Foundry CLI

[![GitHub version](https://badge.fury.io/gh/cloudfoundry%2Fcli.svg)](https://github.com/cloudfoundry/cli/releases/latest)
[![Documentation](https://img.shields.io/badge/docs-online-ff69b4.svg)](https://docs.cloudfoundry.org/cf-cli)
[![Command help pages](https://img.shields.io/badge/command-help-lightgrey.svg)](https://cli.cloudfoundry.org)
[![Slack](https://slack.cloudfoundry.org/badge.svg)](https://slack.cloudfoundry.org)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://github.com/cloudfoundry/cli/blob/master/LICENSE)

***
<p align="left">
<b>Sections: </b>
<b><a href="#getting-started">Getting Started</a></b>
|
<b><a href="#downloads">Download</a></b>
|
<b><a href="#known-issues">Known Issues</a></b>
|
<b><a href="#filing-issues--feature-requests">Bugs/Feature Requests</a></b>
|
<b><a href="#plugin-development">Plugin Development</a></b>
|
<b><a href="#contributing--build-instructions">Contributing</a></b>
</p>

***

***Cloud Foundry CLI*** is the official command line client for [Cloud Foundry](https://cloudfoundry.org).
Latest help of each command is [here](https://cli.cloudfoundry.org) (or run `cf help`);

Currently, there are two versions of the cf CLI in development: 
- the supported v6 cf CLI. See [here](https://docs.cloudfoundry.org/cf-cli) for more information. 
- v7 is stable and will be generally available very soon. With the exception of plugins, it is completely backed by the [v3 API](http://v3-apidocs.cloudfoundry.org/version/3.75.0/index.html). See [here](https://docs.cloudfoundry.org/cf-cli/v7.html) for more information. 


## The v7 CF CLI is pending GA and when it does:
- It will be opt-in.
- Using our supported package managers to pull down the latest v6 CF CLI will continue to work. 
- If you've been pulling down the v7 CF CLI, you **will** be impacted because the v7 binary name will change from `cf7` to `cf` (so `cf7` prefixed commands will no longer work; `cf` prefixed commands will invoke the v7 CLI).
- If you must switch back and forth between CLI versions on the same client, see the [Version Switching](#version-switching) section for instructions.
 
**A Note About v7 Support**:
From the point of v7 GA onward, new features, enhancements, and fixes will only be made on the v7 line.
The v6 line will only be updated to resolve the most severe defects and/or security issues. 
Additionally, when v7 GA's the v7 CLI's minimum supported version of the CC API will be established at v3.85.0 (published in [CAPI release v1.95.0](https://github.com/cloudfoundry/capi-release/releases/tag/1.95.0)), and the maximum supported version of the CC API for the v6 CLI will be capped at v2.149.0 and v3.84.0 (published in [CAPI release v1.94.0](https://github.com/cloudfoundry/capi-release/releases/tag/1.94.0)).

**A Note About v6 Support**: The v6 CF CLI supports as far back as CF Deployment v7.0.0, CAPI Release: 1.74.0 (APIs 2.128.0 and 3.63.0). See our [Versioning Policy](https://github.com/cloudfoundry/cli/wiki/Versioning-Policy#cf-cli-minimum-supported-version) for more information. If you are on an older version of CF Deployment, we recommend you upgrade to a supported version.

If you have any questions, ask away on the #cli channel in [our Slack
community](https://slack.cloudfoundry.org/) and the
[cf-dev](https://lists.cloudfoundry.org/archives/list/cf-dev@lists.cloudfoundry.org/)
mailing list, or [open a GitHub issue](https://github.com/cloudfoundry/cli/issues/new).  You can follow our development progress
on [Core CF CLI Pivotal Tracker](https://www.pivotaltracker.com/n/projects/892938).

## Getting Started

Download and install the cf CLI from the [Downloads Section](#downloads) for either the [v6 cf CLI](https://github.com/cloudfoundry/cli/blob/master/README.md#downloading-the-v6-cli) or the [v7 beta cf CLI](https://github.com/cloudfoundry/cli/blob/master/README.md#downloading-the-v7-beta-cli). 

Once installed, you can log in and push an app.

**Need to switch back and forth between CLI versions?**
See the [Version Switching](#version-switching) section for instructions.

![Example](.github/cf_example.gif)

Check out our [community contributed CLI plugins](https://plugins.cloudfoundry.org) to further enhance your CLI experience.

## Downloads

It is recommended to download installers from the published URLs or using one of the documented package managers (APT/deb/homebrew repos).  Published URLs may redirect requests to URLs that may change over time, so may installer filenames change over time.

### Downloading the latest CF CLI

#### Installing using a package manager

**Mac OS X** and **Linux** using [Homebrew](https://brew.sh/) via the [cloudfoundry tap](https://github.com/cloudfoundry/homebrew-tap):

```sh
brew install cloudfoundry/tap/cf-cli
```

**Note:** `cf` tab completion requires `bash-completion` to be installed properly in order to work.

**Debian** and **Ubuntu** based Linux distributions:

```sh
# ...first add the Cloud Foundry Foundation public key and package repository to your system
wget -q -O - https://packages.cloudfoundry.org/debian/cli.cloudfoundry.org.key | sudo apt-key add -
echo "deb https://packages.cloudfoundry.org/debian stable main" | sudo tee /etc/apt/sources.list.d/cloudfoundry-cli.list
# ...then, update your local package index, then finally install the cf CLI
sudo apt-get update
sudo apt-get install cf-cli
```

**Enterprise Linux** and **Fedora** systems (RHEL6/CentOS6 and up):
```sh
# ...first configure the Cloud Foundry Foundation package repository
sudo wget -O /etc/yum.repos.d/cloudfoundry-cli.repo https://packages.cloudfoundry.org/fedora/cloudfoundry-cli.repo
# ...then, install the cf CLI (which will also download and add the public key to your system)
sudo yum install cf-cli
```

#### Installers and compressed binaries


| | Mac OS X 64 bit | Windows 64 bit | Linux 64 bit |
| :---------------: | :---------------: |:---------------:| :------------:|
| Installers | [pkg](https://packages.cloudfoundry.org/stable?release=macosx64&source=github) |[zip](https://packages.cloudfoundry.org/stable?release=windows64&source=github)  | [rpm](https://packages.cloudfoundry.org/stable?release=redhat64&source=github) / [deb](https://packages.cloudfoundry.org/stable?release=debian64&source=github) |
| Binaries | [tgz](https://packages.cloudfoundry.org/stable?release=macosx64-binary&source=github) | [zip](https://packages.cloudfoundry.org/stable?release=windows64-exe&source=github) | [tgz](https://packages.cloudfoundry.org/stable?release=linux64-binary&source=github) |

Release notes, and 32 bit releases can be found [here](https://github.com/cloudfoundry/cli/releases).

**Download examples** with curl for Mac OS X and Linux binaries
```sh
# ...download & extract Mac OS X binary
curl -L "https://packages.cloudfoundry.org/stable?release=macosx64-binary&source=github" | tar -zx
# ...or Linux 64-bit binary
curl -L "https://packages.cloudfoundry.org/stable?release=linux64-binary&source=github" | tar -zx
# ...move it to /usr/local/bin or a location you know is in your $PATH
mv cf /usr/local/bin
# ...copy tab completion file on Ubuntu (takes affect after re-opening your shell)
sudo curl -o /usr/share/bash-completion/completions/cf https://raw.githubusercontent.com/cloudfoundry/cli-ci/master/ci/installers/completion/cf
# ...and to confirm your cf CLI version
cf --version
```

##### Edge binaries
Edge binaries are *not intended for wider use*; they're for developers to test new features and fixes as they are 'pushed' and passed through the CI.
Follow these download links for [Mac OS X 64 bit](https://packages.cloudfoundry.org/edge?arch=macosx64&source=github), [Windows 64 bit](https://packages.cloudfoundry.org/edge?arch=windows64&source=github) and [Linux 64 bit](https://packages.cloudfoundry.org/edge?arch=linux64&source=github).

---------------------------------------

### Downloading the latest V6 CF CLI

#### Installing using a package manager

**Mac OS X** and **Linux** using [Homebrew](https://brew.sh/) via the [cloudfoundry tap](https://github.com/cloudfoundry/homebrew-tap):

```sh
brew install cloudfoundry/tap/cf-cli@6
```

**Note:** `cf` tab completion requires `bash-completion` to be installed properly in order to work.

**Debian** and **Ubuntu** based Linux distributions:

```sh
# ...first add the Cloud Foundry Foundation public key and package repository to your system
wget -q -O - https://packages.cloudfoundry.org/debian/cli.cloudfoundry.org.key | sudo apt-key add -
echo "deb https://packages.cloudfoundry.org/debian stable main" | sudo tee /etc/apt/sources.list.d/cloudfoundry-cli.list
# ...then, update your local package index, then finally install the cf CLI
sudo apt-get update
sudo apt-get install cf-cli
```

**Enterprise Linux** and **Fedora** systems (RHEL6/CentOS6 and up):
```sh
# ...first configure the Cloud Foundry Foundation package repository
sudo wget -O /etc/yum.repos.d/cloudfoundry-cli.repo https://packages.cloudfoundry.org/fedora/cloudfoundry-cli.repo
# ...then, install the cf CLI (which will also download and add the public key to your system)
sudo yum install cf-cli
```

#### Installers and compressed binaries


| | Mac OS X 64 bit | Windows 64 bit | Linux 64 bit |
| :---------------: | :---------------: |:---------------:| :------------:|
| Installers | [pkg](https://packages.cloudfoundry.org/stable?release=macosx64&source=github) |[zip](https://packages.cloudfoundry.org/stable?release=windows64&source=github)  | [rpm](https://packages.cloudfoundry.org/stable?release=redhat64&source=github) / [deb](https://packages.cloudfoundry.org/stable?release=debian64&source=github) |
| Binaries | [tgz](https://packages.cloudfoundry.org/stable?release=macosx64-binary&source=github) | [zip](https://packages.cloudfoundry.org/stable?release=windows64-exe&source=github) | [tgz](https://packages.cloudfoundry.org/stable?release=linux64-binary&source=github) |

Release notes, and 32 bit releases can be found [here](https://github.com/cloudfoundry/cli/releases).

**Download examples** with curl for Mac OS X and Linux binaries
```sh
# ...download & extract Mac OS X binary
curl -L "https://packages.cloudfoundry.org/stable?release=macosx64-binary&source=github" | tar -zx
# ...or Linux 64-bit binary
curl -L "https://packages.cloudfoundry.org/stable?release=linux64-binary&source=github" | tar -zx
# ...move it to /usr/local/bin or a location you know is in your $PATH
mv cf /usr/local/bin
# ...copy tab completion file on Ubuntu (takes affect after re-opening your shell)
sudo curl -o /usr/share/bash-completion/completions/cf https://raw.githubusercontent.com/cloudfoundry/cli-ci/master/ci/installers/completion/cf
# ...and to confirm your cf CLI version
cf --version
```

##### Edge binaries
Edge binaries are *not intended for wider use*; they're for developers to test new features and fixes as they are 'pushed' and passed through the CI.
Follow these download links for [Mac OS X 64 bit](https://packages.cloudfoundry.org/edge?arch=macosx64&source=github), [Windows 64 bit](https://packages.cloudfoundry.org/edge?arch=windows64&source=github) and [Linux 64 bit](https://packages.cloudfoundry.org/edge?arch=linux64&source=github).

---------------------------------------


### Downloading the latest V7 CF CLI (BETA)

**Important Note**: The v7 CF CLI is pending GA. When it GA's, the binary will be renamed from `cf7` to `cf`. If you're already using the v7 CLI in parallel to the v6 CLI, you may need to change your workflow to accomodate the binary name change. See the [Version Switching](#version-switching) section for instructions. For more information and general status on the v7 CLI, please check [releases](https://github.com/cloudfoundry/cli/releases). 

#### Compatibility
When v7 GA's the v7 CLI's minimum supported version of the CC API will be established at `v3.85.0` (published in [CAPI release v1.95.0](https://github.com/cloudfoundry/capi-release/releases/tag/1.95.0)).
All pre-GA betas have been tested against CAPI release candidate available at the time the betas were published. See the [releases](https://github.com/cloudfoundry/cli/releases) page for the minimum CAPI RC version required for each V7 beta version.


#### Installing using a package manager

**Mac OS X** and **Linux** using [Homebrew](https://brew.sh/) via the [cloudfoundry tap](https://github.com/cloudfoundry/homebrew-tap):

```sh
brew install cloudfoundry/tap/cf-cli@7
```

**Note:** `cf7` tab completion requires `bash-completion` to be installed properly in order to work.

**Debian** and **Ubuntu** based Linux distributions:

```sh
# ...first add the Cloud Foundry Foundation public key and package repository to your system
wget -q -O - https://packages.cloudfoundry.org/debian/cli.cloudfoundry.org.key | sudo apt-key add -
echo "deb https://packages.cloudfoundry.org/debian stable main" | sudo tee /etc/apt/sources.list.d/cloudfoundry-cli.list
# ...then, update your local package index, then finally install the cf CLI
sudo apt-get update
sudo apt-get install cf7-cli
```

**Enterprise Linux** and **Fedora** systems (RHEL6/CentOS6 and up):
```sh
# ...first configure the Cloud Foundry Foundation package repository
sudo wget -O /etc/yum.repos.d/cloudfoundry-cli.repo https://packages.cloudfoundry.org/fedora/cloudfoundry-cli.repo
# ...then, install the cf CLI (which will also download and add the public key to your system)
sudo yum install cf7-cli
```


#### Installers and compressed binaries

| | Mac OS X 64 bit | Windows 64 bit | Linux 64 bit |
| :---------------: | :---------------: |:---------------:| :------------:|
| Installers |[pkg](https://packages.cloudfoundry.org/stable?release=macosx64&version=v7&source=github) | [zip](https://packages.cloudfoundry.org/stable?release=windows64&version=v7&source=github) | [rpm](https://packages.cloudfoundry.org/stable?release=redhat64&version=v7&source=github) / [deb](https://packages.cloudfoundry.org/stable?release=debian64&version=v7&source=github) |
| Binaries | [tgz](https://packages.cloudfoundry.org/stable?release=macosx64-binary&version=v7&source=github) |[zip](https://packages.cloudfoundry.org/stable?release=windows64-exe&version=v7&source=github)  | [tgz](https://packages.cloudfoundry.org/stable?release=linux64-binary&version=v7&source=github) |

Release notes, and 32 bit releases can be found [here](https://github.com/cloudfoundry/cli/releases).

**Download examples** with curl for Mac OS X and Linux binaries
```sh
# ...download & extract Mac OS X binary
curl -L "https://packages.cloudfoundry.org/stable?release=macosx64-binary&version=v7&source=github" | tar -zx
# ...or Linux 64-bit binary
curl -L "https://packages.cloudfoundry.org/stable?release=linux64-binary&version=v7&source=github" | tar -zx
# ...move it to /usr/local/bin or a location you know is in your $PATH
mv cf7 /usr/local/bin
# ...copy tab completion file on Ubuntu (takes affect after re-opening your shell)
sudo curl -o /usr/share/bash-completion/completions/cf7 https://raw.githubusercontent.com/cloudfoundry/cli-ci/master/ci/installers/completion/cf7
# ...and to confirm your cf CLI version
cf7 --version
```

##### Edge binaries
Edge binaries are *not intended for wider use*; they're for developers to test new features and fixes as they are 'pushed' and passed through the CI.
Follow these download links for [Mac OS X 64 bit](https://packages.cloudfoundry.org/edge?arch=macosx64&version=v7&source=github), [Windows 64 bit](https://packages.cloudfoundry.org/edge?arch=windows64&version=v7&source=github) and [Linux 64 bit](https://packages.cloudfoundry.org/edge?arch=linux64&version=v7&source=github).

### Version Switching
When the v7 CLI GA's, the binary will be renamed from `cf7` to `cf`. Existing workflows that switch back and forth between the v7 and v6 CLIs will need to be updated to accomodate this change.

Below you'll find instructions for each of the package managers we support.
For those who use the raw binaries downloaded from GitHub or via CLAW, you must set up for your own infrastructure/scripts for swapping back and forth. 

#### Switching CLI versions Using Brew
- Assuming you've installed both the v6 and v7 CLIs...
  - `brew install cf-cli`
  - `brew install cf-cli@7`
- Currently on v6, want to switch to v7:
  - `brew link cf-cli@7 --overwrite`
Currently on v7, want to switch to v6:
  - `brew link cf-cli --overwrite`

#### Switching CLI versions Using Yum or Apt
We're working on a robust soluiton that will faciliate more seamless switching via these package managers, but for now you must uninstall one version of the CLI and install the other version of the CLI to switch between them. 
- Currently on v6, want to switch to v7:
  - `sudo yum remove cf-cli` **-OR-** `sudo apt-get remove cf-cli`
  - `yum install cf7-cli` **-OR-** `sudo apt-get cf7-cli`
Currently on v7, want to switch to v6:
  - `sudo yum remove cf7-cli` **-OR-** `sudo apt-get remove cf7-cli`
  - `sudo yum install cf-cli` **-OR-** `sudo apt-get cf-cli` 

#### Switching CLI versions Pulled via GitHub or CLAW
There's more than one solution available for doing this. We'll describe one that's been proven to work.
- Download the v6 and v7 binaries into separate directories (for example `~/workspace/V6` and `~/workspace/v7`)
- Write a script that can be invoked to switch the `PATH` and `CF_HOME` environment variables


## Known Issues

* On Windows in Cygwin and Git Bash, interactive password prompts (in `cf login`) do not hide the password properly from stdout ([issue #1835](https://github.com/cloudfoundry/cli/issues/1835)). Please use an alternative command (non-interactive authentication `cf auth` instead of `cf login`) to work around this. Or, use the Windows `cmd` command line.
* On Windows, `cf ssh` may not display correctly if the `TERM` is not set. We've found that setting `TERM` to `msys` fixes some of these issues.
* On Windows, `cf ssh` will hang when run from the MINGW32 or MINGW64 shell. A workaround is to use PowerShell instead.
* CF CLI/GoLang do not use OpenSSL. Custom/Self Signed Certificates need to be [installed in specific locations](https://docs.cloudfoundry.org/cf-cli/self-signed.html) in order to `login`/`auth` without `--skip-ssl-validation`.
* API tracing to terminal (using `CF_TRACE=true`, `-v` option or `cf config --trace`) doesn't work well with some CLI plugin commands. Trace to file works fine. On Linux, `CF_TRACE=/dev/stdout` works too. See [this Diego-Enabler plugin issue](https://github.com/cloudfoundry-attic/Diego-Enabler/issues/6) for more information.
* .cfignore used in `cf push` must be in UTF-8 encoding for CLI to interpret correctly. ([issue #281](https://github.com/cloudfoundry/cli/issues/281#issuecomment-65315518))
* On Linux, when encountering message "bash: .cf: No such file or directory", ensure that you're using the [correct binary or installer for your architecture](https://askubuntu.com/questions/133389/no-such-file-or-directory-but-the-file-exists).

## Filing Issues & Feature Requests

First, update to the [latest cli](https://github.com/cloudfoundry/cli/releases)
and try the command again.

If the error remains or feature still missing, check the [open issues](https://github.com/cloudfoundry/cli/issues) and if not already raised please file a new issue with the requested details.

## Plugin Development

The CF CLI supports external code execution via the plugins API. For more
information follow:

* [The CF CLI plugin development guide](https://github.com/cloudfoundry/cli/tree/master/plugin/plugin_examples)
* [The official plugins repository](https://plugins.cloudfoundry.org/)

When importing the plugin code use `import "code.cloudfoundry.org/cli/plugin"`.
Older plugins that import `github.com/cloudfoundry/cli/plugin` will still work
as long they vendor the plugins directory.

## Contributing & Build Instructions

Please read the [contributors' guide](.github/CONTRIBUTING.md)

If you'd like to submit updated translations, please see the [i18n README](https://github.com/cloudfoundry/cli/blob/master/cf/i18n/README-i18n.md) for instructions on how to submit an update.
