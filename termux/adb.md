# adb 本机

### <mark>提示</mark>

Termux需要先安装android-tools

```shell
pkg install android-tools
```

### 第一步：开启开发者模式

在<mark>关于手机</mark>点击<mark>OS版本号</mark>开启开发者模式

### 第二步：开启无线调试连接Termux

进入<mark>开发者选项</mark>，开启<mark>无线调试</mark>
点击<mark>使用配对码配对设备</mark>，分屏Termux输入

```shell
adb pair address:port 配对码
```

### 第三步：连接设备

配对成功后，关闭窗口
在Termux输入<mark>当前窗口</mark>的IP地址和端口号

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

<mark>MIUI系统</mark>如果<mark>报错</mark>，请打开<mark>USB调试（安全设置）</mark>
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
