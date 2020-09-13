---
 title: Enclave aware containers
 description: enclave ready application containers support on Azure Kubernetes Service (AKS)
 services: virtual-machines
 author: agowdamsft
 ms.service: virtual-machines
 ms.subservice: container-service
 ms.topic: overview
 ms.date: 9/14/2020
 ms.author: agowdamsft
---

# Enclave Aware Containers

An enclave is a protected memory region that provides confidentiality for data and code execution. It is an instance of a Trusted Execution Environment (TEE) which is secured by hardware. Confidential computing nodes on AKS utilizes [Intel Software Guard Extensions (SGX)](https://software.intel.com/en-us/sgx) to create isolated enclave environments in the nodes between each container application.

Container applications developed specifically to run in these enclaves have two components:

1. An untrusted component (called the host) and
1. A trusted component (called the enclave).

![Enclave Aware Container Architecture](./media/aks/enclaveawarecontainer.png)

Enclave aware containers application architecture gives you the most control on the implementation while keeping the code footprint in the enclave to low. This less code in he enclave approach can help reduce the attack surface areas.   

## Enablers

### Open Enclave SDK
The Open Enclave SDK is a hardware-agnostic open source library for developing C, C++ applications that utilize Hardware-based Trusted Execution Environments. The current implementation provides support for Intel SGX as well as preview support for OP-TEE OS on ARM TrustZone.

Get started with Open Enclave based container application [here](https://github.com/openenclave/openenclave/tree/master/docs/GettingStartedDocs)

### Intel SGX SDK
Intel maintained software development kit for building SGX C, C++ based applications for both Linux and Windows (currently not supported by AKS confidential computing nodes) based workloads.

Get started with Intel SDX based applications [here](https://software.intel.com/content/www/us/en/develop/topics/software-guard-extensions/sdk.html)

### Confidential Consortium Framework (CCF)
The Confidential Consortium Framework (CCF) is an open-source framework for building a new category of secure, highly available, and performant applications that focus on multi-party compute and data. CCF can enable high-scale, confidential networks that meet key enterprise requirements — providing a means to accelerate production and enterprise adoption of consortium based blockchain and multi-party compute technology.

Get started with Azure confidential computing and CCF [here](https://github.com/Microsoft/CCF)

## Container Samples Implementations

[Azure samples for enclave aware containers on AKS](https://github.com/Azure-Samples/enclave-aware-container-samples)

<!-- LINKS - external -->
[Azure Attestation]: https://docs.microsoft.com/en-us/azure/attestation/


<!-- LINKS - internal -->
[DC Virtual Machine]: /confidential-computing/virtual-machine-solutions
[Confidential Containers]: /confidential-computing/containercompute/confidential-containers