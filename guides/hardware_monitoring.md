[![PyPI - Python Version](https://badge.fury.io/py/labml.svg)](https://badge.fury.io/py/labml)
[![Join Slack](https://img.shields.io/badge/slack-chat-green.svg?logo=slack)](https://join.slack.com/t/labforml/shared_invite/zt-egj9zvq9-Dl3hhZqobexgT7aVKnD14g/)
[![Twitter](https://img.shields.io/twitter/follow/labmlai?style=social)](https://twitter.com/labmlai?ref_src=twsrc%5Etfw)

# Hardware monitoring

<div align="center">
<img src="https://github.com/lab-ml/lab/blob/master/guides/hardware.png" width="30%" alt=""/>
</div>

We just added support to monitor hardware to our mobile-friendly web app
for monitoring deep learning model training.
You can use it to monitor hardware usage even if you are not training models.

### Installation

You need to install our python package and some dependencies to start monitoring.

```sh
pip install labml
```

`psutil` is the package we use to track hardware (`labml` doesn't install it as a dependency).

```sh
pip install psutil
```

 To monitor GPUs (nvidia) you need to install `py3nvml` package as well.

```sh
pip install py3nvml
```

 You can install all of the above packages in a single command

```sh
pip install labml psutil py3nvml
```

If you have problems with your Python environment you can use
[our guide to setting up Python with conda locally](https://github.com/lab-ml/remote/blob/master/notes/local-ubuntu.md),
or [on a remote computer](https://github.com/lab-ml/remote/blob/master/notes/remote-python.md).

### Start monitoring

Once it's installed you can just run the following command to start monitoring.
You will get a url to view the hardware usage.

```sh
labml monitor
```

You can also run it with `nohup` if you want it to run in the background on a remote computer.

```sh
nohup labml monitor &
```

### Obtaining a token

This step is not necessary but useful if you are monitoring from time to time.
By default when you run `labml monitor` it will give a URL to view the hardware usage.
It can be annoying to get this url from the logs especially if you are running `labml monitor` on a remote computer.

In such cases you can obtain a token from
[app.labml.ai](https://app.labml.ai) (Hamburger menu -> [Settings](https://app.labml.ai/settings)).
You can then add this to `.labml/configs.yaml` in your home directory.

```yaml
web_api: TOKEN_STRING
```

### Hosting your own server

`labml monitor` will start a process that monitors the hardware usage every few seconds
and send the usage information to [app.labml.ai](https://app.labml.ai) by default.
You can also host an instance of our app, by cloning the [Github repository](https://github.com/lab-ml/app).

You can set the url of the server in  `.labml/configs.yaml`.

```yaml
web_api: https://hosted-labml-app.com
```

*Join our [Slack](https://join.slack.com/t/labforml/shared_invite/zt-egj9zvq9-Dl3hhZqobexgT7aVKnD14g/)
to discuss, and open an [issue on Github](https://github.com/lab-ml/labml/issues) if something breaks.*
