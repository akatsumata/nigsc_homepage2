---
id: cuda
title: "CUDA"
---

## How to submit jobs that uses GPU to Grid Engine


When submitting jobs that uses GPU, use the `-l cuda=n` (n specifies the number of GPUs to use. The upper limit is 4.) option in addition to the `-l gpu` option. If the "-l cuda=n" option is not used, the job will be submitted to gpu.q, but no GPUs can be used.

For example, when you use two GPUs, specify as follows.

```
[username@at027 ~]$ qsub -l gpu -l cuda=2 gputest.sh
Your job 10000 ("gputest.sh") has been submitted
```

The GPU can be referenced from the job by the number specified by `cuda = n`.

```
[username@at027 ~]$ cat gputest.sh
#!/bin/bash
#$ -S /bin/bash

nvidia-smi
[username@at027 ~]$ qsub -l gpu -l cuda=1 gputest.sh 
Your job 10001 ("gputest.sh") has been submitted
[username@at027 ~]$ qsub -l gpu -l cuda=2 gputest.sh 
Your job 10002 ("gputest.sh") has been submitted
[username@at027 ~]$ qsub -l gpu -l cuda=4 gputest.sh 
Your job 10003 ("gputest.sh") has been submitted
[username@at027 ~]$ cat gputesh.sh.o10001
Wed Mar  4 20:00:00 2019
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 396.26                 Driver Version: 410.66                    |
|-------------------------------|----------------------|----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  Tesla V100-SXM2...  On   | 00000000:15:00.0 Off |                    0 |
| N/A   32C    P0    39W / 300W |      0MiB / 16130MiB |      0%      Default |
+-------------------------------|----------------------|----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+
[username@at027 ~]$ cat gputesh.sh.o10002
Wed Mar  4 20:00:00 2019
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 396.26                 Driver Version: 410.66                    |
|-------------------------------|----------------------|----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  Tesla V100-SXM2...  On   | 00000000:15:00.0 Off |                    0 |
| N/A   29C    P0    39W / 300W |      0MiB / 16130MiB |      0%      Default |
+-------------------------------|----------------------|----------------------+
|   1  Tesla V100-SXM2...  On   | 00000000:16:00.0 Off |                    0 |
| N/A   30C    P0    39W / 300W |      0MiB / 16130MiB |      0%      Default |
+-------------------------------|----------------------|----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+
[username@at027 ~]$ cat gputesh.sh.o10003
Wed Mar  4 20:00:00 2019
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 396.26                 Driver Version: 410.66                    |
|-------------------------------|----------------------|----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  Tesla V100-SXM2...  On   | 00000000:15:00.0 Off |                    0 |
| N/A   32C    P0    38W / 300W |      0MiB / 16130MiB |      0%      Default |
+-------------------------------|----------------------|----------------------+
|   1  Tesla V100-SXM2...  On   | 00000000:16:00.0 Off |                    0 |
| N/A   32C    P0    39W / 300W |      0MiB / 16130MiB |      0%      Default |
+-------------------------------|----------------------|----------------------+
|   2  Tesla V100-SXM2...  On   | 00000000:3A:00.0 Off |                    0 |
| N/A   30C    P0    39W / 300W |      0MiB / 16130MiB |      0%      Default |
+-------------------------------|----------------------|----------------------+
|   3  Tesla V100-SXM2...  On   | 00000000:3B:00.0 Off |                    0 |
| N/A   31C    P0    37W / 300W |      0MiB / 16130MiB |      0%      Default |
+-------------------------------|----------------------|----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+
```

