# adb 命令备忘

1. adb pull --路径 从手机拷贝文件
2. adb push --电脑路径 --手机路径从电脑拷贝到手机
3. adb shell am monitor  监听手机启动APP的包名
4. adb shell mkdir 新建目录
5. adb -s 设备名 install  apk路径     安装apk到指定设备
6. adb shell dumpsys window | findstr mCurrentFocus 查看当前页面的信息
7. adb shell service list 查看后台services信息
8. adb shell dumpsys gfxinfo packageName framestats
9. adb shell dumpsys meminfo 查看指定进程名或进程id的内存信息
10. adb shell dumpsys package [packagename] 查看指定应用的详细信息 ，打印清单文件
11. adb shell dumpsys dbinfo [packagename] 查看指定应用的数据库存储信息
12. adb shell dumpsys activity top 查看最上层activity的信息-进程信息，布局信息
13. adb shell screencap -p /sdcard/temp.png   截屏保存到指定路径
14. adb shell screenrecord /sdcard/temp.mp4 录屏
15. adb jdwp 查看设备中可以调试的进程号
16. adb shell input text ' 文本' 把电脑文本复制到手机输入框  ,中文需要特殊支持
17. adb shell pm clear [packagename]  清空应用数据
18. adb shell am start -a "android.intent.action,VIEW" -d "https://www.google.com" 启动一个隐式intent
19. adb kill-server      adb start-server 
20. chmod +x gradlew && gradlew -q :mmds_demo:dependencies 查看依赖关系
21. 实时输出日志到指定文件adb shell  logcat -v time > C:\Users\Administrator\Desktop\logcat.txt
22. 输出指定tag的日志 到控制台 adb logcat -s wang
23. 将日志信息输出到指定文件 adb logcat -v time > log.txt 
24. 获取待测应用的userId  adb shell dumpsys package 【包名】 |  findstr userId
25. 启动app adb shell am start com.android.settings/.HWSettings
26. adb shell top -n 1| grep PackageName 查看该包名的性能数据
27. adb shell top [-n/-m/-d/-s/-t] m 最多显示多少进程 n 刷新次数 d 刷新时间间隔 s 按哪里排序 t 显示线程信息
28. adb connect 127.0.0.1:62001 连接夜神模拟器
29. linux dd if=/dev/block/bootdevice/by-name/frp of=/sdcard/frp.bin  文件拷贝命令
30. adb reboot 重启
31. adb push文件失败解决  **mount -o remount -w /** 修改只读权限
32. adb shell ps |grep 包名（相似查询）" 查询对应包的进程信息  
33. adb reboot bootloader 
34. adb reboot recovery
35. fastboot flash recovery Recovery.img 刷入 recovery
36. adb rm -r 删除文件夹
37. adb forward tcp:27042 tcp:27042   端口映射
38. adb shell am start -D -n  应用程序包名/应用程序入口界面  调试模式启动
39. adb shell am start -n  应用程序包名/应用程序入口界面  启动
40. adb shell am startservice -n  应用程序包名/服务名  启动
41. adb shell am broadcast -a [广播动作] 发送一个广播
42. adb jdwp 用于查看Android手机中可调式的进程
43. adb shell cat /proc/cpuinfo 查看cpu架构等信息   
44. adb shell netstat 查看设备端口号
45. adb shell dalvikvm -cp  (dex文件)[运行主类] 执行dex 文件
46. adb shell getprop [属性值名称] 查看系统属性值
47. adb shell cat  /proc/[pid]/maps 查看进程的内存加载情况
48. adb shell cat  /proc/[pid]/status 查看进程状态信息  包含TracerPid跟踪进程的pid
49. adb shell cat  /proc/[pid]/net/tcp/tcp6/udp/udp6 获取当前应用使用的端口号信息
50. adb shell pm list packages 列出安装的应用包
51. adb shell getprop ro.product.brand 获取手机品牌
29. adb  shell  monkey -p  com.leo.uilib.popupdemo  -v 500  模拟触摸
29. 

# Gradlew 命令

/gradlew clean  clean项目

./gradlew build  构建项目

./gradlew assembleDebug or /gradlew aD 编译并打Debug包

./gradlew assemble渠道号Debug or /gradlew aD 编译并打Debug渠道包

./gradlew assembleRelease or /gradlew aR 编译并打Release的包

./gradlew installRelease or /gradlew iR Release模式打包并安装

./gradlew installDebug or /gradlew iD Debug模式打包并安装

./gradlew install渠道号Debug  打渠道包

./gradlew uninstallRelease or ./gradlew uR 卸载Release模式包

  configurations.all{
            resolutionStrategy{
                failOnVersionConflict()
            }
        }

