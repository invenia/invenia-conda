# invenia-conda

A repository of conda templates for open source packages.

The instructions below were run from a fresh Ubuntu docker container with the following
packages installed:

- `curl`
- `git`
- `patch`
- `build-essential`
- `vim`

## Setup

Start by downloading and installing [miniconda](http://conda.pydata.org/miniconda.html#miniconda).
NOTE: Please use the appropriate url for your operating system.
```shell
$ curl -fOsSL https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
$ bash Miniconda3-latest-Linux-x86_64.sh -b
PREFIX=/root/miniconda3
installing: python-3.7.0-hc3d631a_0 ...
Python 3.7.0 (default, Jun 28 2018, 13:15:42)
[GCC 7.2.0]
installing: ca-certificates-2018.03.07-0 ...
installing: conda-env-2.6.0-1 ...
installing: libgcc-ng-8.2.0-hdf63c60_1 ...
installing: libstdcxx-ng-8.2.0-hdf63c60_1 ...
installing: libffi-3.2.1-hd88cf55_4 ...
installing: ncurses-6.1-hf484d3e_0 ...
installing: openssl-1.0.2p-h14c3975_0 ...
installing: xz-5.2.4-h14c3975_4 ...
installing: yaml-0.1.7-had09818_2 ...
installing: zlib-1.2.11-ha838bed_2 ...
installing: libedit-3.1.20170329-h6b74fdf_2 ...
installing: readline-7.0-h7b6447c_5 ...
installing: tk-8.6.8-hbc83047_0 ...
installing: sqlite-3.24.0-h84994c4_0 ...
installing: asn1crypto-0.24.0-py37_0 ...
installing: certifi-2018.8.24-py37_1 ...
installing: chardet-3.0.4-py37_1 ...
installing: idna-2.7-py37_0 ...
installing: pycosat-0.6.3-py37h14c3975_0 ...
installing: pycparser-2.18-py37_1 ...
installing: pysocks-1.6.8-py37_0 ...
installing: ruamel_yaml-0.15.46-py37h14c3975_0 ...
installing: six-1.11.0-py37_1 ...
installing: cffi-1.11.5-py37he75722e_1 ...
installing: setuptools-40.2.0-py37_0 ...
installing: cryptography-2.3.1-py37hc365091_0 ...
installing: wheel-0.31.1-py37_0 ...
installing: pip-10.0.1-py37_0 ...
installing: pyopenssl-18.0.0-py37_0 ...
installing: urllib3-1.23-py37_0 ...
installing: requests-2.19.1-py37_0 ...
installing: conda-4.5.11-py37_0 ...
installation finished.
```

Next we'll need to install the `conda-build` package to support building our package.

```shell
$ ~/miniconda3/bin/conda install conda-build
Solving environment: done

## Package Plan ##

  environment location: /root/miniconda3

  added / updated specs:
    - conda-build


The following packages will be downloaded:

    package                    |            build
    ---------------------------|-----------------
    glob2-0.6                  |           py37_1          17 KB
    pkginfo-1.4.2              |           py37_1          39 KB
    py-lief-0.9.0              |   py37h7725739_1         3.1 MB
    liblief-0.9.0              |       h7725739_1         4.5 MB
    lz4-c-1.8.1.2              |       h14c3975_0         158 KB
    lzo-2.10                   |       h49e0be7_2         313 KB
    pyyaml-3.13                |   py37h14c3975_0         177 KB
    libxml2-2.9.8              |       h26e45fe_1         2.0 MB
    markupsafe-1.1.0           |   py37h7b6447c_0          26 KB
    python-3.7.1               |       h0371630_3        36.4 MB
    psutil-5.4.8               |   py37h7b6447c_0         313 KB
    pytz-2018.7                |           py37_0         247 KB
    conda-build-3.17.0         |           py37_0         499 KB
    openssl-1.1.1a             |       h7b6447c_0         5.0 MB
    libarchive-3.3.3           |       h5d8350f_4         1.5 MB
    icu-58.2                   |       h9c2bf20_1        22.5 MB
    patchelf-0.9               |       he6710b0_3          71 KB
    filelock-3.0.10            |           py37_0          13 KB
    cryptography-2.4.1         |   py37h1ba5d50_0         607 KB
    beautifulsoup4-4.6.3       |           py37_0         138 KB
    jinja2-2.10                |           py37_0         183 KB
    zstd-1.3.7                 |       h0b5b093_0         887 KB
    certifi-2018.10.15         |           py37_0         138 KB
    bzip2-1.0.6                |       h14c3975_5         414 KB
    tqdm-4.28.1                |   py37h28b3542_0          61 KB
    sqlite-3.25.3              |       h7b6447c_0         1.9 MB
    python-libarchive-c-2.8    |           py37_6          20 KB
    ------------------------------------------------------------
                                           Total:        81.1 MB

The following NEW packages will be INSTALLED:

    beautifulsoup4:      4.6.3-py37_0
    bzip2:               1.0.6-h14c3975_5
    conda-build:         3.17.0-py37_0
    filelock:            3.0.10-py37_0
    glob2:               0.6-py37_1
    icu:                 58.2-h9c2bf20_1
    jinja2:              2.10-py37_0
    libarchive:          3.3.3-h5d8350f_4
    liblief:             0.9.0-h7725739_1
    libxml2:             2.9.8-h26e45fe_1
    lz4-c:               1.8.1.2-h14c3975_0
    lzo:                 2.10-h49e0be7_2
    markupsafe:          1.1.0-py37h7b6447c_0
    patchelf:            0.9-he6710b0_3
    pkginfo:             1.4.2-py37_1
    psutil:              5.4.8-py37h7b6447c_0
    py-lief:             0.9.0-py37h7725739_1
    python-libarchive-c: 2.8-py37_6
    pytz:                2018.7-py37_0
    pyyaml:              3.13-py37h14c3975_0
    tqdm:                4.28.1-py37h28b3542_0
    zstd:                1.3.7-h0b5b093_0

The following packages will be UPDATED:

    certifi:             2018.8.24-py37_1      --> 2018.10.15-py37_0
    cryptography:        2.3.1-py37hc365091_0  --> 2.4.1-py37h1ba5d50_0
    openssl:             1.0.2p-h14c3975_0     --> 1.1.1a-h7b6447c_0
    python:              3.7.0-hc3d631a_0      --> 3.7.1-h0371630_3
    sqlite:              3.24.0-h84994c4_0     --> 3.25.3-h7b6447c_0

Proceed ([y]/n)? y


Downloading and Extracting Packages
glob2-0.6            | 17 KB     | ######################################################### | 100%
pkginfo-1.4.2        | 39 KB     | ######################################################### | 100%
py-lief-0.9.0        | 3.1 MB    | ######################################################### | 100%
liblief-0.9.0        | 4.5 MB    | ######################################################### | 100%
lz4-c-1.8.1.2        | 158 KB    | ######################################################### | 100%
lzo-2.10             | 313 KB    | ######################################################### | 100%
pyyaml-3.13          | 177 KB    | ######################################################### | 100%
libxml2-2.9.8        | 2.0 MB    | ######################################################### | 100%
markupsafe-1.1.0     | 26 KB     | ######################################################### | 100%
python-3.7.1         | 36.4 MB   | ######################################################### | 100%
psutil-5.4.8         | 313 KB    | ######################################################### | 100%
pytz-2018.7          | 247 KB    | ######################################################### | 100%
conda-build-3.17.0   | 499 KB    | ######################################################### | 100%
openssl-1.1.1a       | 5.0 MB    | ######################################################### | 100%
libarchive-3.3.3     | 1.5 MB    | ######################################################### | 100%
icu-58.2             | 22.5 MB   | ######################################################### | 100%
patchelf-0.9         | 71 KB     | ######################################################### | 100%
filelock-3.0.10      | 13 KB     | ######################################################### | 100%
cryptography-2.4.1   | 607 KB    | ######################################################### | 100%
beautifulsoup4-4.6.3 | 138 KB    | ######################################################### | 100%
jinja2-2.10          | 183 KB    | ######################################################### | 100%
zstd-1.3.7           | 887 KB    | ######################################################### | 100%
certifi-2018.10.15   | 138 KB    | ######################################################### | 100%
bzip2-1.0.6          | 414 KB    | ######################################################### | 100%
tqdm-4.28.1          | 61 KB     | ######################################################### | 100%
sqlite-3.25.3        | 1.9 MB    | ######################################################### | 100%
python-libarchive-c- | 20 KB     | ######################################################### | 100%
Preparing transaction: done
Verifying transaction: done
Executing transaction: done
```

Finally, we'll want to install the anaconda-client that we'll use to upload our conda builds.

```shell
~/miniconda3/bin/conda install anaconda-client
Solving environment: done

## Package Plan ##

  environment location: /root/miniconda3

  added / updated specs:
    - anaconda-client


The following packages will be downloaded:

    package                    |            build
    ---------------------------|-----------------
    decorator-4.3.0            |           py37_0          15 KB
    nbformat-4.4.0             |           py37_0         141 KB
    clyent-1.2.2               |           py37_1          18 KB
    traitlets-4.3.2            |           py37_0         133 KB
    jsonschema-2.6.0           |           py37_0          62 KB
    python-dateutil-2.7.5      |           py37_0         275 KB
    anaconda-client-1.7.2      |           py37_0         140 KB
    jupyter_core-4.4.0         |           py37_0          63 KB
    ipython_genutils-0.2.0     |           py37_0          39 KB
    ------------------------------------------------------------
                                           Total:         886 KB

The following NEW packages will be INSTALLED:

    anaconda-client:  1.7.2-py37_0
    clyent:           1.2.2-py37_1
    decorator:        4.3.0-py37_0
    ipython_genutils: 0.2.0-py37_0
    jsonschema:       2.6.0-py37_0
    jupyter_core:     4.4.0-py37_0
    nbformat:         4.4.0-py37_0
    python-dateutil:  2.7.5-py37_0
    traitlets:        4.3.2-py37_0

Proceed ([y]/n)? y


Downloading and Extracting Packages
decorator-4.3.0      | 15 KB     | ######################################################### | 100%
nbformat-4.4.0       | 141 KB    | ######################################################### | 100%
clyent-1.2.2         | 18 KB     | ######################################################### | 100%
traitlets-4.3.2      | 133 KB    | ######################################################### | 100%
jsonschema-2.6.0     | 62 KB     | ######################################################### | 100%
python-dateutil-2.7. | 275 KB    | ######################################################### | 100%
anaconda-client-1.7. | 140 KB    | ######################################################### | 100%
jupyter_core-4.4.0   | 63 KB     | ######################################################### | 100%
ipython_genutils-0.2 | 39 KB     | ######################################################### | 100%
Preparing transaction: done
Verifying transaction: done
Executing transaction: done
```
## Creating our new recipe from pypi

```
$ ~/miniconda3/bin/conda skeleton pypi pyftpdlib
Warning, the following versions were found for pyftpdlib
0.2.0
0.3.0
0.4.0
0.5.0
0.5.1
0.5.2
0.6.0
0.7.0
1.0.0
1.0.1
1.1.0
1.2.0
1.3.0
1.3.1
1.4.0
1.5.0
1.5.1
1.5.2
1.5.3
1.5.4
Using 1.5.4
Use --version to specify a different version.
Using url https://files.pythonhosted.org/packages/0d/64/eb0daca74956d0e6849b71c5ba99ab873ec59b888a1d7651d92fb686ee04/pyftpdlib-1.5.4.tar.gz (181 KB) for pyftpdlib.
Downloading pyftpdlib
PyPI URL:  https://files.pythonhosted.org/packages/0d/64/eb0daca74956d0e6849b71c5ba99ab873ec59b888a1d7651d92fb686ee04/pyftpdlib-1.5.4.tar.gz
Using cached download
Unpacking pyftpdlib...
done
working in /tmp/tmpj830mzklconda_skeleton_pyftpdlib-1.5.4.tar.gz
Solving environment: ...working... done

## Package Plan ##

environment location: /root/miniconda3/conda-bld/pyftpdlib_1543881244965/_test_env_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_plac

The following NEW packages will be INSTALLED:

    ca-certificates: 2018.03.07-0
    certifi:         2018.10.15-py37_0
    libedit:         3.1.20170329-h6b74fdf_2
    libffi:          3.2.1-hd88cf55_4
    libgcc-ng:       8.2.0-hdf63c60_1
    libstdcxx-ng:    8.2.0-hdf63c60_1
    ncurses:         6.1-he6710b0_1
    openssl:         1.1.1a-h7b6447c_0
    pip:             18.1-py37_0
    python:          3.7.1-h0371630_3
    pyyaml:          3.13-py37h14c3975_0
    readline:        7.0-h7b6447c_5
    setuptools:      40.6.2-py37_0
    sqlite:          3.25.3-h7b6447c_0
    tk:              8.6.8-hbc83047_0
    wheel:           0.32.3-py37_0
    xz:              5.2.4-h14c3975_4
    yaml:            0.1.7-had09818_2
    zlib:            1.2.11-h7b6447c_3

Preparing transaction: ...working... done
Verifying transaction: ...working... done
Executing transaction: ...working... done
Applying patch: '/tmp/tmpj830mzklconda_skeleton_pyftpdlib-1.5.4.tar.gz/pypi-distutils.patch'
Trying to apply patch as-is
INFO:conda_build.source:Trying to apply patch as-is
patching file core.py
Hunk #1 succeeded at 167 with fuzz 2 (offset 1 line).

'pyopenssl' third-party module is not installed. This means
FTPS support will be disabled. You can install it with:
'pip install pyopenssl'.
Writing recipe for pyftpdlib
--dirty flag and --keep-old-work not specified. Removing build/test folder after successful build/test.

INFO:conda_build.config:--dirty flag and --keep-old-work not specified. Removing build/test folder after successful build/test.

```

**NOTE** You may want to modify the contents of the `pyftpdlib/meta.yaml` file at this point.

## Building packages

Now we can build a package (NOTE: This can also be run from the root package directory to build own of our existing recipes).

```shell
$ ~/miniconda3/bin/conda build pyftpdlib
No numpy version specified in conda_build_config.yaml.  Falling back to default numpy value of 1.11
WARNING:conda_build.metadata:No numpy version specified in conda_build_config.yaml.  Falling back to default numpy value of 1.11
Adding in variants from internal_defaults
INFO:conda_build.variants:Adding in variants from internal_defaults
Attempting to finalize metadata for pyftpdlib
INFO:conda_build.metadata:Attempting to finalize metadata for pyftpdlib
Solving environment: ...working... done
Solving environment: ...working... done
BUILD START: ['pyftpdlib-1.5.4-py37_0.tar.bz2']
Solving environment: ...working... done

## Package Plan ##

  environment location: /root/miniconda3/conda-bld/pyftpdlib_1543880907335/_h_env_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placeho


The following NEW packages will be INSTALLED:

    ca-certificates: 2018.03.07-0
    certifi:         2018.10.15-py37_0
    libedit:         3.1.20170329-h6b74fdf_2
    libffi:          3.2.1-hd88cf55_4
    libgcc-ng:       8.2.0-hdf63c60_1
    libstdcxx-ng:    8.2.0-hdf63c60_1
    ncurses:         6.1-he6710b0_1
    openssl:         1.1.1a-h7b6447c_0
    pip:             18.1-py37_0
    python:          3.7.1-h0371630_3
    readline:        7.0-h7b6447c_5
    setuptools:      40.6.2-py37_0
    sqlite:          3.25.3-h7b6447c_0
    tk:              8.6.8-hbc83047_0
    wheel:           0.32.3-py37_0
    xz:              5.2.4-h14c3975_4
    zlib:            1.2.11-h7b6447c_3

Preparing transaction: ...working... done
Verifying transaction: ...working... done
Executing transaction: ...working... done
Solving environment: ...working... done
Source cache directory is: /root/miniconda3/conda-bld/src_cache
Found source in cache: pyftpdlib-1.5.4_e5fca61397.tar.gz
Extracting download
source tree in: /root/miniconda3/conda-bld/pyftpdlib_1543880907335/work
export PREFIX=/root/miniconda3/conda-bld/pyftpdlib_1543880907335/_h_env_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placeho
export BUILD_PREFIX=/root/miniconda3/conda-bld/pyftpdlib_1543880907335/_build_env
export SRC_DIR=/root/miniconda3/conda-bld/pyftpdlib_1543880907335/work
Ignoring indexes: https://pypi.org/simple
Created temporary directory: /tmp/pip-ephem-wheel-cache-0qpa7d4k
Created temporary directory: /tmp/pip-req-tracker-zydpgno6
Created requirements tracker '/tmp/pip-req-tracker-zydpgno6'
Created temporary directory: /tmp/pip-install-dtf0sycg
Processing $SRC_DIR
  Created temporary directory: /tmp/pip-req-build-mwfqlm0g
  Added file://$SRC_DIR to build tracker '/tmp/pip-req-tracker-zydpgno6'
  Running setup.py (path:/tmp/pip-req-build-mwfqlm0g/setup.py) egg_info for package from file://$SRC_DIR
    Running command python setup.py egg_info
    running egg_info
    creating pip-egg-info/pyftpdlib.egg-info
    writing pip-egg-info/pyftpdlib.egg-info/PKG-INFO
    writing dependency_links to pip-egg-info/pyftpdlib.egg-info/dependency_links.txt
    writing requirements to pip-egg-info/pyftpdlib.egg-info/requires.txt
    writing top-level names to pip-egg-info/pyftpdlib.egg-info/top_level.txt
    writing manifest file 'pip-egg-info/pyftpdlib.egg-info/SOURCES.txt'
    reading manifest file 'pip-egg-info/pyftpdlib.egg-info/SOURCES.txt'
    reading manifest template 'MANIFEST.in'
    writing manifest file 'pip-egg-info/pyftpdlib.egg-info/SOURCES.txt'

    'pyopenssl' third-party module is not installed. This means
    FTPS support will be disabled. You can install it with:
    'pip install pyopenssl'.
  Source in /tmp/pip-req-build-mwfqlm0g has version 1.5.4, which satisfies requirement pyftpdlib==1.5.4 from file://$SRC_DIR
  Removed pyftpdlib==1.5.4 from file://$SRC_DIR from build tracker '/tmp/pip-req-tracker-zydpgno6'
Could not parse version from link: file://$SRC_DIR
Building wheels for collected packages: pyftpdlib
  Created temporary directory: /tmp/pip-wheel-mus42elj
  Running setup.py bdist_wheel for pyftpdlib: started
  Destination directory: /tmp/pip-wheel-mus42elj
  Running command $PREFIX/bin/python -u -c "import setuptools, tokenize;__file__='/tmp/pip-req-build-mwfqlm0g/setup.py';f=getattr(tokenize, 'open', open)(__file__);code=f.read().replace('\r\n', '\n');f.close();exec(compile(code, __file__, 'exec'))" bdist_wheel -d /tmp/pip-wheel-mus42elj --python-tag cp37
  running bdist_wheel
  running build
  running build_py
  creating build
  creating build/lib
  creating build/lib/pyftpdlib
  copying pyftpdlib/__main__.py -> build/lib/pyftpdlib
  copying pyftpdlib/_compat.py -> build/lib/pyftpdlib
  copying pyftpdlib/log.py -> build/lib/pyftpdlib
  copying pyftpdlib/__init__.py -> build/lib/pyftpdlib
  copying pyftpdlib/ioloop.py -> build/lib/pyftpdlib
  copying pyftpdlib/authorizers.py -> build/lib/pyftpdlib
  copying pyftpdlib/servers.py -> build/lib/pyftpdlib
  copying pyftpdlib/handlers.py -> build/lib/pyftpdlib
  copying pyftpdlib/filesystems.py -> build/lib/pyftpdlib
  creating build/lib/pyftpdlib/test
  copying pyftpdlib/test/__main__.py -> build/lib/pyftpdlib/test
  copying pyftpdlib/test/test_functional_ssl.py -> build/lib/pyftpdlib/test
  copying pyftpdlib/test/test_filesystems.py -> build/lib/pyftpdlib/test
  copying pyftpdlib/test/test_servers.py -> build/lib/pyftpdlib/test
  copying pyftpdlib/test/test_ioloop.py -> build/lib/pyftpdlib/test
  copying pyftpdlib/test/test_functional.py -> build/lib/pyftpdlib/test
  copying pyftpdlib/test/test_misc.py -> build/lib/pyftpdlib/test
  copying pyftpdlib/test/__init__.py -> build/lib/pyftpdlib/test
  copying pyftpdlib/test/test_authorizers.py -> build/lib/pyftpdlib/test
  copying pyftpdlib/test/runner.py -> build/lib/pyftpdlib/test
  copying pyftpdlib/test/README -> build/lib/pyftpdlib/test
  copying pyftpdlib/test/keycert.pem -> build/lib/pyftpdlib/test
  running build_scripts
  creating build/scripts-3.7
  copying and adjusting scripts/ftpbench -> build/scripts-3.7
  changing mode of build/scripts-3.7/ftpbench from 644 to 755
  installing to build/bdist.linux-x86_64/wheel
  running install
  running install_lib
  creating build/bdist.linux-x86_64
  creating build/bdist.linux-x86_64/wheel
  creating build/bdist.linux-x86_64/wheel/pyftpdlib
  copying build/lib/pyftpdlib/__main__.py -> build/bdist.linux-x86_64/wheel/pyftpdlib
  creating build/bdist.linux-x86_64/wheel/pyftpdlib/test
  copying build/lib/pyftpdlib/test/__main__.py -> build/bdist.linux-x86_64/wheel/pyftpdlib/test
  copying build/lib/pyftpdlib/test/test_functional_ssl.py -> build/bdist.linux-x86_64/wheel/pyftpdlib/test
  copying build/lib/pyftpdlib/test/test_filesystems.py -> build/bdist.linux-x86_64/wheel/pyftpdlib/test
  copying build/lib/pyftpdlib/test/test_servers.py -> build/bdist.linux-x86_64/wheel/pyftpdlib/test
  copying build/lib/pyftpdlib/test/test_ioloop.py -> build/bdist.linux-x86_64/wheel/pyftpdlib/test
  copying build/lib/pyftpdlib/test/test_functional.py -> build/bdist.linux-x86_64/wheel/pyftpdlib/test
  copying build/lib/pyftpdlib/test/test_misc.py -> build/bdist.linux-x86_64/wheel/pyftpdlib/test
  copying build/lib/pyftpdlib/test/__init__.py -> build/bdist.linux-x86_64/wheel/pyftpdlib/test
  copying build/lib/pyftpdlib/test/test_authorizers.py -> build/bdist.linux-x86_64/wheel/pyftpdlib/test
  copying build/lib/pyftpdlib/test/runner.py -> build/bdist.linux-x86_64/wheel/pyftpdlib/test
  copying build/lib/pyftpdlib/test/README -> build/bdist.linux-x86_64/wheel/pyftpdlib/test
  copying build/lib/pyftpdlib/test/keycert.pem -> build/bdist.linux-x86_64/wheel/pyftpdlib/test
  copying build/lib/pyftpdlib/_compat.py -> build/bdist.linux-x86_64/wheel/pyftpdlib
  copying build/lib/pyftpdlib/log.py -> build/bdist.linux-x86_64/wheel/pyftpdlib
  copying build/lib/pyftpdlib/__init__.py -> build/bdist.linux-x86_64/wheel/pyftpdlib
  copying build/lib/pyftpdlib/ioloop.py -> build/bdist.linux-x86_64/wheel/pyftpdlib
  copying build/lib/pyftpdlib/authorizers.py -> build/bdist.linux-x86_64/wheel/pyftpdlib
  copying build/lib/pyftpdlib/servers.py -> build/bdist.linux-x86_64/wheel/pyftpdlib
  copying build/lib/pyftpdlib/handlers.py -> build/bdist.linux-x86_64/wheel/pyftpdlib
  copying build/lib/pyftpdlib/filesystems.py -> build/bdist.linux-x86_64/wheel/pyftpdlib
  running install_egg_info
  running egg_info
  writing pyftpdlib.egg-info/PKG-INFO
  writing dependency_links to pyftpdlib.egg-info/dependency_links.txt
  writing requirements to pyftpdlib.egg-info/requires.txt
  writing top-level names to pyftpdlib.egg-info/top_level.txt
  reading manifest file 'pyftpdlib.egg-info/SOURCES.txt'
  reading manifest template 'MANIFEST.in'
  writing manifest file 'pyftpdlib.egg-info/SOURCES.txt'
  Copying pyftpdlib.egg-info to build/bdist.linux-x86_64/wheel/pyftpdlib-1.5.4-py3.7.egg-info
  running install_scripts
  creating build/bdist.linux-x86_64/wheel/pyftpdlib-1.5.4.data
  creating build/bdist.linux-x86_64/wheel/pyftpdlib-1.5.4.data/scripts
  copying build/scripts-3.7/ftpbench -> build/bdist.linux-x86_64/wheel/pyftpdlib-1.5.4.data/scripts
  changing mode of build/bdist.linux-x86_64/wheel/pyftpdlib-1.5.4.data/scripts/ftpbench to 755
  adding license file "LICENSE" (matched pattern "LICEN[CS]E*")
  creating build/bdist.linux-x86_64/wheel/pyftpdlib-1.5.4.dist-info/WHEEL
  creating '/tmp/pip-wheel-mus42elj/pyftpdlib-1.5.4-cp37-none-any.whl' and adding 'build/bdist.linux-x86_64/wheel' to it
  adding 'pyftpdlib/__init__.py'
  adding 'pyftpdlib/__main__.py'
  adding 'pyftpdlib/_compat.py'
  adding 'pyftpdlib/authorizers.py'
  adding 'pyftpdlib/filesystems.py'
  adding 'pyftpdlib/handlers.py'
  adding 'pyftpdlib/ioloop.py'
  adding 'pyftpdlib/log.py'
  adding 'pyftpdlib/servers.py'
  adding 'pyftpdlib/test/README'
  adding 'pyftpdlib/test/__init__.py'
  adding 'pyftpdlib/test/__main__.py'
  adding 'pyftpdlib/test/keycert.pem'
  adding 'pyftpdlib/test/runner.py'
  adding 'pyftpdlib/test/test_authorizers.py'
  adding 'pyftpdlib/test/test_filesystems.py'
  adding 'pyftpdlib/test/test_functional.py'
  adding 'pyftpdlib/test/test_functional_ssl.py'
  adding 'pyftpdlib/test/test_ioloop.py'
  adding 'pyftpdlib/test/test_misc.py'
  adding 'pyftpdlib/test/test_servers.py'
  adding 'pyftpdlib-1.5.4.data/scripts/ftpbench'
  adding 'pyftpdlib-1.5.4.dist-info/LICENSE'
  adding 'pyftpdlib-1.5.4.dist-info/METADATA'
  adding 'pyftpdlib-1.5.4.dist-info/WHEEL'
  adding 'pyftpdlib-1.5.4.dist-info/top_level.txt'
  adding 'pyftpdlib-1.5.4.dist-info/RECORD'
  removing build/bdist.linux-x86_64/wheel

  'pyopenssl' third-party module is not installed. This means
  FTPS support will be disabled. You can install it with:
  'pip install pyopenssl'.
  Running setup.py bdist_wheel for pyftpdlib: finished with status 'done'
  Stored in directory: /tmp/pip-ephem-wheel-cache-0qpa7d4k/wheels/0d/c4/29/ea54b990a85971b81a41fb6a563bd5d98c9c16a9ed5fb333e6
  Removing source in /tmp/pip-req-build-mwfqlm0g
Successfully built pyftpdlib
Installing collected packages: pyftpdlib

Successfully installed pyftpdlib-1.5.4
Cleaning up...
Removed build tracker '/tmp/pip-req-tracker-zydpgno6'

Resource usage statistics from building pyftpdlib:
   Process count: 1
   CPU time: unavailable
   Memory: 376.0K
   Disk usage: 988B
   Time elapsed: 0:00:02.0

Packaging pyftpdlib
INFO:conda_build.build:Packaging pyftpdlib
Packaging pyftpdlib-1.5.4-py37_0
INFO:conda_build.build:Packaging pyftpdlib-1.5.4-py37_0
compiling .pyc files...
number of files: 47
nm: dynamic_annotations.o: no symbols
Fixing permissions
Detected hard-coded path in text file bin/ftpbench
Compressing to /tmp/tmpi0nbj4v2/pyftpdlib-1.5.4-py37_0.tar.bz2
Importing conda-verify failed.  Please be sure to test your packages.  conda install conda-verify to make this message go away.
WARNING:conda_build.build:Importing conda-verify failed.  Please be sure to test your packages.  conda install conda-verify to make this message go away.
TEST START: /root/miniconda3/conda-bld/linux-64/pyftpdlib-1.5.4-py37_0.tar.bz2
Adding in variants from /tmp/tmpws7mxszr/info/recipe/conda_build_config.yaml
INFO:conda_build.variants:Adding in variants from /tmp/tmpws7mxszr/info/recipe/conda_build_config.yaml
Renaming work directory,  /root/miniconda3/conda-bld/pyftpdlib_1543880907335/work  to  /root/miniconda3/conda-bld/pyftpdlib_1543880907335/work_moved_pyftpdlib-1.5.4-py37_0_linux-64
Solving environment: ...working... done

## Package Plan ##

  environment location: /root/miniconda3/conda-bld/pyftpdlib_1543880907335/_test_env_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_plac


The following NEW packages will be INSTALLED:

    ca-certificates: 2018.03.07-0
    certifi:         2018.10.15-py37_0
    libedit:         3.1.20170329-h6b74fdf_2
    libffi:          3.2.1-hd88cf55_4
    libgcc-ng:       8.2.0-hdf63c60_1
    libstdcxx-ng:    8.2.0-hdf63c60_1
    ncurses:         6.1-he6710b0_1
    openssl:         1.1.1a-h7b6447c_0
    pip:             18.1-py37_0
    pyftpdlib:       1.5.4-py37_0            local
    python:          3.7.1-h0371630_3
    readline:        7.0-h7b6447c_5
    setuptools:      40.6.2-py37_0
    sqlite:          3.25.3-h7b6447c_0
    tk:              8.6.8-hbc83047_0
    wheel:           0.32.3-py37_0
    xz:              5.2.4-h14c3975_4
    zlib:            1.2.11-h7b6447c_3

Preparing transaction: ...working... done
Verifying transaction: ...working... done
Executing transaction: ...working... done
export PREFIX=/root/miniconda3/conda-bld/pyftpdlib_1543880907335/_test_env_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_plac
export SRC_DIR=/root/miniconda3/conda-bld/pyftpdlib_1543880907335/test_tmp
import: 'pyftpdlib'
import: 'pyftpdlib'

Resource usage statistics from testing pyftpdlib:
   Process count: 1
   CPU time: unavailable
   Memory: 1.1M
   Disk usage: 16B
   Time elapsed: 0:00:02.0

TEST END: /root/miniconda3/conda-bld/linux-64/pyftpdlib-1.5.4-py37_0.tar.bz2
Renaming work directory,  /root/miniconda3/conda-bld/pyftpdlib_1543880907335/work  to  /root/miniconda3/conda-bld/pyftpdlib_1543880907335/work_moved_pyftpdlib-1.5.4-py37_0_linux-64_main_build_loop
# Automatic uploading is disabled
# If you want to upload package(s) to anaconda.org later, type:

anaconda upload /root/miniconda3/conda-bld/linux-64/pyftpdlib-1.5.4-py37_0.tar.bz2

# To have conda build upload to anaconda.org automatically, use
# $ conda config --set anaconda_upload yes

anaconda_upload is not set.  Not uploading wheels: []
####################################################################################
Resource usage summary:

Total time: 0:00:20.9
CPU usage: sys=0:00:00.0, user=0:00:00.0
Maximum memory usage observed: 1.1M
Total disk usage observed (not including envs): 1004B


####################################################################################
Source and build intermediates have been left in /root/miniconda3/conda-bld.
There are currently 4 accumulated.
To remove them, you can run the ```conda build purge``` command
```

**NOTE** You'll want to repeat this command for the other python versions we want to support.
In this case we want to support python 2.7, 3.6 and 3.7, so we'll run:
```shell
$ ~/miniconda3/bin/conda build --python 3.6 pyftpdlib
...
$ ~/miniconda3/bin/conda build --python 2.7 pyftpdlib
...
```

Now we'll want to support multiple operating systems (particularly `linux-64` and `osx-64`).
```shell
$ cd ~/miniconda3/conda-bld/
```
```shell
~/miniconda3/conda-bld$ ~/miniconda3/bin/conda convert linux-64/pyftpdlib-1.5.4-py37_0.tar.bz2 -p all
Converting pyftpdlib-1.5.4-py37_0.tar.bz2 from linux-64 to osx-64
Converting pyftpdlib-1.5.4-py37_0.tar.bz2 from linux-64 to linux-32
Source platform 'linux-64' and target platform 'linux-64' are identical. Skipping conversion.
Converting pyftpdlib-1.5.4-py37_0.tar.bz2 from linux-64 to linux-ppc64le
Converting pyftpdlib-1.5.4-py37_0.tar.bz2 from linux-64 to linux-armv6l
Converting pyftpdlib-1.5.4-py37_0.tar.bz2 from linux-64 to linux-armv7l
Converting pyftpdlib-1.5.4-py37_0.tar.bz2 from linux-64 to linux-aarch64
Converting pyftpdlib-1.5.4-py37_0.tar.bz2 from linux-64 to win-32
Converting pyftpdlib-1.5.4-py37_0.tar.bz2 from linux-64 to win-64
```

Now we'll repeat that for the other python version.
```shell
~/miniconda3/conda-bld$ ~/miniconda3/bin/conda convert linux-64/pyftpdlib-1.5.4-py36_0.tar.bz2 -p all
...
~/miniconda3/conda-bld$ ~/miniconda3/bin/conda convert linux-64/pyftpdlib-1.5.4-py27_0.tar.bz2 -p all
...
```

## Uploading builds to our [anaconda channel](https://anaconda.org/Invenia)

Now we can use a glob pattern to upload all of our builds to anaconda.
NOTE: You'll be prompted for your username and password.
```shell

~/miniconda3/conda-bld$ ~/miniconda3/bin/anaconda upload --user=Invenia --skip ./*/pyftpdlib-1.5.4-py*_0.tar.bz2
Using Anaconda API: https://api.anaconda.org
Using "Invenia" as upload username
Processing './linux-32/pyftpdlib-1.5.4-py27_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-32/pyftpdlib-1.5.4-py27_0.tar.bz2"
The action you are performing requires authentication, please sign in:
Using Anaconda API: https://api.anaconda.org
Username: rofinn
rofinn's Password:
login successful
Using Anaconda API: https://api.anaconda.org
Using "Invenia" as upload username
Processing './linux-32/pyftpdlib-1.5.4-py27_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-32/pyftpdlib-1.5.4-py27_0.tar.bz2"
Distribution already exists. Skipping upload.

Processing './linux-32/pyftpdlib-1.5.4-py36_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-32/pyftpdlib-1.5.4-py36_0.tar.bz2"
Distribution already exists. Skipping upload.

Processing './linux-32/pyftpdlib-1.5.4-py37_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-32/pyftpdlib-1.5.4-py37_0.tar.bz2"
Distribution already exists. Skipping upload.

Processing './linux-64/pyftpdlib-1.5.4-py27_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-64/pyftpdlib-1.5.4-py27_0.tar.bz2"
Distribution already exists. Skipping upload.

Processing './linux-64/pyftpdlib-1.5.4-py36_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-64/pyftpdlib-1.5.4-py36_0.tar.bz2"
Distribution already exists. Skipping upload.

Processing './linux-64/pyftpdlib-1.5.4-py37_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-64/pyftpdlib-1.5.4-py37_0.tar.bz2"
Distribution already exists. Skipping upload.

Processing './linux-aarch64/pyftpdlib-1.5.4-py27_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-aarch64/pyftpdlib-1.5.4-py27_0.tar.bz2"
 uploaded 180 of 180Kb: 100.00% ETA: 0.0 minutes
Upload complete

Processing './linux-aarch64/pyftpdlib-1.5.4-py36_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-aarch64/pyftpdlib-1.5.4-py36_0.tar.bz2"
 uploaded 183 of 183Kb: 100.00% ETA: 0.0 minutes
Upload complete

Processing './linux-aarch64/pyftpdlib-1.5.4-py37_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-aarch64/pyftpdlib-1.5.4-py37_0.tar.bz2"
 uploaded 183 of 183Kb: 100.00% ETA: 0.0 minutes
Upload complete

Processing './linux-armv6l/pyftpdlib-1.5.4-py27_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-armv6l/pyftpdlib-1.5.4-py27_0.tar.bz2"
 uploaded 179 of 179Kb: 100.00% ETA: 0.0 minutes
Upload complete

Processing './linux-armv6l/pyftpdlib-1.5.4-py36_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-armv6l/pyftpdlib-1.5.4-py36_0.tar.bz2"
 uploaded 183 of 183Kb: 100.00% ETA: 0.0 minutes
Upload complete

Processing './linux-armv6l/pyftpdlib-1.5.4-py37_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-armv6l/pyftpdlib-1.5.4-py37_0.tar.bz2"
 uploaded 183 of 183Kb: 100.00% ETA: 0.0 minutes
Upload complete

Processing './linux-armv7l/pyftpdlib-1.5.4-py27_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-armv7l/pyftpdlib-1.5.4-py27_0.tar.bz2"
 uploaded 179 of 179Kb: 100.00% ETA: 0.0 minutes
Upload complete

Processing './linux-armv7l/pyftpdlib-1.5.4-py36_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-armv7l/pyftpdlib-1.5.4-py36_0.tar.bz2"
 uploaded 183 of 183Kb: 100.00% ETA: 0.0 minutes
Upload complete

Processing './linux-armv7l/pyftpdlib-1.5.4-py37_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-armv7l/pyftpdlib-1.5.4-py37_0.tar.bz2"
 uploaded 183 of 183Kb: 100.00% ETA: 0.0 minutes
Upload complete

Processing './linux-ppc64le/pyftpdlib-1.5.4-py27_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-ppc64le/pyftpdlib-1.5.4-py27_0.tar.bz2"
 uploaded 180 of 180Kb: 100.00% ETA: 0.0 minutes
Upload complete

Processing './linux-ppc64le/pyftpdlib-1.5.4-py36_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-ppc64le/pyftpdlib-1.5.4-py36_0.tar.bz2"
 uploaded 183 of 183Kb: 100.00% ETA: 0.0 minutes
Upload complete

Processing './linux-ppc64le/pyftpdlib-1.5.4-py37_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/linux-ppc64le/pyftpdlib-1.5.4-py37_0.tar.bz2"
 uploaded 183 of 183Kb: 100.00% ETA: 0.0 minutes
Upload complete

Processing './osx-64/pyftpdlib-1.5.4-py27_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/osx-64/pyftpdlib-1.5.4-py27_0.tar.bz2"
Distribution already exists. Skipping upload.

Processing './osx-64/pyftpdlib-1.5.4-py36_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/osx-64/pyftpdlib-1.5.4-py36_0.tar.bz2"
Distribution already exists. Skipping upload.

Processing './osx-64/pyftpdlib-1.5.4-py37_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/osx-64/pyftpdlib-1.5.4-py37_0.tar.bz2"
Distribution already exists. Skipping upload.

Processing './win-32/pyftpdlib-1.5.4-py27_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/win-32/pyftpdlib-1.5.4-py27_0.tar.bz2"
Distribution already exists. Skipping upload.

Processing './win-32/pyftpdlib-1.5.4-py36_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/win-32/pyftpdlib-1.5.4-py36_0.tar.bz2"
Distribution already exists. Skipping upload.

Processing './win-32/pyftpdlib-1.5.4-py37_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/win-32/pyftpdlib-1.5.4-py37_0.tar.bz2"
Distribution already exists. Skipping upload.

Processing './win-64/pyftpdlib-1.5.4-py27_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/win-64/pyftpdlib-1.5.4-py27_0.tar.bz2"
Distribution already exists. Skipping upload.

Processing './win-64/pyftpdlib-1.5.4-py36_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/win-64/pyftpdlib-1.5.4-py36_0.tar.bz2"
Distribution already exists. Skipping upload.

Processing './win-64/pyftpdlib-1.5.4-py37_0.tar.bz2'
Detecting file type...
File type is "conda"
Extracting conda package attributes for upload
Creating package "pyftpdlib"
Creating release "1.5.4"
Uploading file "Invenia/pyftpdlib/1.5.4/win-64/pyftpdlib-1.5.4-py37_0.tar.bz2"
Distribution already exists. Skipping upload.

conda package located at:
https://anaconda.org/invenia/pyftpdlib

conda package located at:
https://anaconda.org/invenia/pyftpdlib

conda package located at:
https://anaconda.org/invenia/pyftpdlib

conda package located at:
https://anaconda.org/invenia/pyftpdlib

conda package located at:
https://anaconda.org/invenia/pyftpdlib

conda package located at:
https://anaconda.org/invenia/pyftpdlib

conda package located at:
https://anaconda.org/invenia/pyftpdlib

conda package located at:
https://anaconda.org/invenia/pyftpdlib

conda package located at:
https://anaconda.org/invenia/pyftpdlib

conda package located at:
https://anaconda.org/invenia/pyftpdlib

conda package located at:
https://anaconda.org/invenia/pyftpdlib

conda package located at:
https://anaconda.org/invenia/pyftpdlib
```
