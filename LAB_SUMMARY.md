# Lab Summary

## Lab

Azure Lab 4: Ubuntu VM and Nginx Validation

## Goal

Deploy an Ubuntu VM into an existing Azure network, administer it over SSH, install Nginx, allow HTTP through the subnet NSG, and verify public web access.

## Skills Demonstrated

- Azure VM deployment
- SSH key generation and Linux administration
- Reuse of existing VNet and subnet design
- NSG rule management for application access
- Basic web-service validation with Nginx

## Final State

- `vm-lab-01` deployed in `rg-azure-lab-network`
- VM attached to `vnet-lab-network` / `public-subnet`
- Nginx installed successfully
- NSG updated to allow inbound HTTP
- Browser reached the default Nginx landing page

## Portfolio Value

This lab shows a practical end-to-end path from Azure infrastructure deployment to live service validation, rather than stopping at resource creation alone.
