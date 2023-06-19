# Prerequisites

## Oracle Cloud infrastructure

This tutorial uses [Oracle Cloud infrastructure](https://cloud.oracle.com/) [free tier](https://www.oracle.com/cloud/free/) and Terraform to provision compute infrastructure required to bootstrap a Kubernetes cluster.

## Oracle Cloud Infrastructure SDK

### Install the Oracle Cloud SDK

Follow the Oracle Cloud SDK [documentation](https://docs.oracle.com/en-us/iaas/Content/API/SDKDocs/cliinstall.htm) to install and configure the `oci` command line utility.

#### Use the OCI CLI Container for the `oci` command [optional]
This step assumes you have docker or podman installed.

I will be using the [OCI CLI Container Image](https://docs.oracle.com/en-us/iaas/Content/API/SDKDocs/clicontainer.htm) with podman (aliased as docker).

1. Create the OCI data directory

```sh
mkdir $HOME/.oci
````

2. Create the container overriding the default entrypoint with /bin/bash so the container does not exit on run.

```sh
docker run --name oci -d -it -v "$HOME/.oci:/oracle/.oci" --entrypoint /bin/bash ghcr.io/oracle/oci-cli:latest
```
> We're naming the container *oci* (`--name`) running it in detached mode (`-d`), interactive (`-i`) tty (`-t`), mapping (`-v`) our `$HOME/.oci` to `/oracle/.oci` in the container and running `/bin/bash` in the container which will use the oci-cli image:latest

3. Add an alias in your shell rc file `~/.zshrc` etc

```sh
alias oci='docker exec -it oci oci'
source ~/.zshrc
```
> This step aliases `oci` in your terminal to run `oci` in the container named *oci*.

4. Verify the oci command works
```sh 
oci --version
3.29.0
```

## OCI CLI Set Up

### Set up the oci-cli config file
Refer to the [instructions](https://docs.oracle.com/en-us/iaas/Content/API/Concepts/apisigningkey.htm) to generate an API Signing Key.

This will also create a config for you to put in `$HOME/.oci/config`

Alternatively you can run `oci setup config`

### Verify your credentials are working
```sh
oci os ns get
{
    "data": "demo-tenancy"
}
```

Next: [Installing the Client Tools](02-client-tools.md)
