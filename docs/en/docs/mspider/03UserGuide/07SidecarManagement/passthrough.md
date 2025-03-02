# passthrough of sidecar traffic

Traffic passthrough refers to the fact that all or part of the upstream and downstream traffic of the workload is directly sent to the workload itself without being forwarded by the sidecar.

The DCE 5.0 service mesh realizes the controllable sidecar passthrough of workload outbound/inbound traffic, and can implement interception settings for specific ports and IP segments.

- Feature setting object: Workload
- Setting parameters: port, IP segment
- Flow direction: inbound, outbound

Fields related to traffic passthrough:

```none
traffic.sidecar.istio.io/excludeInboundPorts
traffic.sidecar.istio.io/excludeOutboundPorts
traffic.sidecar.istio.io/excludeOutboundIPRanges
```

## Enable traffic passthrough

This section explains how to enable/disable traffic passthrough on the DCE GUI.

1. Enter a mesh, click `Sidecar Management` -> `Workload Sidecar Management`.

    ![workload sidecar management](../../images/pn01.png)

1. Click `⋮` on the right side of a workload, and select `Traffic passthrough Settings` in the pop-up menu.

    ![click menu item](../../images/pn02.png)

1. After setting the parameters for traffic passthrough, check `Restart now`, and click `Confirm changes`.

     ![Traffic passthrough settings](../../images/pn03.png)

     - Inbound: Only ports are supported, i.e. ports for external access to workloads within the mesh
     - Outbound: You can set the port or IP range of the target

1. If the settings are correct, there will be a prompt message `Traffic passthrough setup successful` in the upper right corner. You can also [check the traffic passthrough effect](#check-traffic-passthrough-effect).

     ![Set successfully](../../images/pn04.png)

1. If traffic passthrough is enabled, the pop-up window of `Traffic passthrough settings` in step 3 above will display the set parameters, click the x on the right, check `Restart workload now`, and click `Confirm changes` to Disable traffic passthrough.

     ![Disable traffic passthrough](../../images/pn05.png)

## Check traffic passthrough effect

In a real mesh cluster, check the effect before and after traffic passthrough.

1. Preparations

     - Prepare a mesh cluster, for example 10.64.30.130
     - In the namespace, configure the workload `helloworld` and inject sidecars
     - Enable traffic passthrough, and then compare the traffic routing changes of the workload

     ![Workload](../../images/pn06.png)

1. Log in to the mesh via console or ssh.

     ```bash
     ssh root@10.64.30.130
     ```

1. Check the svc in the namespace to get the clusterIP and Port:

     ```bash
     $ kubectl get svc -n default
     NAME TYPE CLUSTER-IP EXTERNAL-IP PORT(S) AGE
     helloworld ClusterIP 10.211.201.221 <none> 5000/TCP 39d
     kubernetes ClusterIP 10.211.0.1 <none> 443/TCP 62d
     test-cv NodePort 10.211.72.8 <none> 2222:30186/TCP 62d
     ```

1. Execute the curl command to view the traffic routing of helloworld:

     === "Before enabling traffic passthrough"

         ```bash
         $ curl -sSI 10.211.201.221:5000/hello
         HTTP/1.1 200 OK
         content-type: text/html; charset=utf-8
         content-length: 65
         server: istio-envoy # (1)
         date: Tue, 07 Feb 2023 03:08:33 GMT
         x-envoy-upstream-service-time: 100
         x-envoy-decorator-operation: helloworld.default.svc.cluster.local:5000/*
         ```

         1. The traffic passes through istio-envoy, the proxy of the sidecar

     === "After enabling traffic passthrough"

         ```bash
         $ curl -sSI 10.211.201.221:5000/hello
         HTTP/1.0 200 OK
         Content-Type: text/html; charset=utf-8
         Content-Length: 65
         Server: Werkzeug/0.12.2 Python/2.7.13 # (1)
         Date: Tue, 07 Feb 2023 03:08:10 GMT
         ```

         1. Traffic goes directly to the workload itself
