# Azure Lab 4: Azure Linux VM, SSH, and Nginx Validation

## Objective

Deploy a Linux virtual machine in Azure, place it in the existing lab network, connect over SSH with key-based authentication, install Nginx, correct an NSG port mistake, and confirm HTTP access from a browser.

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
- SSH key-based remote administration

## Resource Details

- Resource group: `rg-azure-lab-network`
- Virtual network: `vnet-lab-network`
- Subnet used by the VM: `public-subnet`
- Network security group: `nsg-lab-network`
- Virtual machine: `vm-lab-01`
- Public IP resource: `vm-lab-01-ip`
- Guest OS family: Ubuntu Server 24.04 LTS
- Web service installed for validation: Nginx
- Authentication method: SSH public key

## Lab Relationship

This lab builds directly on the earlier Azure network foundation rather than starting from scratch. The final VM deployment reused `vnet-lab-network`, placed the VM in `public-subnet`, relied on the subnet-level NSG from the networking lab, and then extended that NSG for web validation.

## Hiring Manager Quick View

| Review area | Evidence |
|---|---|
| Linux administration | SSH key access to Ubuntu Server 24.04 LTS and Nginx installation |
| Azure workload deployment | VM, NIC, public IP, VNet, subnet, and NSG relationship documented |
| Troubleshooting | Incorrect web rule on TCP `8080` corrected to Nginx's default TCP `80` listener |
| Validation | SSH succeeded, Nginx service was running, browser reached the default Nginx page |
| Security handling | Raw screenshots stay private because they include account banner and public-IP context |

## Steps Performed

1. Opened the Azure virtual machine creation workflow.
2. Corrected the VM wizard so the deployment reused the existing `vnet-lab-network` instead of creating a new VNet automatically.
3. Selected `public-subnet` intentionally so the VM would sit behind the subnet-level NSG that already restricted SSH access.
4. Selected an Ubuntu Server 24.04 LTS image for the VM deployment.
5. Created a new SSH key pair as part of the Azure deployment flow and used SSH key authentication instead of password login.
6. Deployed the VM into `rg-azure-lab-network`.
7. Confirmed Azure created the VM, network interface, and public IP resources.
8. Connected to the VM over SSH.
9. Installed Nginx on the Ubuntu VM.
10. Confirmed the service was running on the VM.
11. Reviewed the existing NSG attached to `public-subnet`.
12. Initially added an inbound rule for the wrong port (`8080`) while Nginx was listening on the standard HTTP port.
13. Corrected the NSG by allowing inbound TCP `80`.
14. Confirmed the VM network settings and NSG relationship.
15. Validated the public web response by reaching the default Nginx page from a browser.

## Validation

- SSH access to the Linux VM succeeded.
- `sudo apt install nginx -y` completed successfully on the VM.
- The VM remained attached to `public-subnet` in `vnet-lab-network`.
- The subnet-level NSG was first tested with the wrong web port and then corrected to allow inbound HTTP on TCP `80`.
- A browser request to the VM public IP returned the default `Welcome to nginx!` page.

## What I Learned

- Azure VM deployment becomes easier once the network foundation already exists and can be reused cleanly.
- Subnet-level NSG design makes it straightforward to add workload-specific access later without rebuilding the network.
- A simple HTTP validation is a fast way to prove that the compute, networking, and security layers are working together.
- Service status alone is not enough; the exposed port and the NSG rule have to match the application actually listening on the VM.
- Reusing a prior lab's VNet and NSG turns separate Azure exercises into a more realistic sequence instead of isolated portal clicks.

## Problems Encountered / Notes

- The private evidence set includes account-banner details and public-IP exposure, so the raw screenshots were not copied directly into this public repo.
- The NSG already contained SSH-focused rules from the earlier network lab, and this lab added web access for application validation.
- The first HTTP rule used the wrong destination port (`8080`). The final working path used TCP `80`, which matched the Nginx default listener and resolved the connectivity issue.
- Earlier VM wizard attempts drifted away from the intended network design by trying to create a new VNet or place the VM in the wrong subnet. The final lab state documented here uses the existing `vnet-lab-network` and `public-subnet`.

## Cost Control and Cleanup

- This lab used a single Linux VM and reused the earlier network foundation.
- No load balancer, Application Gateway, or multi-VM design was introduced.
- Cleanup state is not claimed here because the private evidence set does not prove final deletion of every resource.
- The original chat workflow explicitly called out stopping or deallocating the VM when not in use to avoid unnecessary compute charges.

## Repo Structure

- `README.md`
  - main lab walkthrough and outcome
- `LAB_SUMMARY.md`
  - short version for quick portfolio review
- `EVIDENCE_NOTES.md`
  - explains why the screenshot set is currently kept private

## Evidence Approach

The public repo keeps the workflow reviewable through the written build sequence, validation notes, and troubleshooting summary. The screenshot set remains private because it contains account banner details and public-IP exposure that are not useful to publish. This keeps the repo public-safe without pretending the screenshots do not exist.

## Outcome

The lab produced a working Azure Linux VM deployment with SSH administration, an Nginx installation, a corrected NSG web rule, and successful inbound HTTP validation through the existing network and subnet-level security design.

## Repository Notes

- This repo extends the Azure networking lab rather than replacing it.
- The detailed reason the screenshot set remains private is documented in [EVIDENCE_NOTES.md](EVIDENCE_NOTES.md).
