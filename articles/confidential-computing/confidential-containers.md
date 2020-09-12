---
 title: Confidential Containers on AKS
 description: Unmodified containers support on confidential containers
 services: virtual-machines
 author: agowdamsft
 ms.service: virtual-machines
 ms.subservice: container-service
 ms.topic: overview
 ms.date: 9/14/2020
 ms.author: agowdamsft
---

# Confidential Containers

The term “confidential containers” refers to docker application (new or existing) containers packaged with additional components if necessary to run on the hardware that provides strong protections of Confidential Computing as listed above and meets the below list of criteria to improve the overall security posture of the container application and the data-in-use.  

1. data integrity 
2. data confidentiality
3. code integrity
4. hardware-based assurances
5. hardware root of trust
6. software code transparency of the supporting abstraction layer

In the context of confidential containers, a hardware-based TEE is an important component that is used to provide strong assurances of data integrity, data confidentiality, and code integrity through measurement of TCB components. These attributes provide assurances to the application developers, security officers and the parties monitoring the confidentiality of the container that application code is not tampered with after the container image is signed, and is not vulnerable to unauthorized modification at run-time. This isolated and measured execution also from the hardware and software layers elevates the security posture and integrity of the container application and its computations to its expected outcomes.

Confidential containers allows bringing an existing container applications and running them in teh secured enclaves with no modifications to the applications. Applications that are programmed with Python, Java, Node etc.. or even off the shelf application like NGinx, Redis Cache etc.. 

![The confidential container converstion](./media/confcondeployprocess.jpg)

## Confidential Container Enablers

To run existing docker container application an abstraction layer or SGX software is required. This is enabled and fully supported for AKS orchestrations through Azure Partners and Open Source Software projects

### Partner Enablers
#### Scone


https://azuremarketplace.microsoft.com/en-us/marketplace/apps/scontainug1595751515785.scone?tab=Overview

https://sconedocs.github.io/aks/

#### Fortanix

#### Anjuna

### OSS Enablers 

#### Graphene

#### Occlum

### Get In Touch
> Have questions with your implementation or want to become an enabler? please reach out to confcontainers@microsoft.com