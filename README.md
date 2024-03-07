# Reproduction for https://github.com/tox-dev/tox/issues/3238

## With tox 4.14.0

```
pip install tox==4.14.0
rm -rf .tox
tox -e tests
```

Output:

```
build-package: commands[0]> pip wheel . --wheel-dir ~/tox-variables/.tox/build-package/tmp/dist
Processing ~/tox-variables
  Installing build dependencies ... done
  Getting requirements to build wheel ... done
  Preparing metadata (pyproject.toml) ... done
Building wheels for collected packages: tox_variables
  Building wheel for tox_variables (pyproject.toml) ... done
  Created wheel for tox_variables: filename=tox_variables-1.0.0-py3-none-any.whl size=1192 sha256=9850d8ac364efbd1a8e2715b6e223404cfa13a1495fa666a7c98ff989045c7cd
  Stored in directory: Caches/pip/wheels/6d/e5/0d/7d3f13d7e25030418b2c018c848ce55e2aa384e5dfac7e2412
Successfully built tox_variables
tests: install_package> python -I -m pip install --force-reinstall --no-deps ~/tox-variables/.tox/build-package/tmp/dist/tox_variables-1.0.0-py3-none-any.whl
tests: commands[0]> python -c 'import tox_variables'
hello!
  tests: OK (2.70=setup[2.69]+cmd[0.01] seconds)
  congratulations :) (2.73 seconds)
```

## With tox 4.14.1

```
pip install tox==4.14.1
rm -rf .tox
tox -e tests
```

Output:

```
build-package: commands[0]> pip wheel . --wheel-dir '{envtmpdir}/dist'
Processing ~/tox-variables
  Installing build dependencies ... done
  Getting requirements to build wheel ... done
  Preparing metadata (pyproject.toml) ... done
Building wheels for collected packages: tox_variables
  Building wheel for tox_variables (pyproject.toml) ... done
  Created wheel for tox_variables: filename=tox_variables-1.0.0-py3-none-any.whl size=1192 sha256=4e3598946e40cb92c7303c699abefe8f70fb9faabf841eaf13e829a0061e721c
  Stored in directory: Caches/pip/wheels/6d/e5/0d/7d3f13d7e25030418b2c018c848ce55e2aa384e5dfac7e2412
Successfully built tox_variables
tests: failed with no package found in ~/.tox/build-package/tmp/dist/*
  tests: FAIL code 1 (2.06 seconds)
  evaluation failed :( (2.09 seconds)
```
