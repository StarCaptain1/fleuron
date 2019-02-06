Fleuron: Ornament Extractor
===========================

Given a directory of TIF images from scanned books Fleuron will extract the
printers ornaments.

NOTE:  this is an updated version of the fleuron code located at:
<https://github.com/lrm25/fleuron>.  The original was written for Windows, but this update 
works with MacOSX Mojave. It uses newer pip repository packages and is supplied with an 
extended README to accomodate those who are most likely to use this program: scholars of 
book history who may be less dextrous with python and/or navigating terminal.

Prerequisites
------------

* python3
* pip3

NOTE:  Open terminal and enter `type python`. If the return indicates that python is 
aliased to python3, and if entering `pip --version` also indicates that it points to 
a version 3 build of python, then you can omit the '3' at the end of the following commands. 
Anaconda does not have `pip3`, so as long as pip points to a version 3 build, you're OK.

Installation
------------

Instructions are for venv or anaconda on a Mac OSX system.

### 1a. If using venv:

Open terminal and navigate to the directory where you wish to store Fleuron and/or 
establish the virtual environment to house it.

Create the virtual environment with:

    pythonw -m venv <desired folder name>

A folder with <your chosen folder name> should appear in the directory.

Once created, enter this folder [cd <folder name>] and activate the virtual environment with:

    source bin/activate

### 1b. If using anaconda:

Create a folder in your chosen directory, enter this folder, and create a virtual environment with:

    conda create -n <desired environment name>  python=3.7.2 anaconda

Activate the virtual envrionment with:

    conda activate <environment name>

Install the virtual python framework build with:

    conda install python.app

### 2. All (whether using venv or anaconda)

To verify that the executables are linked to the inside of the environment, rather 
than to any default python or pip installations on the exterior system, enter:

    type python3
    type pip3 (or for anaconda, make sure that `type pip` points to a python
    3 version)

From inside the environment (the directory you are currently in), clone the Fleuron repository by entering:

    git clone <the 'clone or download' URL copied from the GitHub repository for this version>

For assistance with cloning, see: <https://help.github.com/articles/cloning-a-repository>

### 3. Navigate to the "fleuron" directory within the virtual environment you created [cd <fleuron>]

If using venv, enter:

    pip3 install -r requirements.txt

If using anaconda, enter:

    pip install -r requirements.txt

Then, if using anaconda, run the following command to allow a dependency, matplotlib, to find the
framework build:

    echo "backend: TkAgg" > ~/.matplotlib/matplotlibrc

### 4. All (whether using venv or anaconda)

Run the following commands:

#### venv

    python3 setup.py sdist 
    pip3 install dist/fleuron-0.9.0.tar.gz

#### anaconda

    pythonw setup.py sdist
    pip install dist/fleuron-0.9.0.tar.gz

Alternatively, if you want to develop/change the code with venv, enter:

    pip3 install -e .

Which for anaconda would be:

    pip install -e .

If you want to install it just for your local user (not system wide) add the
--user flag.

To uninstall in venv, run:

    pip3 uninstall fleuron

Or, in anaconda:

    pip uninstall fleuron

Usage
-----

A script called *fleuron* will be installed and should be available on your path.
If it is not on your path you just need to add the python script directory to
your $PATH environment variable.

Identify the path to the directory where you have stored your TIFF images containing printer's ornaments.

You can run `fleuron -h` for full usage information, but processing images with Fleuron should be as simple
as:

`$>fleuron /path/to/directory/of/TIFF/files`

Note 1: the path to the directory for your TIF files should not include any individual file names. 
Fleuron should process all TIFs in the directory on its own. If you include an individual TIF file name and extension, 
you will be returned an error.

Note 2: any extracted ornaments will be created and saved in the same directory.

Note 3: if terminal indicates trouble locating the TIF file(s), you may need to capitalize their file extensions.

Note 4: if you attempt to run Fleuron on image files and are returned an error telling you that python has not 
been installed as a "framework," open a second terminal window and run the following command from the initial directory:

    echo "backend: TkAgg" > ~/.matplotlib/matplotlibrc
    
Then navigate to ~/.matplotlib and open the file 'matplotlibrc' in a script editor. In 'matplotlibrc,' paste the following text, save and close:

    backend: TkAgg
    
Close the second terminal window and attempt to run Fleuron on your TIF files again.

Caveats
-------

While Fleuron will try to catch all ornaments the performance will depend
strongly on the quality and format of the input images. The approach taken is a
morphological one which means that (degraded) ornaments that resemble the
morphology of text will tend to be missed.

An extension could be to use an OCR engine or rely upon the extracted text to
disambiguate further. Note though that no approach will give perfect accuracy
in all cases.

Useful projects worth exploring for further extension include:

* [gamera](http://gamera.informatik.hsnr.de/)
* [ocropy](https://github.com/tmbdev/ocropy)
* [tesseract](https://github.com/gregjurman/tesserwrap)


License
-------

BSD. See LICENSE.md

Contact
-------

Hazel Wilkinson <hw442@cam.ac.uk>

For Mac updates:
Luke McCrone <luke.r.mccrone@gmail.com>

For application and extensions:
Pierce Williams <piercew@cmu.edu>
