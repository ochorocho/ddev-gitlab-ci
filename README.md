# DDEV GitLab CI - Docker in Docker (dind)

This image is most likely to be used within the GitLab Runner.
As of now it only tested it on gitlab.com

**GitLab CI example**: [.gitlab-ci.yml](.gitlab-ci.yml)

# Workflow - Image build

Build the image

```bash
./build.sh -v <version, at least major.minor> -p
``` 

Available options:
 * v - DDEV version e.g. 'v1.23.1' 
 * l - Load the image (--load)
 * p - Push the image (--push)
 * x - Build multi-arch image (--platform linux/amd64,linux/arm64)

## Version to tags

| Command               | Tags to be created             |
|-----------------------|--------------------------------|
| ./build.sh -v v1.22   | v1.22, v1.22.x (latest bugfix) |
| ./build.sh -v v1.22.5 | v1.22.5                        |
| ./build.sh -v v1.23   | v1.23, v1.23.x (latest bugfix) |
| ...                   | ...                            |

## Run tests locally

Requires [bats-core](https://bats-core.readthedocs.io/en/stable/installation.html) and [yq](https://github.com/mikefarah/yq/tree/v4.44.2?tab=readme-ov-file#install).

```
DDEV_VERSION=v1.23.3 bash bats tests
```

