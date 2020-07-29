# Google Cloud Networking

Google Cloud Platform is build on top of a Software Defined Network.
It is built on a global fiber infrastructure. It is one of the world's largest and fastest networks.

## Comparison of Interconnect Options

[![Comparison of Interconnect Options](https://cloud.google.com/solutions/images/patterns-for-connecting-other-csps-with-gcp-6-comparison.svg)](https://cloud.google.com/solutions/patterns-for-connecting-other-csps-with-gcp)

## Networking Tier Options

[![Networking Tier Options](https://cloud.google.com/images/network-tiers/decision-tree.svg)](https://cloud.google.com/network-tiers/)

## Virtual Private Cloud Network

A project can contain up to 5 VPC networks.

VPC Network Details:

* Subnets:
  * Are the logical isolation partitions for the VPC network.
  * They contain a defined IP range. Instances and other resource draw from this range.
  * **Are regional and span zones in the region.**
* Projects are provided with a default network:
  * Has preset configurations and firewall rules.
  * Can be customized.
* Can have up to 5 networks per Project.
* Instances connect up to networks using interfaces.
* Multiple Interfaces can connect instances to multiple networks.
* Traffic between networks go out through the Google edge routers (Use VPC Peering to avoid).
* Network design is not hierarchical based like in physical networks. Use subnets to group resources such as departments.
* Deleting a custom network requires you to delete subnets first.

## Topology Summary

* Projects can have up to 5 networks.
* Networks span the globe.
* Internal DNS works for the entire network.
* Firewall rules apply to the entire network.
* Subnets are regional and span zones.
* Subnets enable easier service isolation with firewall rules.
* Default routes are created when you create subnets.
* Communication between networks requires external IP addresses.
* Billed for traffic between networks.
* Small bill for traffic between regions.

## Interconnection Options

Connecting your office directly to the Google network you will have private access to all of the services that Google offers including GCP, GMail, Maps, YouTube, etc.

There are three options to interconnect:

1. VPN and Cloud Router.
2. Cloud Interconnect.
3. Direct Peering.
   1. Connecting two VPC networks within and across organizations using private google network
      1. Advantages
         1. Lower Network Latency
         2. Network Security
         3. Network Costs
4. Shared VPC
   1. Host and Shared projects



## Multiple Network Interfaces

Google Cloud Virtual Private Networks (VPC) are by default isolated private networking domains, however there are cases where a machine might need to connect to multiple VPC networks. In such cases VM's can create additional network interfaces (with internal/external ip address) connecting to different VPC networks without direct communication between them (though same host)

- Use cases
  
  - Load Balancers
  
  - Intrusion Detection and Prevention (IDP/IPS)
  
  - Web Application Firewall (WAF)
  
  - WAN
