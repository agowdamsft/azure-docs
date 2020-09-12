---
 title: Platform Software Management with SGX quote helper daemon set
 description: Daemon set for better managing the Intel PSW
 services: virtual-machines
 author: agowdamsft
 ms.service: virtual-machines
 ms.subservice: container-service
 ms.topic: overview
 ms.date: 9/14/2020
 ms.author: agowdamsft
---

# Platform Software Management with SGX quote helper daemon set

There are other advantages, along with the initial set of motivations, of moving into out-of-proc mode as listed below. 

Improved experience of updating the trusted components 

The trusted SW components - Quoting Enclave (QE) & Provisioning Certificate Enclave (PCE), are part of the TCB and must be up-to-date to maintain the attestation requirements. Taking the ownership of managing the trusted SW components transparently, will help in maintaining the up-to-date security posture related to updating in-TCB SW. Thus, customer's experience with handling the security update will be improved. 

![The confidential container converstion](./media/donotuse-sgx101-enclaveawarecontainers.jpg)


1. No attestation failures due to out-of-date PSW components 

    Since ACC manages the updates to PSW components customers will never face attestation failures due to up-to-date trusted SW components. 

2. Better utilization of EPC memory 

With in-proc attestation mode each enclave application needs to instantiate the copy of QE and PCE for remote attestation. Since all the instance of QE and PCE serve the same purpose they can be centralized which will help in minimizing the EPC memory required by each enclave application. 

3. Safeguards against Kernel enforcement  

When the SGX driver is up streamed into Linux kernel there will be enforcement for an enclave to have higher privilege in order to invoke PCE, which will break the enclave application running in in-proc mode as by default this permission is not provided. To grant this privilege to an enclave application would require changes to the application installation process. Out-of-proc model doesn’t suffer from this problem as the entity responsible (AESM), provided by Intel, will be installed with this privilege. 

4. Detect backward compatibility with PSW & DCAP 
As PSW components installation is under our control, we can do better job at testing the compatibility with version of DCAP driver present on the AKS image every time there is an updated either to PSW components or DCAP driver. This will help us detect the compatibility issues upfront and address them before letting them be deployed or available to customer’s workflow.

