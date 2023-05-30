# Kubernetes The Hard Way - Terraform - Oracle Cloud Infrastructure

The goal of this is repo is to follow [Kubernetes The Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way) but using Terraform to provision the cloud infrastructure on [Oracle Cloud Infrastructure's free tier.](https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier.htm)

## Free Tier Resources

Oracle provides a decent selection of ["Always Free"](https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier_topic-Always_Free_Resources.htm) cloud resources which are great for creating and testing new projects.

For our Kubernetes cluster we'll be taking advantage of the Ampere A1 Compute instances which provide a maximum of 4 OCPUs and 24 GB of memory.
