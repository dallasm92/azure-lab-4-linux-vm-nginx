# Azure Lab 4: Ubuntu VM and Nginx Validation

## Objective

Deploy a Linux virtual machine in Azure, reuse the earlier network foundation, connect over SSH, install Nginx, open the required inbound web port in the network security group, and confirm HTTP access from a browser.

## Environment

- Platform: Microsoft Azure
- Subscription shown in evidence: `Azure subscription 1`
- Region: `East US`
- Evidence source: private screenshots captured during the Azure portal and SSH workflow

## Azure Services Used

- Resource Groups
- Virtual Machines
- Virtual Network and Subnets
- Network Interface
- Public IP address
- Network Security Group

## Resource Details

- Resource group: `rg-azure-lab-network`
- Virtual network: `vnet-lab-network`
- Subnet used by the VM: `public-subnet`
- Network security group: `nsg-lab-network`
- Virtual machine: `vm-lab-01`
- Public IP resource: `vm-lab-01-ip`
- Guest OS family: Ubuntu Server 24.04 LTS
- Web service installed for validation: Nginx

## Lab Relationship

This lab builds on the earlier Azure network foundation rather than starting from scratch. The VM was attached to the existing VNet and public subnet, and the NSG from the network lab was updated to allow web traffic for validation.

## Steps Performed

1. Opened the Azure virtual machine creation workflow.
2. Selected an Ubuntu Server 24.04 LTS image for the VM deployment.
3. Created a new SSH key pair as part of the Azure deployment flow.
4. Deployed the VM into `rg-azure-lab-network`.
5. Attached the VM to the existing `vnet-lab-network` and `public-subnet`.
6. Confirmed Azure created the VM, network interface, and public IP resources.
7. Connected to the VM over SSH.
8. Installed Nginx on the Ubuntu VM.
9. Reviewed the existing NSG attached to `public-subnet`.
10. Added an inbound rule to allow HTTP traffic on TCP port `80`.
11. Confirmed the VM network settings and NSG relationship.
12. Validated the public web response by reaching the default Nginx page from a browser.

## Validation

- SSH access to the Linux VM succeeded.
- `sudo apt install nginx -y` completed successfully on the VM.
- The NSG attached to `public-subnet` was updated to allow inbound HTTP.
- A browser request to the VM public IP returned the default `Welcome to nginx!` page.

## What I Learned

- Azure VM deployment becomes easier once the network foundation already exists and can be reused cleanly.
- Subnet-level NSG design makes it straightforward to add workload-specific access later without rebuilding the network.
- A simple HTTP validation is a fast way to prove that the compute, networking, and security layers are working together.
- Reusing a prior lab's VNet and NSG turns separate Azure exercises into a more realistic sequence instead of isolated portal clicks.

## Problems Encountered / Notes

- The private evidence set includes account-banner details and public-IP exposure, so the raw screenshots were not copied directly into this public repo.
- The NSG already contained SSH-focused rules from the earlier network lab, and this lab added web access for application validation.
- One part of the evidence shows experimentation with a custom inbound web port before the final HTTP validation path; the final public validation captured here is the successful Nginx response over standard HTTP.

## Cost Control and Cleanup

- This lab used a single Linux VM and reused the earlier network foundation.
- No load balancer, Application Gateway, or multi-VM design was introduced.
- Cleanup state is not claimed here because the private evidence set does not prove final deletion of every resource.

## Repo Structure

- `README.md`
  - main lab walkthrough and outcome
- `LAB_SUMMARY.md`
  - short version for quick portfolio review
- `EVIDENCE_NOTES.md`
  - explains why the screenshot set is currently kept private

## Outcome

The lab produced a working Azure Linux VM deployment with SSH administration, an Nginx installation, and successful inbound HTTP validation through the existing network and NSG design.
