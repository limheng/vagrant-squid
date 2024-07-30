# vagrant-squid

This guide demonstrates how to quickly set up a virtualized Debian environment using Vagrant and VirtualBox. We'll install squid within this environment, creating an isolated development environment for proxy testing.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)

## Prerequisites

1. [Virtualbox](https://virtualbox.org/) installed on your machine.
2. [Vagrant](https://vagrantup.com/) installed on your machine.

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/limheng/vagrant-squid
   cd vagrant-squid
   ```

## Usage

1. Initiate virtual environment:

   ```bash
   vagrant up
   ```

2. Access virtual machine:

   ```bash
   vagrant ssh
   ```

3. Check squid status:

   ```bash
   sudo systemctl status squid

   ```

4. Check logs:

   ```bash
   export http_proxy=http://192.168.33.10:3128
   export https_proxy=http://192.168.33.10:3128
   curl -I http://example.com
   sudo tail -f /var/log/squid/access.log

   ```
