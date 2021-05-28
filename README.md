# Let's Play with Apache Pulsar

_Apache Pulsar is a cloud-native, distributed messaging and streaming platform originally created at Yahoo! and now a top-level Apache Software Foundation project_

source: <https://pulsar.apache.org/en/>

## Create a new Ubuntu VM on Azure

```text
$ az group create --name pk-group-pulsar-01 --location westeurope
...
```

```text
$ az vm create \
  --resource-group pk-group-pulsar-01 \
  --name pk-vm-pulsar-01 \
  --image UbuntuLTS \
  --admin-username radicel \
  --generate-ssh-keys
{
  ...
  "publicIpAddress": <Public IP adrress>
  ...
}
```

or

```text
$ az vm show --show-details --name pk-vm-pulsar-01 --resource-group pk-group-pulsar-01
{
  ...
  "publicIps": <Public IP adrress>
  ...
}
```

```text
$ ssh radicel@<Public IP adrress>
radicel@pk-vm-pulsar-01:~$
```

```text
$ sudo apt-get update
...
$ sudo apt-get upgrade -y
...
```

## Add Laptop SSH Public Key for VS Code Remote Development

```text
USER@MACHINE MINGW64 ~
$ cd ~/.ssh/

UW31RY@WPU8L0058343 MINGW64 ~/.ssh
$ ls
... config ... id_rsa.pub ...

UW31RY@WPU8L0058343 MINGW64 ~/.ssh
$ cat id_rsa.pub
ssh-rsa AAAA...@mail.com
```

Copy the `ssh-rsa AAAA...@mail.com` string in the clipboard

```text
radicel@pk-vm-pulsar-01:~$ cd ~/.ssh/

radicel@pk-vm-pulsar-01:~/.ssh$ vi vi authorized_keys
```

Paste the `ssh-rsa AAAA...@mail.com` string in the clipboard at the end of the `authorized_keys` file.

```text
UW31RY@WPU8L0058343 MINGW64 ~/.ssh
$ vi config
```

Add the following lines at the end of the `config` file:

```text
Host <Public IP adrress>
  HostName <Public IP adrress>
  User radicel
  IdentityFile ~/.ssh/id_rsa
```

```text
UW31RY@WPU8L0058343 MINGW64 ~/.ssh
$ ssh radicel@<Public IP adrress>
radicel@pk-vm-pulsar-01:~$
```

## Install Java

## Install Pulsar
