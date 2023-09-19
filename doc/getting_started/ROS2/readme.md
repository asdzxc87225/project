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


