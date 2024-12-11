---
layout: post
title:  "Using Micromamba"
author: at
categories: [ Jekyll, tutorial ]
image: assets/images/waves.jpg
featured: true
hidden: true
---


[Micromamba](https://mamba.readthedocs.io/en/latest/installation/micromamba-installation.html#) is a fast, lightweight version of the Mamba package manager. 
Unlike Miniconda, it comes as a single executable with no default Python installation or base environment, making it perfect for minimal installations.

## Why Micromamba?

Traditional package managers like Conda can be slow and heavy. Micromamba offers:
- Fast installation and package resolution
- Minimal disk space usage
- No base environment overhead
- Full compatibility with Conda packages and channels

## Installation

### Linux and macOS

The recommended way to install Micromamba is using the automatic installation script:

```bash
"${SHELL}" <(curl -L micro.mamba.pm/install.sh)
```

For macOS users, you can alternatively use Homebrew:

```bash
brew install micromamba
```

After installation, you'll need to restart your shell or source your configuration file:

```bash
source ~/.bashrc  # for bash
# or
source ~/.zshrc   # for zsh
```

## Basic Usage

### Setting up channels

First, let's configure Micromamba to use conda-forge and bioconda channels:

```bash
micromamba config append channels conda-forge
micromamba config append channels bioconda
micromamba config set channel_priority strict
```

### Creating an Environment

Let's create and activate a new environment called `bioenv`:

```bash
micromamba create -n bioenv
micromamba activate bioenv
```

### Installing Packages

Now let's install `seqfu` from the bioconda channel:

```bash
micromamba install -c bioconda seqfu
```

### Common Commands

Here are some essential Micromamba commands:

```bash
# List environments
micromamba env list

# Search for a package
micromamba search -c bioconda seqfu

# Update packages
micromamba update --all

# Remove a package
micromamba remove package_name

# Delete an environment
micromamba env remove -n bioenv
```

### Updating Micromamba

You can update Micromamba itself using:

```bash
micromamba self-update
```

## Important Notes

- Micromamba uses `MAMBA_ROOT_PREFIX` to store environments (default is `~/micromamba`)
- Unlike Conda, there's no pre-configured base environment
- Micromamba is fully compatible with Conda packages and channels
- Configuration files (.condarc/.mambarc) are read if present but not shipped by default

## Troubleshooting

If you encounter issues:
1. Ensure your `MAMBA_ROOT_PREFIX` is set correctly
2. Check if the channels are properly configured
3. Make sure you've activated the correct environment
4. Try running `micromamba clean --all` to clear the cache

Now you have a lightweight, fast package manager ready for your bioinformatics work. Happy computing!