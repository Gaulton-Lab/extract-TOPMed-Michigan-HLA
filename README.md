# Extract TOPMed and Michigan HLA
<div align="center">

<img src="https://github.com/Gaulton-Lab/t1grs/blob/master/t1grs.jpg" alt="Logo" width="100"/>

</div>

## Overview

This project provides a Docker image that can be pulled from Docker Hub and run locally. The Docker image contains all necessary dependencies and code to get started quickly.

## Prerequisites

- Docker installed on your local machine. You can download Docker from [here](https://www.docker.com/products/docker-desktop).

## Getting Started

### Pulling the Docker Image

To pull the latest Docker image from Docker Hub, use the following command:

```
docker pull kgaultonlab/t1d-grs-analysis:latest
```

### Running the Docker Container

To run the Docker container with the necessary volume mappings, use the following command (this can be run as a bash script):

```
#!/bin/bash

# Run the Docker container
docker run --name my_temp_container \
  -v /path/to/your/TOPMED_r3:/data/TOPMED_r3 \
  -v /path/to/your/Michigan_HLA:/data/Michigan_HLA \
  -v /path/to/your/ALL5_199_TOPMED_SUSIE_HLA_T1D_signals_updateID_r3.snps:/data/ALL5_199_TOPMED_SUSIE_HLA_T1D_signals_updateID_r3.snps \
  your-dockerhub-username/your-repo:latest \
  /usr/local/bin/plink2 /data/TOPMED_r3 /data/Michigan_HLA /data/ALL5_199_TOPMED_SUSIE_HLA_T1D_signals_updateID_r3.snps /output.vcf

# Copy the output file from the container to the host directory
docker cp my_temp_container:/output.vcf /path/to/your/output/output.vcf
```
Replace the paths in the -v options with your actual paths where the files are located on your host machine.

### Stopping and Removing the Container

To stop the running container, use:

```
docker stop my_temp_container
```
To remove the container, use:
```
docker rm my_temp_container
```
### Checking Container Logs

If you need to check the logs of the running container, use:
```
docker logs my_temp_container
```
### Updating the Docker Image

To update the Docker image to the latest version, pull the latest image from Docker Hub:
```
docker pull kgaultonlab/t1d-grs-analysis:latest
```
Then, stop and remove the old container, and run the new image:
```
docker stop my_temp_container
docker rm my_temp_container
docker run -d --name my_temp_container your-dockerhub-username/your-repo:latest
```

## Citation

If you use this tool, please cite:
McGrail, C., Sears, T.J., Griffin, E.N., Ghaben, A.L., Smadbeck, P., Flannick, J., Kudtarkar, P., Carter, H. & Gaulton, K. (2026). Genetic association and machine learning improve the prediction of type 1 diabetes risk. *Nature Genetics*. https://www.nature.com/articles/s41588-026-02578-y

### COPYRIGHT & LICENSE

```
Copyright Notice
This software is Copyright © 2024 The Regents of the University of California. All Rights Reserved. Permission to copy, modify, and distribute this software and its documentation for educational, research, and non-profit purposes, without fee, and without a written agreement is hereby granted, provided that the above copyright notice, this paragraph, and the following three paragraphs appear in all copies. Permission to make commercial use of this software may be obtained by contacting:

Office of Innovation and Commercialization
9500 Gilman Drive, Mail Code 0910
University of California
La Jolla, CA 92093-0910
innovation@ucsd.edu

This software program and documentation are copyrighted by The Regents of the University of California. The software program and documentation are supplied “as is”, without any accompanying services from The Regents. The Regents does not warrant that the operation of the program will be uninterrupted or error-free. The end-user understands that the program was developed for research purposes and is advised not to rely exclusively on the program for any reason.

IN NO EVENT SHALL THE UNIVERSITY OF CALIFORNIA BE LIABLE TO ANY PARTY FOR DIRECT, INDIRECT, SPECIAL, INCIDENTAL, OR CONSEQUENTIAL DAMAGES, INCLUDING LOST PROFITS, ARISING OUT OF THE USE OF THIS SOFTWARE AND ITS DOCUMENTATION, EVEN IF THE UNIVERSITY OF CALIFORNIA HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGE. THE UNIVERSITY OF CALIFORNIA SPECIFICALLY DISCLAIMS ANY WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. THE SOFTWARE PROVIDED HEREUNDER IS ON AN “AS IS” BASIS, AND THE UNIVERSITY OF CALIFORNIA HAS NO OBLIGATIONS TO PROVIDE MAINTENANCE, SUPPORT, UPDATES, ENHANCEMENTS, OR MODIFICATIONS.
```

## Contact
If you have any questions, feel free to open an issue.
