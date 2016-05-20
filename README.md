# docker-phpvirtualbox

[phpVirtualBox](http://sourceforge.net/projects/phpvirtualbox/) is a modern web interface that allows
you to control remote VirtualBox instances - mirroring the VirtualBox GUI.
This is a [docker](https://www.docker.io) image that eases setup.

## About phpVirtualBox

> *From [the official description](http://sourceforge.net/projects/phpvirtualbox/):*

An open source, AJAX implementation of the VirtualBox user interface written in PHP.
As a modern web interface, it allows you to access and control remote VirtualBox instances.
phpVirtualBox is designed to allow users to administer VirtualBox in a headless
environment - mirroring the VirtualBox GUI through its web interface.

![](http://a.fsdn.com/con/app/proj/phpvirtualbox/screenshots/phpvb1.png)

## Getting Started
Start the Virtualbox Web Server. You will be prompted for a password.
Note: detach with `ctrl+p` then `ctrl+q`.

```bash
$ docker run -it --name=vboxwebsrv clue/vboxwebsrv vbox@10.1.1.2
```

Start phpVirtualbox.

```bash
$ docker run -d --name phpvirtualbox -p 80:80 -p 3392:3392 --link vboxwebsrv:gui sisuware/phpvirtualbox
```

Open a browser and navigate to http://localhost:80.

## Environment Variables
`version` phpVirtualbox version specification, currently defaults to 5.0-5
`port` 



This is a rather common setup following docker's conventions:

* `-d` will run a detached session running in the background
* `-p {OutsidePort}:80` will bind the webserver to the given outside port
* `--link {ContainerName}:{DisplayName}` links a `vboxwebsrv` instance with the given {ContainerName} and exposes it under the visual {DisplayName}
* `sisuware/phpvirtualbox` the name of this docker image
