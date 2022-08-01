# 300 - Working with the Docker registry

Based on "Working with the Docker registry" at https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-docker-registry

**NOTE**: The Docker registry has now been replaced by the Container registry.

GitHub's Docker registry (which used the namespace ```docker.pkg.github.com```) has been replaced by the Container registry (which uses the namespace ```https://ghcr.io```). The Container registry offers benefits such as granular permissions and storage optimization for Docker images.

Docker images previously stored in the Docker registry are being automatically migrated into the Container registry. For more information, see "[Migrating to the Container registry from the Docker registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/migrating-to-the-container-registry-from-the-docker-registry)" and "[Working with the Container registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry)."
