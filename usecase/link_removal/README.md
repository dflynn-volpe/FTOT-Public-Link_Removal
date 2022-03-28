

## Modify FTOT code

[Download and install FTOT](https://github.com/VolpeUSDOT/FTOT-Public/wiki/FTOT-Installation-Guide) if you haven't already done so, and install the documentation and scenarios.

Two files in the FTOT code need to be modified for this use case. They are as follows:

- `ftot_networkx.py`
	+ Modified to keep temporary shapefiles. This adds size to the output of each scenario, but allows us to make modifications to the shapefiles
- `ftot_routing.py`
	+ Modified to not add back in interstates to the road network. Without this step, an analysis of the road network would always include the national interstate system.
	+ Also modified to use only a 50 mile buffer around the selected area. This makes the scenario analysis more specific to the local network.

Copy these files from the location of this file to the location of your FTOT installation, which likely is `C:\FTOT\program`.

## Using this code

This code is written for Python 3.x, using Jupyter Notebooks to interact with the outputs of FTOT runs, calculate evenness as a proxy of resiliency, and carry out sequential link removal and recalculation of network performance.

The Python dependences are detailed in `environment.yml`. This assumes you have an installation of Python 3.x and conda. These steps follow [this reference](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-from-an-environment-yml-file). You only need to create the environment once.

From your Anaconda Prompt, navigate to the location where you cloned this repository, and then navigate to the `\usecase\link_removal` subfolder and run the following:

```
conda env create -f environment.yml
```

You should see `FTOTenv` show up as an available environment, when checking your environments with:

```
conda info --envs
```

You can then launch Jupyter Notebook by the following steps:

```
conda activate FTOTenv
jupyter notebook
```

You only need to create the environment once; thereafter, you can simply `conda activate FTOTenv` and `jupyter notebook`.

If the Jupyter Notebook instance launches with a warning about the kernel, you may need to manually select `FTOTenv` as the kernel to use.



## Run quick start scenario

Run quick start 7 now, using the modified FTOT code.
Browse to `C:\FTOT\scenarios\quick_start\qs7_rmp_proc_dest_multi_inputs\Default` and double-click `run_v6_1.bat`.

## Conduct link removal disruptions

From the Jupyter Notebook window, browse to `Conduct_Link_Removal.ipynb` to begin this module.
