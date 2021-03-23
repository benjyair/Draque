# Draque
本项目是一个基本的 Android 项目，包含了 Drone 自动构建的脚本和对应的 Docker 镜像的源文件。

### 项目指引
* 1、基于 Ubuntu 的镜像
文件位置：`docker/Dockerfile`
镜像：`docker pull benjyair/android-env:latest`

* 2、基于 Gradle 的镜像
文件位置：`docker_gradle/Dockerfile`
镜像：`docker pull benjyair/android-env-gradle:latest`

* 3、基于 Drone 和 MinIO 的 CI 构建脚本
`.drone.yml`

### 使用指南
详细用法参见博客系列文章：
[基于 Drone 的 Android CI 环境 - 自动上传打包文件到 MinIO](http://www.benjyair.com/2021/03/23/%E3%80%8C%E7%BE%A4%E8%BE%89%E5%B7%A5%E4%BD%9C%E7%AB%99%E3%80%8D%E5%9F%BA%E4%BA%8E%20Drone%20%E7%9A%84%20Android%20CI%20%E7%8E%AF%E5%A2%83%20-%20%E8%87%AA%E5%8A%A8%E4%B8%8A%E4%BC%A0%E6%89%93%E5%8C%85%E6%96%87%E4%BB%B6%E5%88%B0%20MinIO/)
[基于 Drone 的 Android CI 环境 - 准备 Android 编译镜像](http://www.benjyair.com/2021/03/18/%E3%80%8C%E7%BE%A4%E8%BE%89%E5%B7%A5%E4%BD%9C%E7%AB%99%E3%80%8D%E5%9F%BA%E4%BA%8E%20Drone%20%E7%9A%84%20Android%20CI%20%E7%8E%AF%E5%A2%83%20-%20%E5%87%86%E5%A4%87%20Android%20%E7%BC%96%E8%AF%91%E9%95%9C%E5%83%8F/)
[基于 Drone 的 Android CI 环境 - 搭建 Drone 服务](http://www.benjyair.com/2021/02/26/%E3%80%8C%E7%BE%A4%E8%BE%89%E5%B7%A5%E4%BD%9C%E7%AB%99%E3%80%8D%E5%9F%BA%E4%BA%8E%20Drone%20%E7%9A%84%20Android%20CI%20%E7%8E%AF%E5%A2%83%20-%20%E6%90%AD%E5%BB%BA%20Drone%20%E6%9C%8D%E5%8A%A1/)
[基于 Drone 的 Android CI 环境 - 搭建 Gitea](http://www.benjyair.com/2021/02/24/%E3%80%8C%E7%BE%A4%E8%BE%89%E5%B7%A5%E4%BD%9C%E7%AB%99%E3%80%8D%E5%9F%BA%E4%BA%8E%20Drone%20%E7%9A%84%20Android%20CI%20%E7%8E%AF%E5%A2%83%20-%20%E6%90%AD%E5%BB%BA%20Gitea/)
