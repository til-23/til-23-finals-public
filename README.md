# til-final

SDK, simulator and documentation for TIL 2023 Robotics Challenge.

* ``src/``: SDK and simulator packages.
* ``config/``: SDK and simulator sample configuration files.
* ``data/``: sample audio and images for the AI tasks, sample maps used for
the path planner and simulator.
* ``docs/``: documentation and sphinx doc webpages source.
* ``stubs/``: Code stubs for participants to implement.


## Setup
**Step 1: Clone this git repo.**

It is highly recommended to install python dependencies in a virtual environment.

**Step 2: Activate virtual environment.**
```
pip install virtualenv
virtualenv -p python3.8.10 venv  # create virtual python environment with specific python version.
source <NAME_OF_VENV>/bin/activate  # on Windows, "./<NAME_OF_VENV>/Scripts/activate" to activate virtual python environment.
```

**Step 3: Install the [RoboMaster SDK](https://robomaster-dev.readthedocs.io/en/latest/python_sdk/installs.html)**

Note that the required python version for the RoboMaster SDK is between 3.6.6 and 3.8.10

**Step 4: Install the custom challenge SDK**
```sh
pip install -r requirements.txt  # install third-party dependencies
pip install .  # install the SDK from source. The '.' means install from current directory.
```

**Step 5: Install a python GUI backend.**

install a matplotlib backend to enable visualization of the simulation:
```
pip install pyqt5  # probably works for Linux as well.
```

If the above doesn't work and you're on Ubuntu, try this GUI backend:
```
sudo apt-get install python3-tk
```

**Step 6: (Optional) Install any other dependencies your custom AI models require.**

For example, the sample AI models require these.
```
pip install torch==1.12.1+cu116 torchvision==0.13.1+cu116 torchaudio==0.12.1 --extra-index-url https://download.pytorch.org/whl/cu116
export PYTHONPATH='/your/path/to/til-23-finals/stubs/yolov7'  # on Windows, replace 'export' with 'set'
```

Note: `set` command sets an environment variable temporarily only. Use 'setx' to set a variable permanently.   

## Build the documentation

Much of the technical information needed to understand and run the robotics system is provided in the Sphinx-generated docs.
Be sure to generate and view them!

```sh
# install sphinx dependencies
pip install sphinx sphinx-autoapi sphinx-rtd-theme

# Generate html docs based on source folder.
sphinx-build -b html docs/source docs/build 
```

Access the html docs at `docs/build/index.html`.

## Quickstart Example with Simulator

Open a terminal, start the scoring server:

`til-scoring config/scoring_cfg.yml -o teamName1`

In another terminal, start the simulator:

`til-simulator -c config/sim_cfg.yml`

In another terminal, start your autonomy code:

`python stubs/autonomy_starter.py --config config/autonomy_cfg.yml`

Note: Remember to change the paths in the config files to your own directories.

You can always use the `--help` option with these commands to view help messages. E.g.

`til-scoring --help`
