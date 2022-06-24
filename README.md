<p align="center">
 <img src="https://www.suse.com/c/wp-content/uploads/2020/10/rancher-logo-stacked-color-1024x520.png" alt="The Documentation Compendium"></a>
</p>

<h3 align="center">Rancher Quick Guide Installation</h3>


---

<p align = "center">💡 Arranged By : xxx from many sources</p>

Table of Contents
-----------------

  * [Step-1 Installing Docker](#step-1-installing-docker)
  * [Step-2 Installing Rancher](#step-2-installing-rancher)

Step-1 Installing Docker
----

:bulb:The Docker installation package available in the official Ubuntu repository may not be the latest version. To ensure we get the latest version, we’ll install Docker from the official Docker repository. To do that, we’ll add a new package source, add the GPG key from Docker to ensure the downloads are valid, and then install the package.

First, update your existing list of packages:

```bash
$ sudo apt update
```

Next, install a few prerequisite packages which let ``apt`` use packages over HTTPS:

```bash
$ sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

Then add the GPG key for the official Docker repository to your system:

```bash
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Add the Docker repository to APT sources:

```bash
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```

This will also update our package database with the Docker packages from the newly added repo.
Make sure you are about to install from the Docker repo instead of the default Ubuntu repo:

```bash
$ apt-cache policy docker-ce
```

Finally, install Docker:

```bash
$ sudo apt install docker-ce
```

Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it’s running:

```bash
$ sudo systemctl status docker
```

The output should be similar to the following, showing that the service is active and running:

```bash
Output
● docker.service - Docker Application Container Engine
     Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2020-05-19 17:00:41 UTC; 17s ago
TriggeredBy: ● docker.socket
       Docs: https://docs.docker.com
   Main PID: 24321 (dockerd)
      Tasks: 8
     Memory: 46.4M
     CGroup: /system.slice/docker.service
             └─24321 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock
```
Installing Docker now gives you not just the Docker service (daemon) but also the ```docker``` command line utility, or the Docker client.








Step-2 Installing Rancher
--------

Just a simple line of command to get your Rancher Server up and running~ 

```bash
$ sudo docker run --privileged -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher
```

To access the Rancher server UI, open a browser and go to the hostname or address where the container was installed. You will be guided through setting up your first cluster.

Draft V1
