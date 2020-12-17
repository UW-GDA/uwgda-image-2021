# UWGDA2021 JupyterHub Image Builder

This repository builds a [JupyterHub](https://jupyter.org/hub) environment with JupyterHub [GitHub Actions CI](https://github.com/jupyterhub/repo2docker-action)

[![Action Status](https://github.com/UW-GDA/uwgda-image-2021/workflows/CI/badge.svg)](https://github.com/UW-GDA/uwgda-image-2021/actions)
[![Docker Pulls](https://img.shields.io/docker/pulls/uwgda/uwgda-image-2021)](https://hub.docker.com/r/uwgda/uwgda-image-2021/tags)
[![BinderHub](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/UW-GDA/uwgda-image-2021/main?urlpath=git-pull?repo=https://github.com/UW-GDA/gda_course_2020%26amp%3Bbranch=master%26amp%3Burlpath=lab)  

https://hub.docker.com/r/uwgda/uwgda-image-2021/tags

### How to use:

build with GitHub Actions simply by pushing to GitHub

* pull requests trigger image building without pushing to DockerHub
```
git clone https://github.com/UW-GDA/uwgda-image-2021
cd uwgda-image
git checkout dev
# make sure dev branch is up-to-date with master
git merge master
# modify environment.yml or other files in binder/
git commit -a -m "modified binder/environment to my liking"
git push
# go to github.com and create a pull request to merge dev changes into master
```
* PRs trigger re-building image
* Commits to master build image and push to DockerHub tagged by github commit sha and 'latest'

### Pull your image to run a local JupyterLab session
```
docker pull uwgda/uwgda-image-2021:latest
docker run -it --name UWGDA -p 8888:8888 $IMAGE:$TAG jupyter lab --ip 0.0.0.0
docker stop UWGDA
docker rm UWGDA
```

### Point to a specific tagged image in JupyterHub config
(image: uwgda/uwgda-image:abhjdh)
https://zero-to-jupyterhub.readthedocs.io/en/latest/reference/reference.html?highlight=profile_list#singleuser-profilelist
