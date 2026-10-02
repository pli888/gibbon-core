# Run local CI using act

## Introduction

Use [act](https://nektosact.com) to run GitHub Actions locally. This is useful for testing workflows before pushing changes to the repository.

## Installation

Install act using Homebrew or Macports on MacOS, or download the binary for your platform from the [releases page](https://github.com/nektos/act/releases).

## Usage

Use default image:
```bash
act push
```

Run gibbon CI pipeline:
```bash
act push -j test
```

Specify yml file to run:
```bash
act -W '.github/workflows/ci.yml'
```

Use a specific image for the runner:
```bash
act -W '.github/workflows/ci.yml' -P ubuntu-latest=ghcr.io/catthehacker/ubuntu:full-latest
```

Run CI in verbose mode:
```bash
act --verbose -W '.github/workflows/ci.yml' -P ubuntu-latest=ghcr.io/catthehacker/ubuntu:full-latest
```

Run CI in verbose mode and reuse container:
```bash
act --reuse --verbose -W '.github/workflows/ci.yml' -P ubuntu-latest=ghcr.io/catthehacker/ubuntu:full-latest
```

## Configuration file for act

Create a `.actrc` file in the root of the repository with the following content:
```
--container-architecture=linux/amd64
--action-offline-mode
--artifact-server-path=./.act-artifacts
```
