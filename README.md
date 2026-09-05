# End-to-End CI/CD Pipeline

[![CI/CD Pipeline](https://github.com/ummadisettisindhuja2-netizen/end-to-end-ci-cd-pipeline/actions/workflows/ci-cd.yml/badge.svg)](https://github.com/ummadisettisindhuja2-netizen/end-to-end-ci-cd-pipeline/actions/workflows/ci-cd.yml)

A practical DevOps project that demonstrates an automated CI/CD pipeline for a Python web application. The pipeline tests the application, performs security checks, builds a Docker image, and publishes the image to GitHub Container Registry.

## Architecture

```mermaid
```

## Pipeline Stages

1. A developer pushes code to the `main` branch.
2. GitHub Actions runs automated Pytest checks.
3. Bandit scans the Python code for security issues.
4. pip-audit checks dependencies for known vulnerabilities.
5. If every check passes, the pipeline builds and publishes a Docker image to GitHub Container Registry.

## Application Endpoints

| Endpoint | Purpose |
|---|---|
| `/` | Returns the application status message |
| `/health` | Returns a health-check response |

## Run Locally

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the application:

```bash
python app.py
```

Run automated tests:

```bash
PYTHONPATH=. pytest -q
```

## Run with Docker

Build the image:

```bash
docker build -t end-to-end-ci-cd-pipeline .
```

Run the container:

```bash
docker run -p 5000:5000 end-to-end-ci-cd-pipeline
```

Open the application at:

```text
http://localhost:5000
```

## Security Controls

- Bandit static security scanning for Python source code
- pip-audit dependency vulnerability scanning
- Non-root user inside the Docker container
- `.dockerignore` to exclude unnecessary files from the image
- Pipeline blocks image publishing when tests or security checks fail

## Security Remediation Example

The dependency audit identified a known vulnerability in Pytest `8.4.2`. The dependency was upgraded to Pytest `9.0.3` or later, and the pipeline passed after the remediation.

## Technologies Used

Python | Flask | Pytest | Bandit | pip-audit | Docker | GitHub Actions | GitHub Container Registry | YAML

## Project Structure

```text
.github/workflows/ci-cd.yml  - CI/CD pipeline
tests/test_app.py            - Automated tests
app.py                       - Flask application
Dockerfile                   - Container configuration
.dockerignore                - Docker build exclusions
requirements.txt             - Python dependencies
```

## Author

Sindhuja Ummadisetti  
Cloud & DevOps Engineer

- [GitHub Profile](https://github.com/ummadisettisindhuja2-netizen)
- [LinkedIn Profile](https://www.linkedin.com/in/ummadisetti-sindhuja-1201/)
flowchart LR
    A[Developer Push] --> B[GitHub Repository]
    B --> C[GitHub Actions]
    C --> D[Automated Tests]
    C --> E[Security Scans]
    D --> F[Docker Build]
    E --> F
    F --> G[GitHub Container Registry]
