# 目前有幾個要研究的東西

基本

1. untiy 
1. ROS
1. python PyTorch

上面這部份基礎做的差不多的時候就可以進行整合。

# ROS install 
- [下載文件](https://docs.ros.org/en/humble/Installation.html)
- [ros index](https://index.ros.org/)

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

# 建立工作區

1. 啟用ROS2環境
1. 建立目錄
1. 複製範例儲存庫
1. 解決依賴關西
1. 使用colcon建立工作區
1. 來源覆蓋

## 啟用ROS2環境
```sh
source /opt/ros/humble/setup.bash
```
## 建立目錄
```sh
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws/src
```

## 複製範例儲存庫
```sh
git clone https://github.com/ros/ros_tutorials.git -b humble
```
## 解決依賴關西
```sh
# cd if you're still in the ``src`` directory with the ``ros_tutorials`` clone
cd ..
rosdep install -i --from-path src --rosdistro humble -y
```
得到下面的回覆就代表ok沒問題
```sh
#All required rosdeps installed successfully
```

## 使用colcon建立工作區

```
colcon build
```
檢查結果
```
colcon test
```

## 來源覆蓋
用source 去啟用剛剛建立的程式
```
source install/local_setup.bash
```
接下來就可以使用相關功能


