# KubeCM

[![Build Status](https://travis-ci.org/sunny0826/kubecm.svg?branch=master)](https://travis-ci.org/sunny0826/kubecm)
[![Go Report Card](https://goreportcard.com/badge/github.com/sunny0826/kubecm)](https://goreportcard.com/report/github.com/sunny0826/kubecm)
![GitHub](https://img.shields.io/github/license/sunny0826/kubecm.svg)
[![GitHub release](https://img.shields.io/github/release/sunny0826/kubecm)](https://github.com/sunny0826/kubecm/releases)

```text
KubeConfig Manager
 _          _
| | ___   _| |__   ___  ___ _ __ ___
| |/ / | | | '_ \ / _ \/ __| '_ \ _ \
|   <| |_| | |_) |  __/ (__| | | | | |
|_|\_\\__,_|_.__/ \___|\___|_| |_| |_|

Find more information at: https://github.com/sunny0826/kubecm

Usage:
  kubecm [flags]
  kubecm [command]

Available Commands:
  add         Merge configuration file with $HOME/.kube/config
  completion  Generates bash/zsh completion scripts
  delete      Delete the specified context from the kubeconfig
  help        Help about any command
  merge       Merge the kubeconfig files in the specified directory
  namespace   Switch or change namespace interactively
  rename      Rename the contexts of kubeconfig
  switch      Switch Kube Context interactively
  version     Print version info

Flags:
      --config string   path of kubeconfig (default "$HOME/.kube/config")
  -h, --help   help for kubecm

Use "kubecm [command] --help" for more information about a command.
```

## Quick Start

### Install

#### Homebrew

```bash
brew install sunny0826/tap/kubecm
```

#### Download the binary

[![GitHub release](https://img.shields.io/github/release/sunny0826/kubecm)](https://github.com/sunny0826/kubecm/releases)

```bash
# linux x86_64
curl -Lo kubecm.tar.gz https://github.com/sunny0826/kubecm/releases/download/v${VERSION}/kubecm_${VERSION}_Linux_x86_64.tar.gz
# macos
curl -Lo kubecm.tar.gz https://github.com/sunny0826/kubecm/releases/download/v${VERSION}/kubecm_${VERSION}_Darwin_x86_64.tar.gz
# windows
curl -Lo kubecm.tar.gz https://github.com/sunny0826/kubecm/releases/download/v${VERSION}/kubecm_${VERSION}_Windows_x86_64.tar.gz

# linux & macos
tar -zxvf kubecm.tar.gz kubecm
cd kubecm
sudo mv kubecm /usr/local/bin/

# windows
# Unzip kubecm.tar.gz
# Add the binary in to your $PATH
```

### Auto-Completion

#### bash

```bash
# bash
kubecm completion bash > ~/.kube/kubecm.bash.inc
printf "
# kubecm shell completion
source '$HOME/.kube/kubecm.bash.inc'
" >> $HOME/.bash_profile
source $HOME/.bash_profile
```

#### zsh

```bash
# add to $HOME/.zshrc 
source <(kubecm completion zsh)
# or
kubecm completion zsh > "${fpath[1]}/_kubecm"
```

### Interactive operation

![Interactive](dosc/Interaction.gif)

### Add configuration to `$HOME/.kube/config`

```bash
# Merge example.yaml with $HOME/.kube/config.yaml
kubecm add -f example.yaml 

# Merge example.yaml and name contexts test with $HOME/.kube/config.yaml
kubecm add -f example.yaml -n test

# Overwrite the original kubeconfig file
kubecm add -f example.yaml -c
```

### Merge the kubeconfig

```bash
# Merge kubeconfig in the directory
kubecm merge -f dir

# Merge kubeconfig in the directory and overwrite the original kubeconfig file
kubecm merge -f dir -c
```

### Switch Kube Context interactively

```bash
# Switch Kube Context interactively
kubecm switch
```
![switch](dosc/switch.gif)

### Delete context

```bash
# Delete the context interactively
kubecm delete
# Delete the context
kubecm delete my-context
```
### Rename context

```bash
# Renamed the context interactively
kubecm rename
# Renamed dev to test
kubecm rename -o dev -n test
# Renamed current-context name to dev
kubecm rename -n dev -c
```
 
### Switch namespace

You can switch namespace or switch namespace interactively

```bash
# Switch Namespace interactively
kubecm namespace
# or
kubecm ns
# change to namespace of kube-system
kubecm ns kube-system
``` 
![ns](dosc/ns.gif)

## Video

[[Video introduction](https://www.bilibili.com/video/av88259938/)]: https://www.bilibili.com/video/av88259938/


## Contribute

Feel free to open issues and pull requests. Any feedback is highly appreciated!

## Thanks

- [JetBrains IDEs](https://www.jetbrains.com/?from=kubecm)

<p align="center">
  <a href="https://www.jetbrains.com/?from=kubecm" title="前往官网了解JetBrains出品的IDEs">
    <img src="dosc/jetbrains.svg" width="128" alt="JetBrains logo">
  </a>
</p>
