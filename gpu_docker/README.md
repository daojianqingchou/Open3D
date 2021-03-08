# Open3D GPU docker CI

```bash
# First, cd to the top Open3D directory

# 1. Build image
docker build -t open3d-gpu-ci:latest -f gpu_docker/Dockerfile .

# 2. Run in detached mode
docker run -d -it --rm --gpus all -v ~/.docker_ccache:/root/.cache/ccache --name ci open3d-gpu-ci:latest

# 3. Attach to container
docker exec -it ci /bin/bash

# 2&3. Run and attach together
docker run -d -it --rm --gpus all -v ~/.docker_ccache:/root/.cache/ccache --name ci open3d-gpu-ci:latest && docker exec -it ci /bin/bash

# 4. Build and test
# Now you should be in /root/Open3D inside docker
./gpu_docker/build_and_test.sh

# 5. Stop container
docker stop ci

# Extra: run command immediately
docker run --rm --gpus all open3d-gpu-ci:latest nvidia-smi
docker run --rm --gpus all open3d-gpu-ci:latest ccache -s
```
