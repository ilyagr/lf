## README for this fork of `lf`

This is an unsupported and unofficial fork.
The official repository for the `lf` file manager is at https://github.com/gokcehan/lf
This fork is intended to be a preview of upcoming `lf` features.
It also includes a few additional minor features that I like but may not be added to the official versions.

Currently, it adds the following to the official version of `lf`:

- The [`:keys` command](https://github.com/gokcehan/lf/pull/918)
- All of my open pull requests from https://github.com/gokcehan/lf/pull/
- Possibly additinal half-baked minor features that may lack sufficient documentation.

### Fork installation

Occasionally, I make binaries available at https://github.com/ilyagr/lf/releases/.
My plan is that release `r28-ig2` in my repo would be the second release I make that is based on the `r28` official `lf` release.
It may or may not include a description of which features it includes.
Most of its features will hopefully be a preview of the `r29` official version of `lf`.

Alternatively, compiling Go programs is spectacularly fast and easy.
The steps would be:

1. Install Go. I use `sudo apt install golang-1.19` on Debian. See http://go.dev for official instructions.
2. Clone this repo: `git clone https://github.com/ilyagr/lf && cd lf`.
3. Run `CGO_ENABLED=0 go build`. If all is well, it will seem like nothing happened. An `lf` binary will appear in the same directory.

   Alternatively, the [lengthier command below](https://github.com/ilyagr/lf#installation) will result in a smaller binary.

4. Copy the resulting `lf` binary to somewhere in your PATH.

### Fork details and warnings

The `ilya` branch should be a merge of several feature branches.
Each commit should describe what it does.
This is a little difficult to see in gihub's view of repo history.
You may need to clone the repo and use another tool (`git log`, `gitk`, `tig`).

WARNING: I force-push the `ilya` branch regularly and without warning, whenever I update any of the branches or rebase them on top of a new upstream commit.
This is because I use [`jj`](https://github.com/martinvonz/jj) to manage this repo.
There's no way to find out where the `ilya` branch was previously other than the taggged releases.
You can see a diff between a tag and the present `ilya` branch via an URL like https://github.com/ilyagr/lf/compare/ilya..r28-ig1.

Original README follows.

---------------------------------------------------

# LF

[Google Groups](https://groups.google.com/forum/#!forum/lf-fm)
| [Wiki](https://github.com/gokcehan/lf/wiki)
| [#lf](https://web.libera.chat/#lf) (on Libera.Chat)
| [#lf:matrix.org](https://matrix.to/#/#lf:matrix.org) (with IRC bridge)

[![Go Report Card](https://goreportcard.com/badge/github.com/gokcehan/lf)](https://goreportcard.com/report/github.com/gokcehan/lf)
[![Go Reference](https://pkg.go.dev/badge/github.com/gokcehan/lf.svg)](https://pkg.go.dev/github.com/gokcehan/lf)

> This is a work in progress. Use at your own risk.

`lf` (as in "list files") is a terminal file manager written in Go with a heavy inspiration from ranger file manager.
See [faq](https://github.com/gokcehan/lf/wiki/FAQ) for more information and [tutorial](https://github.com/gokcehan/lf/wiki/Tutorial) for a gentle introduction with screencasts.

![multicol-screenshot](http://i.imgur.com/DaTUenu.png)
![singlecol-screenshot](http://i.imgur.com/p95xzUj.png)

## Features

- Cross-platform (Linux, macOS, BSDs, Windows)
- Single binary without any runtime dependencies
- Fast startup and low memory footprint due to native code and static binaries
- Asynchronous IO operations to avoid UI locking
- Server/client architecture and remote commands to manage multiple instances
- Extendable and configurable with shell commands
- Customizable keybindings (vi and readline defaults)
- A reasonable set of other features (see the [documentation](https://pkg.go.dev/github.com/gokcehan/lf))

## Non-Features

- Tabs or windows (better handled by window manager or terminal multiplexer)
- Builtin pager/editor (better handled by your pager/editor of choice)

## Installation

See [packages](https://github.com/gokcehan/lf/wiki/Packages) for community maintained packages.

See [releases](https://github.com/gokcehan/lf/releases) for pre-built binaries.

Building from the source requires [Go](https://go.dev/).

On Unix (Go version < 1.17):

```bash
env CGO_ENABLED=0 GO111MODULE=on go get -u -ldflags="-s -w" github.com/gokcehan/lf
```

On Unix (Go version >= 1.17):

```bash
env CGO_ENABLED=0 go install -ldflags="-s -w" github.com/gokcehan/lf@latest
```

On Windows `cmd` (Go version < 1.17):

```cmd
set CGO_ENABLED=0
set GO111MODULE=on
go get -u -ldflags="-s -w" github.com/gokcehan/lf
```

On Windows `cmd` (Go version >= 1.17):

```cmd
set CGO_ENABLED=0
go install -ldflags="-s -w" github.com/gokcehan/lf@latest
```

On Windows `powershell` (Go version < 1.17):

```powershell
$env:CGO_ENABLED = '0'
$env:GO111MODULE = 'on'
go get -u -ldflags="-s -w" github.com/gokcehan/lf
```

On Windows `powershell` (Go version >= 1.17):

```powershell
$env:CGO_ENABLED = '0'
go install -ldflags="-s -w" github.com/gokcehan/lf@latest
```

## Usage

After the installation `lf` command should start the application in the current directory.

Run `lf -help` to see command line options.

Run `lf -doc` to see the [documentation](https://pkg.go.dev/github.com/gokcehan/lf).

See [etc](etc) directory to integrate `lf` to your shell and/or editor.
Example configuration files along with example colors and icons files can also be found in this directory.

See [integrations](https://github.com/gokcehan/lf/wiki/Integrations) to integrate `lf` to other tools.

See [tips](https://github.com/gokcehan/lf/wiki/Tips) for more examples.

## Contributing

See [contributing](https://github.com/gokcehan/lf/wiki/Contributing) for guidelines.
