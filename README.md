# Hexiosec Transfer CLI

Command Line Interface for Hexiosec Transfer.

<!-- toc -->
* [Hexiosec Transfer CLI](#hexiosec-transfer-cli)
* [Prerequisites](#prerequisites)
* [Installation](#installation)
* [Usage](#usage)
* [Authentication & Configuration](#authentication--configuration)
* [Commands](#commands)
<!-- tocstop -->

# Prerequisites

Use of the [Hexiosec Transfer](https://hexiosec.com/transfer) CLI requires an active subscription to Hexiosec Transfer with API Access.

The CLI package requires [Node.js >=18](https://nodejs.org/en/download), and uses the [npm package manager](https://docs.npmjs.com/about-npm) for installation and upgrades.

# Installation

Update your ~/.npmrc to use GitHub Packages for the `@hexiosec` namespace:

```
@hexiosec:registry=https://npm.pkg.github.com
```

If you have not already configured authentication for the GitHub Package registry, create a GitHub Personal Access Token (classic) and add it to your ~/.npmrc, using the instructions in [Authenticating to GitHub Packages](https://docs.github.com/en/packages/learn-github-packages/introduction-to-github-packages#authenticating-to-github-packages).

This is done in GitHub from [Settings > tokens](https://github.com/settings/tokens), and needs, at a minimum, the `read:packages` scope.

```
//npm.pkg.github.com/:_authToken=YOUR_AUTH_TOKEN
```

# Usage

<!-- usage -->
```sh-session
$ npm install -g @hexiosec/transfer-cli
$ hxtransfer COMMAND
running command...
$ hxtransfer (--version)
@hexiosec/transfer-cli/0.0.6 darwin-arm64 node-v18.20.6
$ hxtransfer --help [COMMAND]
USAGE
  $ hxtransfer COMMAND
...
```
<!-- usagestop -->

# Authentication & Configuration

1. Go to [My Account](https://transfer.hexiosec.com/account) in Hexiosec Transfer.
2. Under **Create a new API Key** add a description and choose a validity, then click **Create**.
3. Add the API Key value to your environment under the variable `HXTRANSFER_API_KEY`.
4. If you are using a custom domain, set `HXTRANSFER_BASE_URL` to `https://transfer.your-custom-domain.com`. Your API Key will need to be from this domain as well.
5. Check the configuration using `hxtransfer config`.

## All Configuration Options

| Variable                         |            Default            | Description                                    |
| -------------------------------- | :---------------------------: | ---------------------------------------------- |
| `XDG_CONFIG_HOME`                |      Platform-dependent       | Configuration data store location              |
| `XDG_DATA_HOME`                  |      Platform-dependent       | Transfer data store location                   |
| `HXTRANSFER_API_KEY`             |             None              | User API Key                                   |
| `HXTRANSFER_BASE_URL`            | https://transfer.hexiosec.com | Base URL for the Hexiosec Transfer service     |
| `HXTRANSFER_DEFAULT_DOWNLOADS`   |               5               | Default setting for transfer maximum downloads |
| `HXTRANSFER_DEFAULT_EXPIRY_DAYS` |               7               | Default setting for transfer expiry (days)     |

# Commands

<!-- commands -->
* [`hxtransfer auth`](#hxtransfer-auth)
* [`hxtransfer config`](#hxtransfer-config)
* [`hxtransfer help [COMMAND]`](#hxtransfer-help-command)
* [`hxtransfer request ID`](#hxtransfer-request-id)
* [`hxtransfer request create SUBJECT`](#hxtransfer-request-create-subject)
* [`hxtransfer request download ID [DESTINATION]`](#hxtransfer-request-download-id-destination)
* [`hxtransfer request files ID`](#hxtransfer-request-files-id)
* [`hxtransfer request list`](#hxtransfer-request-list)
* [`hxtransfer send`](#hxtransfer-send)
* [`hxtransfer send files [FILES]`](#hxtransfer-send-files-files)
* [`hxtransfer send message MESSAGE`](#hxtransfer-send-message-message)
* [`hxtransfer version`](#hxtransfer-version)

## `hxtransfer auth`

Show authentication information.

```
USAGE
  $ hxtransfer auth [--json]

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  Show authentication information.
```

_See code: [src/commands/auth.ts](https://github.com/hexiosec/transfer-cli/blob/v0.0.6/src/commands/auth.ts)_

## `hxtransfer config`

Show current configuration.

```
USAGE
  $ hxtransfer config [--json]

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  Show current configuration.
```

_See code: [src/commands/config/index.ts](https://github.com/hexiosec/transfer-cli/blob/v0.0.6/src/commands/config/index.ts)_

## `hxtransfer help [COMMAND]`

Display help for hxtransfer.

```
USAGE
  $ hxtransfer help [COMMAND...] [-n]

ARGUMENTS
  COMMAND...  Command to show help for.

FLAGS
  -n, --nested-commands  Include all nested commands in the output.

DESCRIPTION
  Display help for hxtransfer.
```

_See code: [@oclif/plugin-help](https://github.com/oclif/plugin-help/blob/v6.2.27/src/commands/help.ts)_

## `hxtransfer request ID`

Show details of an existing sharing request.

```
USAGE
  $ hxtransfer request ID [--json]

ARGUMENTS
  ID  Public ID

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  Show details of an existing sharing request.

ALIASES
  $ hxtransfer req
  $ hxtransfer reqs
  $ hxtransfer requests
```

_See code: [src/commands/request/index.ts](https://github.com/hexiosec/transfer-cli/blob/v0.0.6/src/commands/request/index.ts)_

## `hxtransfer request create SUBJECT`

Create a new sharing request.

```
USAGE
  $ hxtransfer request create SUBJECT [--json] [-e <value>]

ARGUMENTS
  SUBJECT  Subject

FLAGS
  -e, --exp=<value>  Expiry date (format: yyyy/MM/dd HH:mm)

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  Create a new sharing request.

ALIASES
  $ hxtransfer req create
  $ hxtransfer reqs create
  $ hxtransfer requests create
```

_See code: [src/commands/request/create.ts](https://github.com/hexiosec/transfer-cli/blob/v0.0.6/src/commands/request/create.ts)_

## `hxtransfer request download ID [DESTINATION]`

Download received files from an existing sharing request.

```
USAGE
  $ hxtransfer request download ID [DESTINATION] [--json]

ARGUMENTS
  ID           Public ID
  DESTINATION  [default: .] Destination folder

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  Download received files from an existing sharing request.

ALIASES
  $ hxtransfer req download
  $ hxtransfer reqs download
  $ hxtransfer requests download
  $ hxtransfer req dl
  $ hxtransfer reqs dl
  $ hxtransfer requests dl
```

_See code: [src/commands/request/download.ts](https://github.com/hexiosec/transfer-cli/blob/v0.0.6/src/commands/request/download.ts)_

## `hxtransfer request files ID`

Show received files of an existing sharing request.

```
USAGE
  $ hxtransfer request files ID [--json]

ARGUMENTS
  ID  Public ID

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  Show received files of an existing sharing request.

ALIASES
  $ hxtransfer req files
  $ hxtransfer reqs files
  $ hxtransfer requests files
```

_See code: [src/commands/request/files.ts](https://github.com/hexiosec/transfer-cli/blob/v0.0.6/src/commands/request/files.ts)_

## `hxtransfer request list`

List active requests.

```
USAGE
  $ hxtransfer request list [--json]

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  List active requests.

ALIASES
  $ hxtransfer req list
  $ hxtransfer reqs list
  $ hxtransfer requests list
```

_See code: [src/commands/request/list.ts](https://github.com/hexiosec/transfer-cli/blob/v0.0.6/src/commands/request/list.ts)_

## `hxtransfer send`

List active transfers.

```
USAGE
  $ hxtransfer send [--json] [-e <value>]

FLAGS
  -e, --expiredDays=<value>  Expired days to include

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  List active transfers.
```

_See code: [src/commands/send/index.ts](https://github.com/hexiosec/transfer-cli/blob/v0.0.6/src/commands/send/index.ts)_

## `hxtransfer send files [FILES]`

Send one or more files.

```
USAGE
  $ hxtransfer send files [FILES...] [--json] [-c <value>] [-d <value>] [-e <value>] [--generate-password]

FLAGS
  -c, --count=<value>      Maximum download count
  -d, --desc=<value>       [default: Secure Files 28/03/2025] Transfer description
  -e, --exp=<value>        Expiry duration (days)
  --generate-password

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  Send one or more files.

ALIASES
  $ hxtransfer send file
```

_See code: [src/commands/send/files.ts](https://github.com/hexiosec/transfer-cli/blob/v0.0.6/src/commands/send/files.ts)_

## `hxtransfer send message MESSAGE`

Send a secure message.

```
USAGE
  $ hxtransfer send message MESSAGE [--json] [-c <value>] [-d <value>] [-e <value>] [--generate-password] [-s
    <value>]

ARGUMENTS
  MESSAGE  Message body

FLAGS
  -c, --count=<value>      Maximum download count
  -d, --desc=<value>       [default: Secure Message 28/03/2025] Transfer description
  -e, --exp=<value>        Expiry duration (days)
  -s, --subject=<value>    [default: Secure Message] Message subject
  --generate-password

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  Send a secure message.

ALIASES
  $ hxtransfer send msg
```

_See code: [src/commands/send/message.ts](https://github.com/hexiosec/transfer-cli/blob/v0.0.6/src/commands/send/message.ts)_

## `hxtransfer version`

```
USAGE
  $ hxtransfer version [--json] [--verbose]

FLAGS
  --verbose  Show additional information about the CLI.

GLOBAL FLAGS
  --json  Format output as json.

FLAG DESCRIPTIONS
  --verbose  Show additional information about the CLI.

    Additionally shows the architecture, node version, operating system, and versions of plugins that the CLI is using.
```

_See code: [@oclif/plugin-version](https://github.com/oclif/plugin-version/blob/v2.2.27/src/commands/version.ts)_
<!-- commandsstop -->
