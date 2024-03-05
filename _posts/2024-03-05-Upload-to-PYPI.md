---
layout: post
slug: Upload MiSleep to pypi
---

MiSleep got its basic version already, which is version 0.1.0. So I decided to open it to pypi.

## Basic architecture of folder.
The folder should contains the following:
```
- MiSleep
    - MiSleep
        - __init__.py
        - gui
        - io
        - preprcessing
        - utils
        - viz
    - LISCENSE
    - README.md
    - setup.py
```

## LISCENSE
I followed Dr. Raphael's `yasa` package and use the `BSD License`, check [yasa github](https://github.com/raphaelvallat/yasa/tree/master).
So the content is as following:
```
BSD 3-Clause License

Copyright (c) 2018, Raphael Vallat
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this
   list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its
   contributors may be used to endorse or promote products derived from
   this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

## README.md
In the README.md is the description about your package, and you can self-define it as you like.

## setup.py
This is important for package, I follow Dr. Raphael again [setup.py](https://github.com/raphaelvallat/yasa/blob/master/setup.py), and my configration is like:
```python
# -*- coding: UTF-8 -*-
# Copyright (C) 2024 Xueqiang Wang

DESCRIPTION = "MiSleep: Mice Sleep EEG/EMG visualization, scoring and analysis."


DISTNAME = "MiSleep"
MAINTAINER = "Xueqiang Wang"
MAINTAINER_EMAIL = "swang@gmail.com"
URL = "https://github.com/BryanWang0702/MiSleep/"
LICENSE = "BSD (3-clause)"
DOWNLOAD_URL = "https://github.com/BryanWang0702/MiSleep/"
VERSION = "0.1.0"

INSTALL_REQUIRES = [
    "numpy>=1.18.1",
    "matplotlib"
    "scipy",
    "pyedflib",
    "hdf5storage",
]

PACKAGES = [
    "MiSleep",
]

CLASSIFIERS = [
    "Intended Audience :: Science/Research",
    "Programming Language :: Python :: 3.8",
    "Programming Language :: Python :: 3.9",
    "Programming Language :: Python :: 3.10",
    "Programming Language :: Python :: 3.11",
    "License :: OSI Approved :: BSD License",
    "Operating System :: POSIX",
    "Operating System :: Unix",
    "Operating System :: MacOS",
]

try:
    from setuptools import setup
except ImportError:
    from distutils.core import setup

if __name__ == "__main__":
    setup(
        name=DISTNAME,
        author=MAINTAINER,
        author_email=MAINTAINER_EMAIL,
        maintainer=MAINTAINER,
        maintainer_email=MAINTAINER_EMAIL,
        description=DESCRIPTION,
        license=LICENSE,
        url=URL,
        version=VERSION,
        download_url=DOWNLOAD_URL,
        include_package_data=True,
        packages=PACKAGES,
        classifiers=CLASSIFIERS,
    )
```

## Create an account in pypi
Create an account in pypi, and generate a token for your package, here I generated a token for misleep.

![Alt text](resource/generate_token.png)

## Upload package to pypi
```
python setup.py sdist
python setup.py sdist bdist_wheel --universal
twine upload dist/*
```

## pip install
Done, now can use the `pip install misleep` to install the package.
