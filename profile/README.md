# sogeor

An open-source reference DevSecOps platform: build any Kubernetes cluster from a short
description, on a home Proxmox server or in the cloud, with security by default at every layer.
Aligned with international (CIS, NIST SSDF, SLSA, OWASP) and Russian (GOST R 56939-2024,
FSTEC orders, FSTEC BDU) frameworks.

## Architecture

```mermaid
flowchart LR
  L0["Layer 0<br/>bootstrap"] --> GHA["GitHub Actions<br/>state on gitlab.com"]
  GHA --> EDGE["edge<br/>Headscale mesh"]
  GHA --> MGMT["mgmt cluster<br/>Talos"]
  MGMT -- "Argo CD + Cluster API" --> MAIN["main<br/>kubeadm, Ubuntu / Astra"]
  MGMT -- "Argo CD + Cluster API" --> TALOS["talos<br/>Talos Linux"]
  MAIN <-- "Cilium ClusterMesh" --> TALOS
```

- **Management cluster `mgmt`** (Talos): Argo CD, Cluster API with autoscaling, OpenBao,
  Keycloak, Harbor, GitLab, backups.
- **Workload clusters** are created from `mgmt` in the cloud, scale down to zero worker nodes and
  can be torn down and restored from backups in one operation.

## Cluster constructor

A cluster is a combination of independent axes; a new combination is a new description file,
not new code.

| Axis | Values |
|---|---|
| Distribution | Talos, kubeadm, k3s |
| Operating system (per node pool) | Ubuntu 24.04, Ubuntu 26.04, Astra Linux SE 1.8, Talos, Alpine (experimental) |
| Provider | Proxmox, Selectel, VK Cloud, Yandex Cloud, Timeweb, bring-your-own VDS |
| Topology | `single` (minimum cost) or `ha`, switched by configuration |
| Profiles | core, CI, data, security-plus, observability-plus, chaos, ru-track |

## Principles

- **Supply chain:** SLSA provenance, SBOM and VEX attestations, Cosign signatures verified at admission.
- **No static secrets in CI:** OIDC → OpenBao short-lived credentials.
- **Policy as code** on every layer: infrastructure plans, cluster descriptions, OS, admission, runtime, network.
- **Zero trust access:** short-lived SSH certificates, OIDC for the Kubernetes API, no public admin endpoints.
- **Self-healing:** nodes are recreated from descriptions, data is restored from backups automatically.
- **Documentation is part of the product:** every repository explains every option and every action.

## Repositories

| Repository | Purpose | Status |
|---|---|---|
| [`images`](https://github.com/sogeor/images) | VM images: Ubuntu for Proxmox, Talos Image Factory schematic | Ready [![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/sogeor/images/badge)](https://scorecard.dev/viewer/?uri=github.com/sogeor/images) |
| [`.github`](https://github.com/sogeor/.github) | Organization profile and community defaults | In progress |
| [`workflows`](https://github.com/sogeor/workflows) | Reusable GitHub Actions workflows | In progress |
| `docs` | Platform-wide documentation, ADRs, runbooks | Planned |
| `bootstrap` | Layer 0: Hyper-V, Proxmox, cloud accounts, secrets | Planned |
| `modules` | OpenTofu modules and the cluster constructor | Planned |
| `management` | Outer contour: edge, mgmt cluster, DNS, Cloudflare | Planned |
| `platform` | GitOps for all clusters | Planned |
| `ansible` | Roles for non-Talos nodes | Planned |
| `ci-templates` | GitLab CI templates for the inner contour | Planned |
| `charts` | Shared Helm `service` chart | Planned |
| `store` | Online store running on the platform | Planned |
| `policies` | Policy and detection as code | Planned |
| `compliance` | Compliance matrix, evidence, tooling | Planned |

Each repository documents itself in its `docs/` directory; platform-wide documentation will live in
the `docs` repository.
