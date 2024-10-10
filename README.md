# Linux-docker
# 利用虚拟机 Linux 系统安装 Docker 完成部署

## 虚拟机：Oracle VirtualBox/VMware 都可以

1. 看是否能通网络：`ping www.baidu.com`
2. 安装依赖包：`sudo yum install -y yum-utils`

    > 大概率会失败，要改国内镜像

    设置阿里云国内 CE 镜像：
    ```sh
    yum-config-manager --add-repo https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
    ```

    再次安装依赖包尝试：
    ```sh
    sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    ```

3. Docker CE 安装（CE 为社区版本不用收费）：
    ```sh
    yum install -y docker-ce
    ```

### Docker 一系列命令：

- 启动 Docker 命令：
  ```sh
  systemctl start docker
  ```

- 设置开机自启命令：
  ```sh
  systemctl enable docker
  ```

- 查看 Docker 版本命令：
  ```sh
  docker version
  ```

- 启动 Docker：
  ```sh
  sudo systemctl start docker
  sudo docker run hello-world
  ```

## Docker Compose 介绍

在软件开发和部署过程中，Docker Compose 具有重要的作用，Docker 的最新版本中就包含 Docker Compose。其优点主要包括以下几个方面：

### 1. 简化容器管理

在没有 Docker Compose 时，如果要管理多个容器，需要逐个手动启动和配置每个容器，这是一项繁琐且容易出错的任务。而 Docker Compose 允许你在一个配置文件中定义多个容器的配置信息，通过一个简单的命令就可以同时启动、停止和管理这些容器。这大大简化了容器的管理工作，提高了开发和运维效率。例如，一个由 Web 服务器、数据库和缓存组成的应用程序，使用 Docker Compose 可以轻松地将它们作为一个整体进行管理，而不必分别处理每个容器。

### 2. 可重复性和一致性

Docker Compose 确保了在不同环境中的可重复性和一致性。通过定义明确的配置文件，你可以在开发、测试和生产环境中使用相同的配置来启动容器。这有助于减少因环境差异而导致的问题，确保应用程序在不同阶段的行为一致。无论你是在本地开发还是在云端部署，都可以依赖相同的配置文件来启动应用程序的各个组件。

### 3. 快速部署和扩展

使用 Docker Compose，可以快速部署复杂的应用程序栈。只需一个命令，就可以启动整个应用程序所需的所有容器。此外，当需要扩展应用程序时，也可以轻松地通过修改配置文件来增加容器的数量或调整资源分配。例如，如果你的应用程序面临高负载，可以快速增加 Web 服务器容器的数量来提高性能。

### 4. 团队协作

对于团队开发来说，Docker Compose 提供了一种方便的方式来共享和协作。团队成员可以使用相同的配置文件来启动和管理应用程序的容器，确保每个人都在相同的环境中工作。这有助于减少因环境不一致而导致的问题，提高团队的协作效率。配置文件可以被版本控制，方便团队成员跟踪和管理应用程序的配置变化。

综上所述，Docker Compose 在容器化应用程序的管理中具有重要的地位，它简化了容器管理、提供了可重复性和一致性、支持快速部署和扩展，并促进了团队协作。