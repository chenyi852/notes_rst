docker
^^^^^^^^^^^^^^

容器配置文件
================

docker引擎的配置文件在 /etc/docker/daemon.json, 下面是一个案例 ::

	{
		"insecure-registries": [
			"ghcr.io",
			"quay.io",
			"registry-1.docker.io",
		  ],
		"registry-mirrors": [

			"https://docker.mirrors.ustc.edu.cn",

			"https://registry.docker-cn.com",

			"http://hub-mirror.c.163.com"

		],

		"data-root": "/data/docker",

		"log-opts": {

			"max-size": "50m",

			"max-file": "1"

		},

		"exec-opts": ["native.cgroupdriver=systemd"]

	}

通过上面的配置文件，可以指定docker daemon的文件都保存在/data/docker里。
