# Open3D GPU docker CI

```bash
# Build image
docker build -t open3d-gpu-ci:latest .

# Run in detached mode
docker run -d -it --rm --gpus all -v ~/.docker_ccache:/root/.cache/ccache --name ci open3d-gpu-ci:latest

# Attach to container
docker exec -it ci /bin/bash

# Stop container
docker stop ci

# Extra: run command immediately
docker run --rm --gpus all open3d-gpu-ci:latest nvidia-smi
docker run --rm --gpus all open3d-gpu-ci:latest ccache -s
```
