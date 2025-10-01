
# Cryptix Fusion
Website: https://cryptix-network.org/cryptix-fusion
Discord: https://discord.cryptix-network.org/


Supports:
AMD GPU | NVIDIA GPU | Intel GPU | Onboard GPUs | All CPUs | 

Windows | Linux | HiveOS | MMPOS

### v1 Note

Please note that Cryptix Fusion v1 is only a CPU release.

It's possible that you can already use the GPU. However, the GPU server, CCPI adjustment, and possible jobs are still being developed. However, anyone who would like to test the GPU can do so. However, the profitability for GPUs will be rather low until GPU release v2.

<img width="1149" height="1297" alt="9999999999999999999" src="https://github.com/user-attachments/assets/c8fea6db-180d-48fa-b16f-e6a304558e4b" />
---
To get your Cryptix ID, you first need to create an account in the Member Area: https://cryptix-network.org/member-area
You will also need a Cryptix CPAY wallet address: https://wallet.cryptix-network.org/

Once your account and wallet are ready, download the software and add your Cryptix ID into the pre-made BAT files, or start from the console. You need to specify which device to use for the jobs.

CPU only:
./cryptix-fusion -u <cryptixID> --use-cpu

Limit the threads with:
--threads=4

Totally:
./cryptix-fusion -u <cryptixID> --use-cpu --threads=4

GPU only:
For NVIDIA GPUs (CUDA):
./cryptix-fusion -u <cryptixID> --use-gpu --use-nvidia

For AMD GPUs (OPENCL):
./cryptix-fusion -u <cryptixID> --use-gpu --use-amd

For other GPUs or if you have issues (OPENCL experimental):
./cryptix-fusion -u <cryptixID> --use-gpu --use-mixed

You can append a worker name to your ID using a dot, e.g.:
-u <cryptixID>.workercpu

You can also start the software twice on the same device: once with CPU only and once with GPU only. This allows both CPU and GPU Jobs to run simultaneously.

---

It is important that the Fusion software is started with the correct tags.

CPU jobs are started with the --use-cpu argument.
GPU jobs are started with the --use-gpu argument.

GPU specifics:
The additional tags are crucial: --use-amd, --use-nvidia, and --use-mixed:

--use-amd will launch OpenCL on all AMD devices in the rig/computer.
--use-nvidia will launch CUDA on all NVIDIA devices in the rig/computer.
--use-mixed will launch OpenCL on all devices in the rig and also create a fallback job from the CPU Server.

Some jobs run better on AMD, while others run better on NVIDIA. That’s why it is important to provide the authentication server with the correct hardware information — so the most profitable jobs can be assigned. CUDA and OpenCL can technically run the same jobs, but the performance depends on the specific job.
The --use-mixed tag is mainly intended as a safe fallback for any hardware. It can also utilize Intel chips, onboard GPUs, and other devices. However, since it relies on a fallback CPU job, profitability will generally be low. On a laptop, though, if you’re already running Fusion, it can be a way to squeeze out a bit more from the onboard GPU.

Mixed rigs:
In theory, it should be possible to start separate instances for AMD and NVIDIA GPUs.

That means:
Run one instance with --use-nvidia to activate the NVIDIA GPUs.
Run another instance with --use-amd to activate the AMD GPUs.

It’s also possible to start an additional instance for CPUs, so in total three instances could run simultaneously. This setup still needs to be tested.

---


JIT-Compilation for Cuda / Nvidia:

Fusion uses JIT compilation. This means the full CUDA toolkit, version 12.4, is required. If it's already installed on the Hive/Linux device, it must be installed via the shell:


Example Ubuntu or HiveOS:


wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-ubuntu2004.pin

sudo mv cuda-ubuntu2004.pin /etc/apt/preferences.d/cuda-repository-pin-600

wget https://developer.download.nvidia.com/compute/cuda/12.4.0/local_installers/cuda-repo-ubuntu2004-12-4-local_12.4.0-550.54.14-1_amd64.deb

sudo dpkg -i cuda-repo-ubuntu2004-12-4-local_12.4.0-550.54.14-1_amd64.deb

sudo cp /var/cuda-repo-ubuntu2004-12-4-local/cuda-*-keyring.gpg /usr/share/keyrings/

sudo apt-get update

sudo apt-get -y install cuda-toolkit-12-4

---

Versions:

Win64: Normal Version use Cuda 12.4
Win64 Cuda 11: Use Cuda 11

Hive (for Clore Rent Rigs): Normal Version use glibc .36 and Cuda 12.4 (build with debian 11)
Hive glibc_old (for Home Rigs): use glibc .35 and Cuda 12.4 (build with ubuntu)

Linux: Normal Version use glibc .36 and Cuda 12.4 build with debian 11)
Linux glibc_old: use glibc .35 and Cuda 12.4 (build with ubuntu)


---
xmrig was used as container software.

If you would like to donate to the developers of xmrig, you can do so here:

XMR: 

48edfHu7V9Z84YzzMa6fUueoELZ9ZRXq9VetWzYGzKt52XU5xvqgzYnDK9URnRoJMk1j8nLwEVsaSWJ4fhdUyZijBGUicoD




