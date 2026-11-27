Trimui - 劫持启动
=================

trimui/ 将被复制到 SDCARD 根目录。

注意：除非新增新设备，否则这个目录不需要改动。


版本差异
========

启动脚本位置：
- smart：          /etc/main.sh
- smart pro/brick：/usr/trimui/bin/runtrimui.sh


文件列表
========

- MainUI:       劫持程序
- main.sh:      smart 版本的替换件
- runtrimui.sh: smart pro/brick 版本的替换件


劫持流程
========

1. 原版 runtrimui.sh 或 main.sh 执行 SDCARD 根目录的 MainUI 劫持程序
2. MainUI 备份并替换原版的 main.sh 或 runtrimui.sh
3. MainUI 复制 .tmp_update 到 SDCARD 根目录
4. MainUI 删除整个 trimui/ 目录（MainUI 自身在内存中，在退出前不会被删除）
5. MainUI 执行 .tmp_uddate/updater
6. MainUI 重启系统


整个 trimui/ 是一次性消耗品，劫持完成后将自行销毁，后续启动运行已经替换的 runtrimui.sh 或 main.sh。
