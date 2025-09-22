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
