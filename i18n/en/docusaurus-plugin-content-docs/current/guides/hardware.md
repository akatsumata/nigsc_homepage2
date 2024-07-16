---
id: hardware
title: Hardware
---

## Overview

<table>
<tbody>
<tr>
<th colspan="3">Classification</th>
<th>Specifications</th>
</tr>
<tr>
<td rowspan="6">
Compute Nodes
<br /><br/><br/><br />
15,424 CPU cores<br /><br />
933.560 TFLOPS<br />
(CPU: 434.360 TFLOPS, GPU: 499.2 TFLOPS)<br /><br />
153.088 TB total memory
</td> 
<td rowspan="4">
Thin nodes
<br />Total: 232 units<br/><br/>
Total number of CPU cores: 14,336<br />
Total computing performance: 844.472 TFLOPS<br />
(CPU: 345.272 TFLOPS, GPU: 499.2 TFLOPS)<br />
Total memory capacity 110.080 TB
</td>
<td>
Type 1a<br />
AMD EPYC 7501 CPU.<br />
</td>
<td>
136 nodes<br />
8,704 CPU cores<br />
139.264 TFLOPS<br />
69.632 TB total memory（8GB memory/CPU core）<br/>
</td>
</tr>
<tr>
<td>
Type 1b<br />
AMD EPYC 7702 CPU. (Expansion in April 2020)
</td>
<td>
28 nodes<br />
3,584 CPU cores<br />
57.344 TFLOPS<br />
14.336 TB total memory (4GB memory/CPU core)
</td>
</tr>
<tr>
<td>
Type 2a<br />
Intel Xeon Gold 6130 CPU
</td>
<td>
52 nodes<br />
1,664 CPU cores<br />
111.800 TFLOPS<br />
19.968 TB total memory (12GB memory/CPU core)
</td>
</tr>
<tr>
<td>
Type 2b<br />
GPU installed
</td>
<td>
16 nodes<br />
384 CPU cores<br />
64GPUs (4 GPU/node)<br />
536.064 TFLOPS<br />
(CPU: 36.864 TFLOPS, GPU: 499.2 TFLOPS)<br />
6.144 TB total memory (16GB moemory/CPU core)
</td>
</tr>
<tr>
<td colspan="2">
Medium node<br />
3TB of shared memory installed
</td>
<td>
10 nodes<br />
800 CPU cores<br />
61.440 TFLOPS<br />
30.72 TB total memory (38.4GB memory/CPU core)
</td>
</tr>
<tr>
<td colspan="2">
Fat node<br />
12TB of shared memory
</td>
<td>
1 node<br />
288 CPU cores<br />
27.648 TFLOPS<br />
12.288 TB total memory (42.7GB memory/CPU core)
</td>
</tr>
<tr>
<td rowspan="2">
Storage
<br /><br />
Total storage capacity: 57.6PB
</td>
<td colspan="2">
Analysis storage(*1)<br />
For user home directories in the general analysis division and personal genome analysis division.
</td>
<td>
Lustre file system<br />
13.3PB
</td>
</tr>
<tr>
<td colspan="2">
Database storage<br />
For DDBJ database including DRA
</td>
<td>
Lustre file system<br />
40.5PB
</td>
</tr>
<tr>
<td colspan="3">Inter-node interconnect network</td>
<td>
InfiniBand 4×EDR 100Gbps fat tree<br />
(For storage, full bi-division; for compute nodes, connection bandwidth to upstream SW : connection bandwidth to downstream SW = 1:4)
</td>
</tr>
</tbody>
</table>


## Compute nodes

### Thin compute node Type 1a (HPE ProLiant DL385 Gen10; 136 computers)

Compute nodes with AMD EPYC 7501 processors.

![](Thin1a.png)
<br />

HPE ProLiant DL385 Gen10
(host name: at001 -- at136)
	

| component |model number                                       | number of computation | performance par node, etc      |
|-----------|---------------------------------------------------|-----------------------|--------------------------------|
| CPU       | AMD EPYC 7501 (32 cores)  Base 2.0GHz, Max 3.0GHz |                     2 | Total 64 core                  |
| Memory    | 32GB DDR4-2666                                    |                    16 | Total 512GB (8GB par CPU core) |
| Storage   | 1.6TB NVMe SSD x1, 3.2TB NVMe SSDx1               |                       |                                |
| Network   | InfiniBand 4xEDR                                  |                     1 | 100Gbps                        |


 
### Thin compute node Type 1b (DELL PowerEdge R6525; 28 computers)

Compute nodes with AMD EPYC 7702 processors.

![](Thin1b.png)


DELL PowerEdge R6525
(host name: at137 -- at164)

| component |model number                                        | number of computation | performance par node, etc          |
|-----------|----------------------------------------------------|-----------------------|------------------------------------|
| CPU       | AMD EPYC 7702 (64 cores)  Base 2.0GHz, Max 3.35GHz |                     2 | Total 128 core                     |
| Memory    | 32GB DDR4-2666                                     |                    16 | Total 512GB (4GB par CPU core)     |
| Storage   | 1.6TB NVMe SSD x1, 900GB SAS HDDx1                 |                       |                                    |
| Network   | InfiniBand 4xEDR                                   |                     1 | 100Gbps                            |

 
### Thin compute node Type 2a (HPE Apollo 2000 Gen10; 52 computers)

Compute nodes with Intel Xeon processors.

![](Thin2a.png)


HPE Apollo 2000 Gen10
(host name: it001 -- it052)


