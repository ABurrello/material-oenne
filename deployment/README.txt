## clone the repository
git clone https://github.com/pulp-platform/dory.git
## build the docker inside dory repository. Run in a shell executed with sudo.
sudo docker build --tag tutorial_dory .
## launch the docker
docker run -it tutorial_dory bash
## source gap8 board (inside the gap_sdk folder)
source sourceme.sh
## clone inside the material-oenne to have the tutorial there
git clone https://github.com/ABurrello/material-oenne.git
## install dory
git clone https://github.com/pulp-platform/dory.git
cd dory
git submodule update --remote --init dory/dory_examples
git submodule update --remote --init dory/Hardware_targets/PULP/Backend_Kernels/pulp-nn
## activate the environment
source /dory_env/bin/activate
## create the first network and test it
python3 network_generate.py Quantlab PULP.PULP_gvsoc ./dory/dory_examples/config_files/config_Quantlab_MV1_8bits.json
cd application/
make clean all run CORE=8 platform=gvsoc