ubuntu-systemd-playground
=========================
Not working yet

### Steps
- Start [the Github Action](https://github.com/dirkarnez/ubuntu-systemd-playground/actions/workflows/build-from-docker-compose.yml)
- Go to https://tmate.io/xxx web SSH with url printed in terminal
- `docker compose up --build --detach`
- `docker attach ubuntu-systemd-playground-my-systemd-playground-1`
- `docker exec ubuntu-systemd-playground-my-systemd-playground-1 systemctl start apache2.service`

### Notes
- `sudo chmod -R +x . && ./build.sh` in CI/CD .yaml file is good enough for running docker build on GitHub Action
- It seems that docker environment conflicts with the systemd workflow (requires system restart? requires some root rights?)
- reference `--entrypoint=/usr/lib/systemd/systemd --mount type=bind,source=/sys/fs/cgroup,target=/sys/fs/cgroup --mount type=bind,source=/sys/fs/fuse,target=/sys/fs/fuse --mount type=tmpfs,destination=/tmp --mount type=tmpfs,destination=/run --mount type=tmpfs,destination=/run/lock ubuntu-systemd-playground`

#### Prebuilt docker images
- [eniocarboni/docker-ubuntu-systemd: Ubuntu LTS Docker container with systemd, useful for tests with ansible and molecule](https://github.com/eniocarboni/docker-ubuntu-systemd)
- [jrei/systemd-ubuntu - Docker Image | Docker Hub](https://hub.docker.com/r/jrei/systemd-ubuntu)
- [robertdebock/docker-ubuntu-systemd: Container to test Ansible roles in, including capabilities to use systemd facilities](https://github.com/robertdebock/docker-ubuntu-systemd)

### References
- [Docker systemd进程管理器 — Cloud Atlas beta 文档](https://cloud-atlas.readthedocs.io/zh-cn/latest/docker/init/docker_systemd.html)
- [使用 systemd 管理 Docker container](https://blog.davy.tw/posts/use-systemd-to-manage-docker-container/)
- [渡鴉之丘: 在 docker container 裡面執行 systemd 服務（測試環境用～）](https://ravenonhill.blogspot.com/2018/08/systemd-inside-docker-container.html)
- [修复 "System has not been booted with systemd as init system "的错误。 - A5互联 - 博客园](https://www.cnblogs.com/a5idc/p/13752839.html)
- [Ubuntu 报错：System has not been booted with systemd as init system (PID 1). Can‘t operate.-CSDN博客](https://blog.csdn.net/weixin_46389691/article/details/133523514)
- [[小抄] Docker 基本命令 | 想不起來而已](https://yingclin.github.io/2018/docker-basic.html)
- [Systemd 入门教程：命令篇 - 阮一峰的网络日志](https://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html)
