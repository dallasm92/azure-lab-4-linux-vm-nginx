# Lab Summary

## Lab

Azure Lab 4: Azure Linux VM, SSH, and Nginx Validation

## Goal

Deploy a Linux VM into the existing Azure lab network, connect over SSH with key-based authentication, install Nginx, correct the NSG web rule, and validate public HTTP access.

## Skills Demonstrated

- Azure VM deployment into an existing VNet and subnet design
- SSH key generation and Linux remote administration
- Reuse of earlier network security foundations
- NSG rule management for application exposure
- Port-based troubleshooting between service configuration and firewall rules

## Final State

- `vm-lab-01` deployed in `rg-azure-lab-network`
- VM attached to `vnet-lab-network` / `public-subnet`
- SSH key authentication used successfully
- Nginx installed and running
- NSG corrected from an initial wrong web port to inbound HTTP on TCP `80`
- Browser reached the default Nginx landing page

## Portfolio Value

This lab shows a practical end-to-end path from Azure infrastructure deployment to live service validation. It ties compute, networking, security, and Linux administration together in a way that is stronger than a VM-creation-only project.
