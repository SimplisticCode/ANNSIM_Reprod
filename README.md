# ANNSIM_Reprod
This repository contains the material to reproduce the results for the paper: Synthesizing Orchestration Algorithms For FMI 3.0, which appears on ANNSIM 2023.


## Matlab Code:

The Matlab code is located in the folder `Matlab Code` and contains 3 Simuliink models:

* `Powersystem_FMU.slx`: This model contains the FMU of the power system model.
* `Discrete_EKF_2FMUs.slx`: This model contains the FMU of the discrete EKF / Kalman filter /State estimator.
* `Discrete_EKF_Controller.slx`: This model contains the FMU of the controller.

Note that the Simulink models cannot at the time of exported as FMI 3.0 FMUs as the FMI 3.0 export is not yet supported in Simulink. 

## Scala Code

The Scala code can be found in this repository: <https://github.com/INTO-CPS-Association/synchronous_clock_cosimulation/tree/main/SynchronousClockedOrchestrator/synchronousclockedorchestrator>.
We link to the repository as the code is ongoing development to support more features of FMI 3.0 - more specifically, the support for Scheduled Execution of FMUs.

Nevertheless, we recommend running the code using the docker image, as this will ensure that the correct version of the code is used and that all dependencies are installed.

## Docker Image

We recommend using the docker image to run the orchestrator. This only requires that docker is installed on the system. Docker can be installed from [here](https://docs.docker.com/get-docker/).
The docker image can be found on Docker Hub: <https://hub.docker.com/repository/docker/simonthrane/synchronous_clocks_orchestrator>.

The image can be pulled using the following command:

```bash
    docker pull simonthrane/synchronous_clocks_orchestrator:latest
```

The orchestrator can be run using the following command:

```bash
    docker run -it --rm \
        -v "${PWD}":/app/bin/user \
        --name synchronousclocks_orchestrator  \
        simonthrane/synchronous_clocks_orchestrator:latest \
        --simulate --folder /app/bin/user/
```

This will start a simulation of the PowerSystem model described in the paper. The results will be saved in the current directory in CSV-format.