# GLSO0215 Lab Template

Author: Seonghyeon Lee

This template is used for open-sourced programming course.

To do our lab, clone this repository first.

```
git clone https://github.com/sh0416/glso0215-template.git
cd glso0215-template
```

## Build docker image and run container

In our lab, we use docker and docker-compose to standardize our environment. So, you should install docker desktop in advance. You can install it from [here](https://www.docker.com/products/docker-desktop/).

After clone this repository, create an image with your personal information.

```
docker-compose build --build-arg USER=$USER --build-arg EMAIL=$EMAIL
```

Copy the one-time code displayed in the shell and visit the provided URL to link your GitHub account.

```
=> [app 7/8] RUN gh auth login --web --skip-ssh-key -s admin:public_key &&     gh ssh-key add ~/.ssh/id_rsa.pub
 => => # ! First copy your one-time code: AAAA-AAAA        
 => => # Open this URL to continue in your web browser: https://github.com/login/device
 ```

> **Warning**
> Do not upload this image to the internet. Your credential can be leaked.

Next, run docker container. (With `-d` option for running container background.)

```
docker-compose up -d
```

Next, open bash shell to enter the container.

```
docker exec -it glso0215-app-1 /bin/bash
```

## Git configuration

During the image build process, your personal information has been added into your image. You should check it by printing the git configuration setting.

```
git config list
```

**If the personal information is not properly added, you must ask the instructor to handle this issue.** Otherwise, you will get zero point.

```
user.name=${USER}
user.email=${EMAIL}
core.pager=
```

Check whether you can push your branch into `glso0215-lab` repository.

```
git clone git@github.com:sh0416/glso0215-lab.git
cd glso0215-lab
git checkout -b ${USER}/master
git push origin ${USER}/master
```

## Wrap up

After you finish the lab, stop and remove docker container.

```
$ docker-compose down
```

## TODO

- [x] Set up git config email and name automatically.
- [ ] Check cross-platform availability.
- [ ] Handle ssh key issue.

## Contact

If there is any issue, contact the instructor.

