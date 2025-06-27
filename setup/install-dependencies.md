# Install dependencies on Ubuntu (MPI + RDMA Benchmarking)

This guide installs the essential packages for MPI benchmarking, including RDMA support.

## Tested on
- Ubuntu 22.04 LTS
- Two servers connected via Mellanox SN2700 switch.

---
## 1. Update System


```bash
sudo apt update && sudo apt upgrade -y 
```

## 2. Install MPI (OpenMPI)

``` bash
sudo apt install openmpi-bin openmpi-common libopenmpi-dev -y
```
### Verify
```bash
mpirun --version
```

## 3. Install RDMA and OFED Tools
```bash
sudo apt install rdma-core ibverbs-utils infiniband-diags perftest -y
```

### Verify
```bash
ibv_devinfo
```
If your NIC supports RDMA, this will show devices like:
```vbnet
hca_id: mlx5_0
    transport:          InfiniBand (or Ethernet with RoCE)
```

## 4. Download OSU Micro-Benchmarks (MPI Tests)