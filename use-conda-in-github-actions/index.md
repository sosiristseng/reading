# Use Conda in GitHub Actions


The following example uses [setup miniconda](https://github.com/conda-incubator/setup-miniconda) GitHub action and the [mamba](https://github.com/mamba-org/mamba) package manager.

<!--more-->

The workflow file `.github/workflows/conda.yml` with the `jobs` section only.

- enable `mamba` by specifying `mamba-version: "*"`.
- `bash -l {0}` to activate conda environment correctly in CI.

```yml
jobs:
  example-6:
    name: Ex6 Mamba
    runs-on: "ubuntu-latest"
    steps:
      - uses: actions/checkout@v2
      - uses: conda-incubator/setup-miniconda@v2
        with:
          python-version: 3.6
          mamba-version: "*"
          channels: conda-forge,defaults
          channel-priority: true
          activate-environment: anaconda-client-env
          environment-file: etc/example-environment.yml
      - shell: bash -l {0}
        run: |
          conda info
          conda list
          conda config --show-sources
          conda config --show
          printenv | sort
      - shell: bash -l {0}
        run: mamba install jupyterlab
```

