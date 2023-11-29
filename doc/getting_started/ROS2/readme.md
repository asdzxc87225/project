# ROS入門

- [ROS2 LST官方文檔](http://docs.ros.org/en/humble/index.html)
- [micro ROS](https://micro.ros.org/docs/tutorials/core/overview/)
- [參考書](https://www.tenlong.com.tw/products/9787111715504)
- [Getting Started with ROS Part 1: Nodes, Parameters and Topics](https://www.youtube.com/watch?v=46TPAKXBOF8)
# 安裝

- [官方ubuntu](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html)
- [it文章](https://ithelp.ithome.com.tw/articles/10239445)
- [Foxy ](https://docs.ros.org/en/foxy/Installation.html)

## 運行測試

### step1 
要先啟用ros2的環境。
```
source /opt/ros/humble/setup.zsh
```
根據使用者的shell去下對應的指令
bash 的改成下面
```
source /opt/ros/humble/setup.bash
```

### setp2 
接下來我們可以試著開啟了。
```
ros2 run turtlesim turtlesim_node
```
這時你會看到一個視窗，上面有個圖示。

### step3 

開另外一個terminal ，可以確定有幾個節點(node)

```
╭─luu@luu-ASUSLaptop ~/doc/project/doc/getting_started/ROS2 ‹main●›
╰─$ ros2 node list
/turtlesim
```
### step4

確認節點後就可以連結上去控制。

```
╭─luu@luu-ASUSLaptop ~/doc/project/doc/getting_started/ROS2 ‹main●›
╰─$ ros2 run turtlesim turtle_teleop_key
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation.
'Q' to quit.
```

### step5

接著在檢查節點，這時可以看到兩個。
```
ros2 node list                                                                                   2 ↵
/teleop_turtle
/turtlesim
```

這樣基本的操作就結束了。
## rqt 使用
如果開啟沒看到任何東，可以去Plugins去設定。
### 重新映射

```
ros2 run turtlesim turtle_teleop_key --ros-args --remap turtle1/cmd_vel:=turtle2/cmd_vel
```
在原先的指令後面加上
```
--ros-args
```
之後就可重新命名

# ROS 2 中的基本概念
## Subscribers（訂閱者）：

概念： 訂閱者是ROS 2中的節點，它用來接收特定主題（Topic）上發布的消息。節點可以訂閱一個或多個主題，以接收感測數據、狀態信息等。訂閱者使用異步通信模型，當有新消息時，它會執行相應的回調函數[1]。
## Publishers（發布者）：

概念： 發布者是ROS 2中的節點，它用來向特定主題上發布消息。消息可以包含感測數據、狀態信息等。與訂閱者相對應，發布者也使用異步通信模型，將消息發布到主題，讓訂閱者能夠接收[2]。
## Service Servers（服務伺服器）：

概念： 服務伺服器是ROS 2中的節點，它提供了一種請求-響應模型的通信方式。當有節點需要某種服務時，它可以向服務伺服器發送請求，並等待伺服器的響應。這種機制通常用於執行一些複雜的任務，如機器人的特定動作[3][4]。
## Service Clients（服務客戶端）：

概念： 服務客戶端是ROS 2中的節點，它用於向提供特定服務的伺服器發送請求並等待響應。當節點需要執行一項特定的任務時，它會向相應的服務伺服器發送請求[4]。
## Action Servers（動作伺服器）：

概念： 動作伺服器是ROS 2中用於處理異步任務的機制。與服務相似，動作提供了一種執行較長時間的任務的方法。動作伺服器可以提供反饋（feedback）和結果（result），這使得在執行過程中能夠向發起請求的節點提供即時信息[1][6]。
## Action Clients（動作客戶端）：

概念： 動作客戶端是ROS 2中的節點，它用於向提供動作的伺服器發送目標（goal），並等待伺服器的反饋（feedback）和最終的結果（result）。動作客戶端通常用於執行需要長時間完成的任務，例如機器人的導航[1][5]。
以上概念是ROS 2中用於實現節點之間通信和執行複雜任務的基本元素。

|類型|概念|ROS2中的角色 |通信模型 |用途|
|--|--|--|--|--|
|Subscribers（訂閱者）	|接收特定主題上發布的消息，使用異步通信模型，有新消息時執行回調函數[1]	|節點	|異步	|接收感測數據、狀態信息等|
|Publishers（發布者）	|向特定主題上發布消息，使用異步通信模型，發布消息到主題[2]	|節點	|異步	|發布感測數據、狀態信息等|
|Service Servers（服務伺服器）	|提供請求-響應模型的通信方式，執行複雜的任務[3][4]	|節點	|同步	|提供特定服務，執行複雜任務|
|Service Clients（服務客戶端）	|向服務伺服器發送請求並等待響應，用於執行特定任務[4]	|節點	|同步	|向服務伺服器發送請求，等待伺服器響應|
|Action Servers（動作伺服器）	|處理異步任務的機制，提供反饋和結果，執行較長時間的任務[1][6]	|節點	|異步	|處理需要長時間完成的任務，提供反饋和結果|
|Action Clients（動作客戶端）	|向動作伺服器發送目標，等待伺服器的反饋和結果，用於長時間任務[1][5]	|節點	|異步	|向提供動作的伺服器發送目標，等待伺服器反饋和結果|

## Service Servers vs. Action Servers
| |Service Servers（服務伺服器）	|Action Servers（動作伺服器）|
|--|--|--|
|用途	|實現 ROS 中的服務，較簡單的請求-回應場景。	|實現 ROS 中的動作，較長時間執行的任務。|
|特點	|處理來自客戶端的請求，同步通信，客戶端等待伺服器回應。	|支援複雜行動，包括目標設定、回饋、取消等功能。異步通信，客戶端可繼續執行其他任務。|

----------------

## 同步v.s異步
### 定義：
同步通訊：通信方在發送請求後需要等待回應，期間通信方被阻塞，直到接收到回應為止[1][3]。
異步通訊：通信方在發送請求後不需要等待回應，可以繼續執行其他任務。接收回應的過程通常使用回調（Callback）函數或事件通知[1][6]。
### 阻塞與非阻塞：

同步通訊：是阻塞的，通信方在等待回應的過程中無法執行其他任務[1][3]。
異步通訊：是非阻塞的，通信方在等待回應的同時可以執行其他任務[6]。
### 實時性：

同步通訊：更容易實現實時性，因為通信發送和接收是同步的，可以確保及時回應[2]。
異步通訊：由於通信是非阻塞的，可能存在一些延遲，不太適合要求即時性的應用[6]。
### 應用場景：

同步通訊：適用於需要確保順序和實時性的應用，如一對一通話、同步數據庫查詢[2][3]。
異步通訊：適用於需要高併發、非阻塞的應用，如網絡通信、消息發布訂閱[6]

|概念	|定義	|阻塞/非阻塞	|實時性	|應用場景|
|--|--|--|--|--|
|同步通訊 |通信方發送請求後需等待回應，期間被阻塞，直到接收到回應。 |阻塞|容易實現實時性，通信發送和接收同步。|需要確保順序和實時性的應用，如一對一通話、同步數據庫查詢。|
|異步通訊 |通信方發送請求後不需等待回應，可繼續執行其他任務。回應接收通常使用回調函數或事件通知|非阻塞|由於非阻塞，可能存在延遲，不太適合即時性應用。|高併發、非阻塞的應用，如網絡通信、消息發布訂閱。|

----------------

# 導航
```sh
rqt_graph
source /opt/ros/humble/setup.zsh
export TURTLEBOT3_MODEL=waffle_pi
export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:/opt/ros/humble/share/turtlebot3_gazebo/models
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```
```sh
source /opt/ros/humble/setup.zsh
ros2 launch slam_toolbox online_async_launch.py
```
```sh
source /opt/ros/humble/setup.zsh
rviz2
```
```sh
source /opt/ros/humble/setup.zsh
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```
