---
date: 2023-01-12
---

# DCE 5.0 Community Edition v0.4.0

This page can download the offline installation package and verification file of DCE 5.0 Community Edition.

## Download

| File Name | Version | Architecture | File Size | Downloads | Date Updated |
| ----------------------------- | ------- | -------- | -- ----------------------------------------------- | ----- ----- | -------------------------------- |
| offline-community-v0.4.0-amd64.tar | v0.4.0 | AMD64 | 5.73GB | [:arrow_down: Download](https://qiniu-download-public.daocloud.io/DaoCloud_Enterprise/dce5/offline- community-v0.4.0-amd64.tar) | 2023-01-12 |
| offline-community-v0.4.0-arm64.tar | v0.4.0 | ARM64 | 5.16GB | [:arrow_down: Download](https://qiniu-download-public.daocloud.io/DaoCloud_Enterprise/dce5/offline- community-v0.4.0-arm64.tar) | 2023-01-12 |

## Verify

Enter the download directory of the offline installation package.

=== "AMD64"

     Execute the following command to verify the installation package:

     ```sh
     echo "41f7705d2be5487a721b936ba16b89ad2f35011b0d1a98d71d29ab51cf36ef2bf34283be384e76b0438c172ff9e236c44c33843e9855e9af253b1db4b84144fe  offline-community-v0.4.0-amd64.tar" | sha512sum -c
     ```

     If the verification is successful, it will print:

     ```none
     offline-community-v0.4.0-amd64.tar: OK
     ```

=== "ARM64"

     Execute the following command to verify the installation package:

     ```sh
     echo "1d0476965fd73002c379639353b0bd0e09cefe99156ef448c42a4c10aff60a9836981c86e914ba3f614617a455b67a8c3ce4d82d53b3e47a22222c34020d0a00  offline-community-v0.4.0-arm64.tar" | sha512sum -c
     ```

     If the verification is successful, it will print:

     ```none
     offline-community-v0.4.0-arm64.tar: OK
     ```

## Install

After successfully verifying the offline package,

=== "AMD64"

     Execute the following command to extract the tar package:

     ```sh
     tar -zxvf offline-community-v0.4.0-amd64.tar
     ```

=== "ARM64"

     Execute the following command to extract the tar package:

     ```sh
     tar -zxvf offline-community-v0.4.0-arm64.tar
     ```

- For installation, please refer to [Community Edition Installation Process](../../install/community/k8s/online.md#_2)
- After successful installation, please [try free](../../dce/license0.md)

## Modules

DCE 5.0 Community Edition includes the following modules by default:

| Modules | Introduction | What's New |
| -------- | ----------------------------------------- ------------------------- | ------------------------ ------------------------------------- |
| Global Management | Responsible for user access control, permissions, enterprise space, audit logs, personalized appearance settings, etc. | [v0.13.2](../../ghippo/01ProductBrief/release-notes.md#v0132) |
| Container Management | Manage K8s core functions such as clusters, nodes, workloads, Helm applications, CRDs, and namespaces | [v0.14.0](../../kpanda/03ProductBrief/release-notes.md#v0140) |
| Observability | Provide rich graphic information such as dashboards, scene monitoring, data query, and alarms | [v0.13.2](../../insight/03ProductBrief/releasenote.md#v0132) |

## More

- [Online Documentation](https://docs.daocloud.io/dce/what-is-dce/)
- [Report a bug](https://github.com/DaoCloud/DaoCloud-docs/issues)
