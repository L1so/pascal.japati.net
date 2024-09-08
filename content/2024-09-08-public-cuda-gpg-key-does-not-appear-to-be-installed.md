---
title: Public CUDA GPG Key does not appear to be installed
date: 2024-09-08
taxonomies:
  tags: [linux, tech]
---
I once encountered this following problem while trying to install cuDNN (NVIDIA CUDA® Deep Neural Network library).

```
prepare to decompress cudnn-local-repo-ubuntu2204-8.5.0.96_1.0-1_amd64.deb  ...
decompressing cudnn-local-repo-ubuntu2204-8.5.0.96 (1.0-1) and overriding (1.0-1) ...
setup cudnn-local-repo-ubuntu2204-8.5.0.96 (1.0-1) ...

The public CUDA GPG key does not appear to be installed.
To install the key, run this command:
sudo cp /var/cudnn-local-repo-ubuntu2204-8.5.0.96/cudnn-local-7ED72349-keyring.gpg /usr/share/keyrings/
```
It seems the installation process lack the public CUDA GPG key, this makes the installation process go awry—I decided to search the net to seek the workaround or solution.

Turns out that there exist the GPG key, the problem is the naming is not what CUDA package expect, so simply renaming them (I use `cp`).

```
sudo cp /var/cudnn-local-repo-ubuntu2204-8.5.0.96/cudnn-local-7ED72349-keyring.gpg /usr/share/keyrings/cuda-archive-keyring.gpg
```
Boom ! Back to business :)