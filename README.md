# Hexiosec Transfer CLI

Transfer command line interface

[![oclif](https://img.shields.io/badge/cli-oclif-brightgreen.svg)](https://oclif.io)
[![Version](https://img.shields.io/npm/v/trebuchet-cli.svg)](https://npmjs.org/package/trebuchet-cli)
[![Downloads/week](https://img.shields.io/npm/dw/trebuchet-cli.svg)](https://npmjs.org/package/trebuchet-cli)

<!-- toc -->
* [Hexiosec Transfer CLI](#hexiosec-transfer-cli)
* [Installation](#installation)
* [Usage](#usage)
* [CLI Configuration](#cli-configuration)
* [Commands](#commands)
<!-- tocstop -->

# Installation

Update your ~/.npmrc to use GitHub Packages for the `@hexiosec` namespace:

```
@hexiosec:registry=https://npm.pkg.github.com
```

If you have not already configured authentication for the GitHub Package registry, create a GitHub Personal Access Token (classic) and add it to your ~/.npmrc, using https://docs.github.com/en/packages/learn-github-packages/introduction-to-github-packages#authenticating-to-github-packages

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
@hexiosec/transfer-cli/0.0.4 darwin-arm64 node-v18.20.6
$ hxtransfer --help [COMMAND]
USAGE
  $ hxtransfer COMMAND
...
```
<!-- usagestop -->

# CLI Configuration

1. Go to [My Account](https://transfer.hexiosec.com/account) in Hexiosec Transfer.
2. Under **Create a new API Key** add a description and choose a validity, then click **Create**.
3. Add the API Key value to your environment under the variable `HXTRANSFER_API_KEY`.
4. If you are using a custom domain, set `HXTRANSFER_BASE_URL` to `https://transfer.your-custom-domain.com`. Your API Key will need to be from this domain as well.
5. Check the configuration using `hxtransfer config`.

# Commands

<!-- commands -->
* [`hxtransfer config`](#hxtransfer-config)
* [`hxtransfer help [COMMAND]`](#hxtransfer-help-command)
* [`hxtransfer send`](#hxtransfer-send)
* [`hxtransfer send file [FILES]`](#hxtransfer-send-file-files)
* [`hxtransfer send files [FILES]`](#hxtransfer-send-files-files)
* [`hxtransfer send message MESSAGE`](#hxtransfer-send-message-message)
* [`hxtransfer send msg MESSAGE`](#hxtransfer-send-msg-message)
* [`hxtransfer version`](#hxtransfer-version)

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

_See code: [src/commands/config/index.ts](https://github.com/hexiosec/transfer-cli/blob/v0.0.4/src/commands/config/index.ts)_

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

_See code: [src/commands/send/index.ts](https://github.com/hexiosec/transfer-cli/blob/v0.0.4/src/commands/send/index.ts)_

## `hxtransfer send file [FILES]`

Send one or more files.

```
USAGE
  $ hxtransfer send file [FILES...] [--json] [-c <value>] [-d <value>] [-e <value>] [--generate-password]

FLAGS
  -c, --count=<value>      [default: 5] Maximum download count
  -d, --desc=<value>       [default: Secure Files 27/03/2025] Transfer description
  -e, --exp=<value>        [default: 7] Expiry duration (days)
  --generate-password

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  Send one or more files.

ALIASES
  $ hxtransfer send file
```

## `hxtransfer send files [FILES]`

Send one or more files.

```
USAGE
  $ hxtransfer send files [FILES...] [--json] [-c <value>] [-d <value>] [-e <value>] [--generate-password]

FLAGS
  -c, --count=<value>      [default: 5] Maximum download count
  -d, --desc=<value>       [default: Secure Files 27/03/2025] Transfer description
  -e, --exp=<value>        [default: 7] Expiry duration (days)
  --generate-password

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  Send one or more files.

ALIASES
  $ hxtransfer send file
```

_See code: [src/commands/send/files.ts](https://github.com/hexiosec/transfer-cli/blob/v0.0.4/src/commands/send/files.ts)_

## `hxtransfer send message MESSAGE`

Send a secure message.

```
USAGE
  $ hxtransfer send message MESSAGE [--json] [-c <value>] [-d <value>] [-e <value>] [--generate-password] [-s
    <value>]

ARGUMENTS
  MESSAGE  Message body

FLAGS
  -c, --count=<value>      [default: 5] Maximum download count
  -d, --desc=<value>       [default: Secure Message 27/03/2025] Transfer description
  -e, --exp=<value>        [default: 7] Expiry duration (days)
  -s, --subject=<value>    [default: Secure Message] Message subject
  --generate-password

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  Send a secure message.

ALIASES
  $ hxtransfer send msg
```

_See code: [src/commands/send/message.ts](https://github.com/hexiosec/transfer-cli/blob/v0.0.4/src/commands/send/message.ts)_

## `hxtransfer send msg MESSAGE`

Send a secure message.

```
USAGE
  $ hxtransfer send msg MESSAGE [--json] [-c <value>] [-d <value>] [-e <value>] [--generate-password] [-s
    <value>]

ARGUMENTS
  MESSAGE  Message body

FLAGS
  -c, --count=<value>      [default: 5] Maximum download count
  -d, --desc=<value>       [default: Secure Message 27/03/2025] Transfer description
  -e, --exp=<value>        [default: 7] Expiry duration (days)
  -s, --subject=<value>    [default: Secure Message] Message subject
  --generate-password

GLOBAL FLAGS
  --json  Format output as json.

DESCRIPTION
  Send a secure message.

ALIASES
  $ hxtransfer send msg
```

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
