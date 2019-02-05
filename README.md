Fleuron: Ornament Extractor
===========================

NOTE:  this is an updated version of the fleuron code located at:
<https://github.com/dgorissen/fleuron>.  This update works with MacOSX Mojave
and uses newer pip repository packages.

Given a directory of TIF images from scanned books Fleuron will extract the
printers ornaments.

Prerequisites
------------

* python3
* pip3

Installation
------------

Instructions are for venv, though environments such as anaconda should work
as well.

Create the virtual environment with:

    python3 -m venv <desired folder name>

Once created, enter the folder and start the environment with:

    source bin/activate

To check that the virtual environment is set up properly, enter:

    type python3
    type pip3

to verify that the executables are linked to inside the environment, rather 
than to any default python or pip installations on the system.

Inside the environment, clone the repository, navigate to the directory and run:
```python
$> pip3 install -r requirements.txt
$> python3 setup.py sdist
$> pip3 install dist/fleuron-x.x.x.tar.gz
```

Alternatively if you want to develop/change the code run

    pip3 install -e .`

If you want to install it just for your local user (not system wide) add the
--user flag.

To uninstall simply run:

`   pip3 uninstall fleuron`

Usage
-----

A script called *fleuron* will be installed and should be available on your path.
If it is not on your path you just need to add the python script directory to
your $PATH environment variable.

Run `fleuron -h` for full usage information but invocation should be as simple
as:

`$>fleuron /path/to/directory/of/TIFF/files`

Note any extracted ornaments will be created and saved in the same directory!

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
