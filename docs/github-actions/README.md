# GitHub Actions & CI Strategy

This document outlines the approach, goals, and local testing procedures for the project's CI/CD pipeline.

## Approach

Our CI pipeline is designed for **reliability, performance, and consistency**. We use standard Elixir and Phoenix patterns, leveraging the official community-maintained actions to ensure long-term support.

### Key Pillars:
- **Lock-file Integrity**: We always use `mix.lock` to ensure that dependencies are consistent across all environments, preventing "dependency drift."
- **Aggressive Caching**: We cache both the `deps/` directory and the `_build/` directory. This significantly reduces build times by avoiding redundant network fetches and recompilation of unchanged code.
- **Strict Validation**: Our CI doesn't just run tests; it also enforces code formatting (`mix format`) and treats compiler warnings as errors to maintain high code quality.
- **Isolated Services**: We use GitHub Actions' native service containers for PostgreSQL to ensure a clean, reproducible database environment for every test run.

## Goals

1.  **Fast Feedback**: Provide developers with quick results on their changes.
2.  **Drift Prevention**: Ensure the `test` environment exactly matches the `dev` and `prod` dependency trees.
3.  **Network Resilience**: Minimize reliance on external package mirrors during CI runs through robust caching.
4.  **Local Parity**: Make it easy for developers to run the exact same CI checks on their local machines.

## Local Testing with `act`

To avoid "commit-to-test" cycles, we support running GitHub Actions locally using [nektos/act](https://github.com/nektos/act).

### Prerequisites
- [nektos/act](https://github.com/nektos/act) installed

### Running CI Locally

`act` should be enough for now.

### Tips for Local Testing
- **First Run**: The first time you run this, it will pull several large Docker images. Subsequent runs will be much faster.
- **Specific Jobs**: If you only want to run the test job, you can append `-j test` to the command.
- **Path Mapping**: If `act` reports issues finding the `/app` directory, ensure your Docker engine has permission to mount the project root.
- **Secrets**: If your workflow eventually requires secrets (e.g., API keys), you can create a `.secrets` file locally and pass it to `act` using the `--secret-file` flag.

## Troubleshooting

### Docker Registry Authentication Errors
If you receive a `403 Forbidden` or `Unauthorized` error when pulling images from `ghcr.io`:
1.  **Switch Registry**: We have switched our default `act` image to `nektos/act` on Docker Hub to minimize this risk.
2.  **Authenticate**: If you need to pull specific images from GitHub's registry, create a Personal Access Token (classic) with `read:packages` scope and run:
    ```bash
    echo $YOUR_TOKEN | docker login ghcr.io -u YOUR_GITHUB_USERNAME --password-stdin
    ```
