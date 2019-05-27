# analysis
Analysis of inference methods on standard population models

# how to set up your environment to run the analysis
We recommend you start by creating a new `conda` environment for the analysis. 

```
conda create -n popsim_env_test python=3.6.8 --yes
conda activate popsim_env_test
```

Next clone and install `stdpopsim`
```
git clone https://github.com/popgensims/stdpopsim.git
cd stdpopsim
python setup.py install
cd ..
```

Now clone the analysis repo, and install its dependencies
```
git clone https://github.com/popgensims/analysis.git
cd analysis/

for c in terhorst bioconda defaults conda-forge; do conda config --add channels $c; done
conda install --file requirements.txt --yes
````

For using `msmc` we need to download and compile it to play nice
with the conda environment that we have set up.
```
cd extern
git clone https://github.com/stschiff/msmc.git
cat msmc_makefile_stdpopsim_patch > msmc/Makefile && cd msmc && make
cd ../../
```

> Note that I have not uploaded the conda package smcsmc-core or pip package smcsmc, and they are both local to me right now. So for that reason I haven't included it in the requirements.txt until it is actually live.)

For using SMCSMC we need to install both the python front end and the C++ backend. The recomended installing route is

```sh
conda install -c terhorst smcsmc 
```

which installs the SMCMSC binary (`smcsmc-core`) and the python package called `smcsmc` along with dependencies. 

Further instructions can be currently found in each task directory
