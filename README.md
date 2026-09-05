# End-to-End CI/CD Pipeline

[![CI/CD Pipeline](https://github.com/ummadisettisindhuja2-netizen/end-to-end-ci-cd-pipeline/actions/workflows/ci-cd.yml/badge.svg)](https://github.com/ummadisettisindhuja2-netizen/end-to-end-ci-cd-pipeline/actions/workflows/ci-cd.yml)

A practical DevOps project that demonstrates an automated CI/CD pipeline for a Python web application. The pipeline tests the application, performs security checks, builds a Docker image, and publishes the image to GitHub Container Registry.

## Architecture

```mermaid
flowchart LR
    A[Developer Push] --> B[GitHub Repository]
    B --> C[GitHub Actions]
    C --> D[Automated Tests]
    C --> E[Security Scans]
    D --> F[Docker Build]
    E --> F
    F --> G[GitHub Container Registry]
