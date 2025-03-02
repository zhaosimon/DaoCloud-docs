---
date: 2022-11-23
hide:
  - navigation
---

# DCE 5.0 Community Edition v0.3.27

This page can download the offline installation package and verification file of DCE 5.0 Community Edition.

## Download

| version name | installation package |
| ----------------------------- | ------------------- -------------------------------------------------- -------------------------------------------- |
| offline-community-v0.3.27.tar | [:arrow_down: Download](https://proxy-qiniu-download-public.daocloud.io/DaoCloud_Enterprise/dce5/offline-community-v0.3.27.tar) |

## Validation

Enter the download directory of the offline installation package. Execute the following command to verify the installation package:

```sh
echo "7a2f07fd9d09c827347d2994c0b6d4852f55e1f6de149e7b95e29625c4081eba3d415d3dbb261d226d8179c3251ac8e67c2de898d3eb6a58ff218f79fd31d42e  offline-community-v0.3.27.tar" | sha512sum -c
```

If the verification is successful, it will print:

```none
offline-community-v0.3.27.tar: OK
```

## Install

After successfully verifying the offline package, unpack the tar package:

```sh
tar -zxvf offline-community-v0.3.28.tar
```

Then refer to [Community Edition Installation Process](../../install/community/k8s/online.md#_2) to install.

After successful installation, please [apply for free community experience](../../dce/license0.md).

## Modules

DCE 5.0 Community Edition includes the following modules by default:

| Modules | Introduction | What's New |
| -------- | ----------------------------------------- ------------------------- | ------------------------ ----------------------------------------- |
| Global Management | Responsible for user access control, permissions, enterprise space, audit logs, personalized appearance settings, etc. | [Release Notes](../../release/rn5.0.md#_4) |
| Container Management | Manage K8s core functions such as clusters, nodes, workloads, Helm applications, CRDs, and namespaces | [v0.12.0](../../kpanda/03ProductBrief/release-notes.md#v0120) |
| Observability | Provide rich graphic information such as dashboards, scene monitoring, data query, and alarms | [v0.11.1](../../insight/03ProductBrief/releasenote.md#v0111) |

## More

- [Online Documentation](https://docs.daocloud.io/dce/what-is-dce/)
- [Report a bug](https://github.com/DaoCloud/DaoCloud-docs/issues)