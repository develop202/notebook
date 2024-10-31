# adb 本机

### <mark>提示</mark>

Termux需要先安装android-tools

```shell
pkg install android-tools
```

### 第一步：开启开发者模式

在==关于手机==点击==OS版本号==开启开发者模式

### 第二步：开启无线调试连接Termux

进入==开发者选项==，开启==无线调试==
点击==使用配对码配对设备==，分屏Termux输入

```shell
adb pair address:port 配对码
```

### 第三步：连接设备

配对成功后，关闭窗口
在Termux输入==当前窗口==的IP地址和端口号

```shell
adb connect address:port
```

即可连接成功

# Android12以上限制子线程

### Android 12和Android 13

```shell
./adb shell "settings put global settings_enable_monitor_phantom_procs false"
```

### Android 12

```shell
./adb shell "/system/bin/device_config set_sync_disabled_for_tests persistent; /system/bin/device_config put activity_manager max_phantom_processes 2147483647"
```

==MIUI系统==如果==报错==，请打开==USB调试（安全设置）==
如果无法分屏可以在开发者选项强制开启

```shell
pkg install android-tools
```

```shell
adb shell device_config \
    set_sync_disabled_for_tests persistent
```

```shell
adb \
    shell \
    device_config \
    put activity_manager \
    max_phantom_processes 214181594
```
