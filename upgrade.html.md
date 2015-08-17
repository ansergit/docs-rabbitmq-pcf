---
title: RabbitMQ for Pivotal Cloud Foundry
---

# Upgrades

This product enables a seamless upgrade experience between versions of the product that is deployed through Ops Manager.

The upgrade paths are detailed [here](http://docs.pivotal.io/rabbitmq-cf/index.html) for each released version.

To upgrade the product:

* The Operator should download the latest version of the product from [Pivotal Network](https://network.pivotal.io/products/pivotal-rabbitmq-service)
* Upload the new .pivotal file to Ops Manager
* Upload the stemcell associated with the update (*if required*)
* Update any new mandatory configuration parameters (*if required*)
* Press "Apply changes" and the rest of the process is automated

During a typical upgrade deployment, nodes are upgraded one at a time in the cluster providing a zero downtime deployment. Applications may experience a disconnected session, if the application attempts to reconnect it will be directed to another working node automatically. 

Only when upgrading between specific versions of Erlang or RabbitMQ is an outage required on the cluster. This will be clearly stated on the release notes for that version, should this be required. 

The length of the downtime depends on whether there is a stemcell update to replace the operating system image or whether the existing VM can simply have the RabbitMQ software updated. Stemcell updates incur additional downtime while the IaaS creates the new VM while updates without a stemcell update are faster. 

Ops Manager ensures the instances are updated with the new packages and any configuration changes are applied automatically.

Upgrading to a newer version of the product does not cause any loss of data or configuration. This is explicitly tested for during our build and test process for a new release of the product.

# Release policy

When a new version of RabbitMQ is released we aim to release a new version of the product containing this soon after.

Where there is a new version of RabbitMQ or another dependent software component such as the stemcell released due to a critical CVE, Pivotal's goal is to release a new version of the product within 48 hours.