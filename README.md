# Pantheon
Programming Assignment 3
README - Pantheon Network Experiments
Overview
This project uses the Pantheon framework to evaluate and compare various TCP congestion control algorithms, including BBR, Vegas, Cubic, and Copa. The goal is to measure performance in a simulated network environment using consistent runtime conditions and network traces.
Requirements
•	Operating System: Ubuntu 20.04 or newer
•	Python: Version 2.7
•	Packages and Tools:
o	mahimahi
o	python-pip
o	cmake, g++, make
o	libssl-dev, libboost-all-dev, and other Pantheon dependencies
Installation
1.	Clone the Repository
git clone https://github.com/StanfordSNR/pantheon.git
cd pantheon
2.	Install System Dependencies
sudo apt update
sudo apt install python-pip mahimahi cmake g++ make libssl-dev libboost-all-dev
3.	Install Python Dependencies
sudo python2 get-pip.py
sudo pip2 install -r requirements.txt
4.	Set Up Schemes
python2 src/experiments/setup.py --schemes "vegas bbr copa cubic" --setup
Running Experiments
To compare the performance of different congestion control algorithms:
python2 src/experiments/test.py local \
  --schemes "vegas cubic bbr" \
  --run-times 1 \
  --runtime 60 \
  --data-dir result/part_low_latency \
  --uplink-trace src/experiments/50mbps.trace \
  --downlink-trace src/experiments/50mbps.trace \
  --prepend-mm-cmds "mm-delay 5"
Analyzing Results
After the experiment runs:
python2 src/analysis/analyze.py --data-dir result/part_low_latency
This generates performance plots comparing throughput, latency, and fairness across schemes.
Output Structure
result/
└── part_low_latency/
    ├── log_vegas*
    ├── log_bbr*
    ├── log_cubic*
    └── pantheon_metadata.json
Reproducibility
All experiments are reproducible using the commands above. Ensure that all dependencies are installed and the directory structure is preserved. The result/ folder will contain logs and plots for grading and comparison.
Notes
•	Ensure mahimahi is functioning correctly on your system.
•	If needed, update trace files or parameters to match specific experiment goals.

