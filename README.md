<p align="center">
  <img src="assets/camille.png" alt="Camille, the mascot of Liko" width="240">
</p>

<h1 align="center">argo-rollouts.liko</h1>

**This repository contains the Argo Rollouts module for the Liko data language. This module is officially maintained by the Liko team.**

It contains the complete set of Argo Rollouts schema definitions (`Rollout`, `AnalysisTemplate`, `ClusterAnalysisTemplate`, `AnalysisRun`, `Experiment`) generated from the CRDs of the official [Argo Rollouts repository](https://github.com/argoproj/argo-rollouts/releases).

---

## Installation

Initialize a local module with `liko init`, then add `argo-rollouts.liko` as a dependency.

```bash
liko init
```

```bash
liko add argo-rollouts
```

```bash
liko install
```

## Usage

The module can now be used from any directory within the current module.

```liko
#Ar: import "argo-rollouts/v1alpha1"

$: #Ar.Rollout & {
    metadata: {
        name: "my-app"
    }
    spec: {
        replicas: 3
        selector: {
            matchLabels: {
                app: "my-app"
            }
        }
        strategy: {
            canary: {
                steps: [
                    { setWeight: 20 }
                    { pause: { duration: "5m" } }
                    { setWeight: 50 }
                ]
            }
        }
    }
}
```

## Versions

Each release of this repository matches a release of Argo Rollouts: `liko add argo-rollouts@v1.10.0`. Without a version, the latest release is installed.
