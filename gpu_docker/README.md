# Open3D GPU docker CI

```bash
# Build image
docker build -t open3d-gpu-ci:latest .

# Run command and immediately exit
docker run --rm --gpus all open3d-gpu-ci:latest nvidia-smi

# Run in detached mode
docker run -d -it --rm --gpus all --name ci open3d-gpu-ci:latest

# Attach to container
docker exec -it ci /bin/bash

# Stop container
docker stop ci
```
