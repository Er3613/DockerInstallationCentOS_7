Introduction...

Docker, accoding to docker documentation is a great standarized unit of software. In a computer ambiance to
another, it is a solid, trusthworthy, active, and agile way to run an application with all its dependecies and
code amalgamated.

Prerequisites.

There are several way to install docker in the variety of distros, so the following steps are for CentOS 7
in my case.

 + This Demo will be using CentOS 7 and Docker CE.
 + Remove old version
 + Enable the following repositories and packages.
   - epel-release.
   - yum-utils, device-mapper-persistent-data, lvm2
   - docker repo (There are two repos included inside docker repo: nightly and test.
   - Kernel 3.10 or higher.

Setting Up.

- Remove Old Version, if there is one installed.

  $ sudo yum remove docker docker-client docker-client-latest
  $ sudo yum remove docker-common docker-latest docker-latest-logrotate
  $ sudo yum remove docker-logrotate docker-engine

- Ensuring that we are using kernel 3.10 or higher.

  $ uname -r

- Install epel-release.

  $ sudo yum install -y epel-release

- Install required packages.

  $ sudo yum install -y yum-utils device-mapper-persistent-data lvm2

- Set up Docker stable repo and we will be using "ce" Community Edition.
  GPG key will be verify at this step.

  $ sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

- Install Docker ce.

  $ sudo yum install docker-ce docker-ce-cli containerd.io

- Docker has been installed but it has not been started.
  Note: A group has been created ( docker group ) but no users have been added to this group

  $ sudo systemctl start docker
  $ sudo systemctl enable docker

- Now, we can verify that Docker has been installed correctly, as a result; we will add our user to the Docker group.
  $ sudo docker run hello-world

  - Adding our user to the docker group.

    $ sudo usermod -aG docker [your-user]

    Note: For this to take effect, remember to log out and log back in.

- Conclusion.

  It is obvious that there are other ways to instaled Docker and Docker documentation is a the place to clarify
  any inqueries we might have. The purpose of this demo is to help you set up Docker in CentOS 7 and I hope this
  guide helps you find a new path to expand your posibilities.
