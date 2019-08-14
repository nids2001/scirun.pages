---
title: Python API 0.2
category: info
tags: python
---

The API contains global functions for network editing, file management, module state modification, and data object extraction and insertion.

Some functions are not available for execution within the `InterfaceWithPython` module, since they are not useful in that context and can cause instability. They are marked with a (*).

## Global functions

### Network editing
* `scirun_add_module("ModuleName")`
  * Adds a new instance of a module to the network. Returns the module ID as a string. (*)
* `scirun_remove_module("ModuleID")`
  * Removes the module specified by the ID string. (*)
* `scirun_execute_all()`
  * Executes the entire current network. (*)
* `scirun_module_ids()`
  * Returns a list of all module ID strings in the current network, sorted by module creation time.
* `scirun_connect_modules("ModuleIDFrom", fromIndex, "ModuleIDTo", toIndex)`
  * Connects ports between two modules by index. From is the output, To is the input. (*)
* `scirun_disconnect_modules("ModuleIDFrom", fromIndex, "ModuleIDTo", toIndex)`
  * Used to disconnect two modules, with the same syntax as connecting. (*)

### Network file management
* `scirun_save_network("Filename.srn5")`
  * Saves the current network file. (*)
* `scirun_load_network("Filename.srn5")`
  * Loads the specified network file. (*)
* `scirun_import_network("Filename.srn")`
  * Imports the specified v4 network file. (*)
* `scirun_quit_after_execute()`
  * Enables quitting SCIRun after the next network execution is complete. (*)
* `scirun_force_quit()`
  * Quits SCIRun immediately. (*)

### Module state editing
* `scirun_get_module_state("ModuleID", "StateVariableName")`
  * Returns the value of a the specified module state variable.
* `scirun_set_module_state("ModuleID", "StateVariableName", value)`
  * Sets the specified module state variable's value.
* `scirun_dump_module_state("ModuleID")`
  * Returns a dictionary with the entire state of the specified module.
* `scirun_get_module_transient_state("ModuleID", "StateVariableName")`
  * Returns the value of a the specified module transient state variable.
* `scirun_set_module_transient_state("ModuleID", "StateVariableName", value)`
  * Sets the specified module transient state variable's value. Used to pass data values (strings, matrices, fields [coming soon]) back to modules.

### Module/Datatype input
* `scirun_get_module_input_type("ModuleID", portIndex)`
  * Returns the type of the input data object on the specified port.
* `scirun_get_module_input_object("ModuleID", "PortName")`
  * Returns a special `PyDatatype` wrapper object containing a copy of the data on the specified input port, by name.
* `scirun_get_module_input_value("ModuleID", "PortName")`
  * Returns a Python object containing a copy of the data on the specified input port.
* `scirun_get_module_input_object_by_index("ModuleID", portIndex)`
  * Returns a special `PyDatatype` wrapper object containing a copy of the data on the specified input port, by port index.
* `scirun_get_module_input_value_by_index("ModuleID", portIndex)`
  * Returns a Python object containing a copy of the data on the specified input port, by index.

### InterfaceWithPython special syntax
* This module lets you set input/output variable names in the module UI. Once this is done (or by using the defaults), one can use assignment syntax to read input data and send output data.
  * Examples
     * `pythonOutput = "hello"` will send a string to the output port associated with `pythonOutput`
     * `field = inputField1` will extract a field object from the input port associated with `inputField1`
     * `outputString1 = "string concat " + inputString1` Input/Output can be combined on the same line.
  * Note: for output variable assignment, make sure to include spaces around the `=`.
  
  ####  InterfaceWithPython Top-Level Script
  
  In the InterfaceWithPython there is a "Top-Level Script" tab which allows users to run matlab code in a broader scope on execution of the InterfaceWithPython Module.  This is helpful if
  
  

## Installing packages
* If there is an installation of the packages with other python builds on the machine, the system path can be used to use those packages.  This is likely the easiest way to use python packages in SCIRun, and will also likely to be easiest to maintain.  However, to use packages from another Python build, the Python versions will need to match.  Once the packages are installed, use the SCIRun triggered events to modify the python path to include these packages.

### Installing Python to maintain Python packages.

