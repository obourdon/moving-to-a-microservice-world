---
id: initial_situation
title: "Initial situation"
sidebar_label: "Initial situation"
---
Now that you have our "cloud" environment up and running, you can start to add our applications.
In the initial situation there are 2 "VMs", one containing an ingress proxy called "web" and the other one containing the "payments" monolith.
The applications are configured statically, with web pointing directly to the ip address of payments.

![Initial Setup](assets/initial_setup.png?raw=true)

In order to be able to run this demo entirely on our local machine, the VMs are simulated with fat containers.
These Alpine containers have 3 processes running, managed by Supervisor:
- the application binary.
- a Consul agent, configured as a client.
- an Envoy sidecar proxy for the application.

![Containers as VMs](assets/fake_vm.png?raw=true)

## Create the initial setup

To spin up the two VMs you can create the resources located in the `v1` directory.

```
shipyard run v1
```

## Web service

The `web` service is listening on port 9090 and will be routing our requests to the internal services.
Once the applications have started, the `web` service should automatically open in your browser on the `/ui` path. 

![Fake Service UI](assets/fake_service_ui.png?raw=true)

To see the raw output of the service, browse to the root `/` path of the service.