| component |model number                                             | number of computation | performance par node, etc        |
|-----------|---------------------------------------------------------|-----------------------|----------------------------------|
| CPU       | Intel Xeon Gold 6130 (16 cores) Base 2.1GHz, Max 3.7GHz |                     2 | Total 32 core                    |
| Memory    | 32GB DDR4-2666                                          |                    12 | Total 386GB (12GB per CPU core ) |
| Storage   | 1.6TB NVMe SSD x1, 3.2TB NVMe SSDx1                     |                       |                                  |
| Network   | InfiniBand 4xEDR                                        |                     1 | 100Gbps                          |


 
### Thin compute node Type 2b (HPE Apollo 6500 Gen10; 16 computers)

Compute nodes with four GPUs on each node.

![](Thin2b.png)

HPE Apollo 6500 Gen10
(host name: igt001 -- igt016)
	

| component |model number                                             | number of computation | performance par node, etc       |
|-----------|---------------------------------------------------------|-----------------------|---------------------------------|
| CPU       | Intel Xeon Gold 6136 (12 cores) Base 3.0GHz, Max 3.7GHz |                     2 | Total 24 core                   |
| Memory    | 32GB DDR4-2666                                          |                    12 | Total 386GB (16GB per CPU core) |
| GPU       | NVIDIA Tesla V100 SXM2                                  |                     4 |                                 |
| Storage   | 1.6TB NVMe SSD x1, 3.2TB NVMe SSDx1                     |                       |                                 |
| Network   | InfiniBand 4xEDR                                        |                     1 | 100Gbps                         |


 
#### (Reference) GPU Specifications

| Properties                                                 |  Value                  |
|------------------------------------------------------------|-------------------------|
| name                                                       | NVIDIA Tesla V100 SXM2  |
| number of core                                             | 640                     |
| clock speed                                                | 1,455MHz                |
| peak performance of single precision floating point number | 15TFLOPS                |
| peak performance of double precision floating point number | 7.5TFLOPS               |
| single core theoretical performance                        | 1.3GLOPS                |
| memory size                                                | 16GB(GDDR5)              |
| memory bandwidth                                           | 900GB/sec               |
| memory bandwidth per 1GFLOPS                               | 266GB/sec               |
| connection bandwidth                                       | 8 (PCIe2.0 x16)GB/sec   |


### Medium compute node (HPE ProLiant DL560 Gen10; 10 computers)

[The Medium node has been partially migrated to Ubuntu Linux and a new Gride Engine queue (medium-ubuntu.q) has been established. For more information, see the announcement.](/blog/2024-07-08-news_medium-ubuntu-q)


These nodes are compute nodes with 80 cores with 3 TB of physical memory, suitable for running large memory intensive programs such as de novo assembler, etc. You can use it by job submission under Grid Engine.


![](Medium.png)


HPE ProLiant DL560 Gen10
(host name: m01 -- m10)


| component |model number                                             | number of computation | performance par node, etc           |
|-----------|---------------------------------------------------------|-----------------------|-------------------------------------|
| CPU       | Intel Xeon Gold 6148 (20 cores) Base 2.4GHz, Max 3.7GHz |                     4 | Total 80 core                       |
| Memory    | 32GB DDR4-2666                                          |                    48 | Total 3,072GB (38.4GB per CPU core) |
| Storage   | 1TB SATA HDD                                            |                     2 | 1TB (RAID1)                         |
| Network   | InfiniBand 4xEDR                                        |                     1 | 100Gbps                             |

 
### Fat compute node (HPE Superdome Flex; one computer)

[The fat node hardware (that is, HPE ProLiant DL560 Gen10 and HPE Superdome Flex) do not support Ubuntu Linux and could not be migrated from Cent OS 7.9 to Ubuntu Linux 22.04 at the scheduled maintenance in November 2023.](/blog/2023-11-24-scheduled-maintenance#work-description)

A total of 12 TB of shared memory compute nodes are configured by connecting HPE Superdome Flex 2 chassis with Superdome Flex grid interconnects.

You can use FAT nodes by application only.

![](Fat.png) 

HPE Superdome Flex
(host name: fat1)
	
| component |model number                                             | number of computation | performance par node, etc            |
|-----------|---------------------------------------------------------|-----------------------|--------------------------------------|
| CPU       | Intel Xeon Gold 6154 (18 cores) Base 3.0GHz, Max 3.7GHz |                    16 | Total 288 core                       |
| Memory    | 32GB DDR4-2666                                          |                   192 | Total 12,288GB (47.2GB per CPU core) |
| Storage   | 1.2TB SAS HDD                                           |                     4 | 2.4TB (RAID1)                        |
| Network   | InfiniBand 4xEDR                                        |                     1 | 100Gbps                              |


## Storage

### Analysis storage


| access path | Effective Capacity | Usage                                      | Peak Performance | Configuration  
|-------------|--------------------|--------------------------------------------|------------------|--------------------------------------------------|
| /lustre7    | 8.0PB              | home directories in the general analysis division         | 35GB/sec or more | DDN SFA14KXE+SS9012, DDN 1U server, DDN SFA7700X |
| /lustre8     | 5.3PB              | home directories in the personal genome analysis division | 35GB/sec or more | DDN SFA14KXE+SS9012, DDN 1U server, DDN SFA7700X |



### Database storage

| access path | Effective Capacity | Usage                                      | Peak Performance | Configuration  
|-------------|--------------------|--------------------------------------------|------------------|--------------------------------------------------|
| /lustre9    | 40.5PB              | DDBJ work                                  | 150GB/sec         | DDN ES400NVX2 + DDN SS9024 |