The main advantage of doing this step is that a seperate Python will likely have pip or multiple packages already installed, unlike the SCIRun Python distribution (we are working on it).  Most distributions will likely work; some operating systems come with a python distribution that may work, yet it may be an outdated version. [Anaconda](https://www.anaconda.com/distribution/#download-section) is a good choice because most of the commonly used packages will be installed when it is installed.  However, the cleanest option will likely be installing [Python's own distribution](https://www.python.org/downloads/), then to install the packages that you want to use.  The both these distributions should come with pip installed, which makes it easy to install most common packages.

*Make sure the python versions of the seperate Python installation matches the version that SCIRun is using*
To check the Python version in SCIRun, simply open the Python Console, it show print the version in the initialization method.  You can also get the version when running on the command line by using the `-v` flag.



### Installing numpy, scipy, and other major packages with pip

Once you have a seperate Python with pip installed, installing packages is usually farily straightforward.  The basic command to install numpy is:
`pip install numpy`
However, if you have multiple python installations, it may be necessary to specify which pip to use.  The pip version will need to match the python version you intend to use.  Often the version name is appended to the function call:
`pip3.5 install numpy`
Yet it may be necessary to point to the specific installation:
`/Library/Frameworks/Python.framework/Versions/3.5/bin/pip3.5 install numpy`
for instance. If ther is an error installing the package, try upgrading pip first:
`pip3.5 install --upgrade pip`


### Installing Matlab engine for python in SCIRun

Full installation instructions for installing the Matlab engine in Python are found [on the mathworks site](http://www.mathworks.com/help/matlab/matlab_external/install-the-matlab-engine-for-python.html).  Keep in mind that each Matlab version will only support a few Python versions, and the Python version much match what is running in SCIRun (see above).  Also, it would probably help if Python Matlab engine installation was in the same location as the other packages to be used in SCIRun.  It is helpful to have numpy and scipy installed aswell.

To install the Matlab engine in Python run in the terminal:

```
cd "matlab_root"/extern/engines/python
"Python_installation"/bin/python3.5 setup.py build install
```
### [Adding packages to the Python Path in SCIRun](#python-path)

In order to use the installed packages, SCIRun's Python has to be able to find them.  If the package files are located in the Python Path, the can be used with the `import` function.  The python path can be modified in many ways, but the most practical for general purpose is to use the triggered events in SCIRun.  Triggered events are explained in [another section](#triggered-events), but we will explain how to use it to modify the Python Path.

Open up the Triggered Event Window in SCIRun and choose the "Application Start" tab.  Make sure that this script is enabled by clicking the "Enabled" checkbox.  Now enter a script that will add the directories to the package installation in the textbox.  It will look something like this:

```
import sys
sys.path.append('/Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages/')
```

There can be many directories or many `sys.path.append(...)` calls as needed.  This script is saved and will run everytime SCIRun starts, and therefore it will update the path.

If there are module or package paths that need to be set on a network basis (rather than for every network), the InterfaceWithPython module can acheive this with the "Top-Level Script" Tab.  This tab will execute the code in this tab on a global scale (until SCIRun is closed), so a script similar to the triggered events example will be saved and executed only for the network.

  
## Matlab engine in SCIRun 5 (through python)

In SCIRun 5, Matlab code and functions can be run using the matlab engine for python in the python console or python interface.  To do so, make sure that the matlab engine is installed (previous section).
Full documentation can be found [here](http://www.mathworks.com/help/matlab/matlab-engine-for-python.html).

### Matlab code block

In the InterfaceWithPython module, there is a Matlab code block option.  This is a series of Matlab functions that are serparated by `%%`.  The InterfaceWithPython module will attempt to convert the native Matlab code in the block as Python code.  The commands cannot be complex in that they must only contain one function per line.  For example:
```
%%
A = magic(3);
[evec, eval] = eig(A);
%%
```
Users can insert a Matlab code block with the button in the InterfaceWithPython UI, or bby typing `%%`.  To use the Matlab code block, make sure:
- Matlab and the Python Matlab engine are installed
- The Matlab Python module is in the Python Path in SCIRun
- The ["MatlabConversion.py"](https://github.com/SCIInstitute/SCIRun/blob/master/src/Modules/Python/MatlabConversion.py) file is in the Python Path.  This is found in the source code: "SCIRun/src/Modules/Python".
- Matlab functions are in the Matlab path.  This is best accomplished in the Matlab UI.

The Matlab Code Block is experimental code, so it will likely not work with complex Matlab functionality. However, if there is a code block detected, SCIRun will start Matlab and it will remain open until SCIRun is closed.   The python variable names should match the variable names in the assignment.

## [Triggered Events](#triggered-events)

Triggered events in SCIRun execute a python script upon certain SCIRun events.  Possible events include: application start,  network load, and adding a module.  The scripts and settings can be modified in the triggered events window.  The triggered event scripts allow for increased customization such as: modifying the Python path, changing the module default settings, and others.  Instructions on how to use triggered events to modify the Python path are [describe previously](#python-path)



## Python Macros

## Running Python Scripts
