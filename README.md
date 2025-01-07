# GCP Registry Login Action

A GitHub Action that logs you into GCP, with docker authorization setup

## Usage

```yaml
name: Build and Push Docker Image
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4

    - name: Login to GCP
      uses: Fulfil0518/gcp-registry-login-action@v1
      with:
        service_key: ${{ secrets.SERVICE_KEY }}
        endpoint: gcr.io/your-project-id/foo/bar:tag

    - name: Set up Docker Buildx
      uses: docker/setup-buildx-action@v3
    - name: Build and push
      uses: docker/build-push-action@v6
      with:
        push: true
        tags: gcr.io/your-project-id/foo/bar:tag
```
