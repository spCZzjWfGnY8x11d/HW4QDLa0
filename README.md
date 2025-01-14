# Experimental Data and Scripts
This repository contains experimental data and scripts used for performance evaluation. The data includes results from various measurements, and the scripts are designed to collect CPU, memory, network throughput, and database throughput metrics.

## Contents
### data.zip
This file contains the experimental data generated during the evaluation. The data is organized into Excel files, with each file corresponding to a specific experiment. The experiment number can be found at the end of the Excel file names.

### scripts.zip
This file contains the scripts used to collect various performance metrics, including CPU usage, memory usage, network throughput, and database throughput. These scripts were used to monitor and analyze the system during the experiments.

## How to Use
### 1. Deploy the System and the Tester
Download the core network source code from the corresponding GitHub repository and follow the instructions to install:
- Free5GC: [https://github.com/free5gc/free5gc](https://github.com/free5gc/free5gc)
- Open5GS: [https://github.com/open5gs/open5gs](https://github.com/open5gs/open5gs)
- OpenAirInterface: [https://gitlab.eurecom.fr/oai/cn5g/oai-cn5g-fed/-/blob/master/docs/DEPLOY_HOME.md](https://gitlab.eurecom.fr/oai/cn5g/oai-cn5g-fed/-/blob/master/docs/DEPLOY_HOME.md)

We recommend using specialized commercial testing tools as they offer higher rates and greater reliability. However, we also provide open-source testing tools for reference.

Download the testing tools from the corresponding websites and follow the steps in the links to install them.
Optional testing tools include:
- UERANSIM: [https://github.com/aligungr/UERANSIM](https://github.com/aligungr/UERANSIM)
- gNBSim: [https://github.com/omec-project/gnbsim](https://github.com/omec-project/gnbsim)
- My-5GRANTester: [https://github.com/my5G/my5G-RANTester](https://github.com/my5G/my5G-RANTester)

### 2. Configuration and Connectivity
**Configuration**: 
First, increase the number of subscribed UEs in the core network to 500,000. 
- For Open5GS and Free5GC, this can be done through the WebUI.
- For OpenAirInterface, you need to modify its data files.
The key point here is to configure the appropriate `MNC` and `MCC` for the UEs to facilitate connectivity with the testing tools.

**Connectivity**: 
1. The primary condition for connecting the core network with the testing tools is that they must be on the same subnet.
2. Next, you need to modify the configuration files on both sides to achieve consistency. For more information, refer to the [UERANSIM configuration](https://github.com/aligungr/UERANSIM) and connectivity tutorial.
3. Specifically, several important parameters need to be set, such as `MNC`, `MCC`, `N2 IP`, `N3 IP`, `TAC`, `CellID`, `AMF`, `OPc`, etc.

### 3. Conduct Testing
1. Download `script.zip` and extract it to the corresponding folder. Adjust flexibly according to the process names of different open-source core networks.
2. Then, execute our test script. Next, sequentially start the core network and the testing tools. The testing tools will generate the corresponding traffic.
3. After the traffic generation is complete, the testing tools, the core network, and the test script are shut down sequentially to obtain the test results.

## Troubleshooting & Resources
We have listed some issues encountered during our deployment to help with the process:
1. It is recommended that the process version of the core network be used for deployment.
   - Although the Docker version is easier to deploy, it may lead to inaccuracies in measurement work. Our scripts are prepared for the process version.
3. Why does the core network fail at high test rates?
   1.  First, check whether the physical/virtual machine resources are sufficient. A number of 500,000 UEs requires high resources for both the core network and the testing tools.
   2.  Additionally, some configurations need to be adjusted, such as the IP pool size in the SMF config and the index settings in the corresponding database.
4.  Examples of connectivity configurations can be found at [tester config](https://github.com/aligungr/UERANSIM/tree/master/config).


## License
This project is licensed under the GNU General Public License (GPL).
