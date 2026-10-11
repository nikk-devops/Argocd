# Argocd

We are going to implement a basic workflow to test how argocd can be configure to implement CD for our kubernetes GKE cluster wherein it actually following the below workflow.

                  DEVELOPER
                      |
                      | git push
                      v
              +------------------+
              |  GitHub Repo     |
              |  Application     |
              |  Source Code     |
              +------------------+
                      |
                      v
              +------------------+
              | GitHub Actions   |
              |                  |
              | 1. Build Image   |
              | 2. Push to GHCR  |
              +------------------+
                      |
                      v
              +------------------+
              | GitHub Container |
              | Registry (GHCR)  |
              |                  |
              | app:v1.0.0       |
              +------------------+

                      GitOps
                         |
                         v
              +------------------+
              | GitHub Repo      |
              |                  |
              | Helm Chart       |
              | values.yaml      |
              +------------------+
                         ^
                         |
                  Watches Git
                         |
              +------------------+
              |     Argo CD      |
              | Running in GKE   |
              +------------------+
                         |
                         | Deploys Helm chart
                         v
              +------------------+
              |    GKE Cluster   |
              |                  |
              | Kubernetes Pods  |
              | Services         |
              +------------------+
                         |
                         v
              Container image pulled
                    from GHCR
