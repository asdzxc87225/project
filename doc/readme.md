# 目前有幾個要研究的東西

基本

1. untiy 
1. ROS
1. python PyTorch

上面這部份基礎做的差不多的時候就可以進行整合。

# ROS install 
- [下載文件](https://docs.ros.org/en/humble/Installation.html)

## 步驟

1. 系統語系設定
1. 新增ROS2鏡像
1. 安裝ROS2軟體


### 系統語系設定
```sh
locale  # check for UTF-8

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings
```
### 新增ROS2鏡像
```
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
sudo apt update
sudo apt upgrade
```

### 安裝ROS2軟體
```
sudo apt install ros-humble-ros-base
sudo apt install ros-dev-tools
```
