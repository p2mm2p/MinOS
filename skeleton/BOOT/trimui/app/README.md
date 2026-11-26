<div align="center">
  <h1>Trimui</h1>
  <p>劫持原版的启动流程</p>
</div>

`trimui/` 目录将被复制到 SDCARD 根目录。


不同版本的 Trimui 将从不同的脚本开始启动：

- smart pro/brick：`/usr/trimui/bin/runtrimui.sh`。
- smart：`/etc/main.sh`。


## 文件

- MainUI: 原版 `runtrimui.sh` 或 `main.sh` 会执行它。
- runtrimui.sh: smart pro/brick 版本的替换件。
- main.sh: smart 版本的替换件。


## 劫持流程

1. 原版的 `runtrimui.sh` 或 `main.sh` 执行 SDCARD 根目录的 `MainUI` 程序。
2. `MainUI` 替换原版的 `runtrimui.sh` 或 `main.sh`。
3. `MainUI` 复制 `.tmp_update` 到 SDCARD 根目录。
4. `MainUI` 删除整个 `trimui/` 目录（自身在内存中执行，不会被删除）。
5. `MainUI` 执行 `.tmp_uddate/updater`。
6. `MainUI` 重启系统。


也就是说，整个 `trimui/` 目录是一次性消耗品，劫持完成后将自行销毁。

后续启动直接运行已经替换的 `runtrimui.sh` 或 `main.sh`。

注意：除非新增新设备，否则这个目录不需要改动。
