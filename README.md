# ansible-virtualenv

Use this to create a python virtualenv at the given directory, and install a
requirements from the given file.

```
  - role: EDITD.virtualenv
    virtualenv_path: /opt/envs/someapp
    virtualenv_requirements_file: /opt/someapp/requirements.pip
    virtualenv_user: vagrant
    virtualenv_group: vagrant
```

If you want to have system site packages, use

```
    virtualenv_site_packages: "--system-site-packages"
```

If you want to use python 3, use

```
    virtualenv_python_major_version: 3
```

If you want to specify the pip version, use

```
  virtualenv_pip_version: 8.1.2
```

If you want to specify virtualenv version, use

```
  virtualenv_version: "13.0.0"
```

Otherwise the latest virtualenv version will be installed if `virtualenv_version` is not defined.

If you want to pass in extra args to the `pip install` command, use

```
  virtualenv_extra_pip_args: "--process-dependency-links"
```

By default, this role will write a `pip.conf` file in the virtualenv that points to our private pypi index (pypi.edtd.net). If you want to skip this behaviour (for instance, to write your own custom pip.conf file), use

```
  virtualenv_write_pip_conf: false
```

The virtualenv will by deleted and recreated if the major python version is increasing from 2 to 3. If you want to force it to recreate for any other reason, then you can use

```
  virtualenv_recreate_venv: true
```