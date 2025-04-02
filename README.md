以下是一个 **Markdown 文档**，详细说明了在 **宝塔卸载工具** 中做了哪些改进，并感谢了原作者 [TeamVastsea](https://github.com/TeamVastsea/bt-uninstall)。

---

# 宝塔卸载工具改进说明

## 项目背景
本项目基于 [TeamVastsea/bt-uninstall](https://github.com/TeamVastsea/bt-uninstall) 的宝塔卸载工具进行改进，旨在优化卸载流程并增加新功能，确保卸载过程更加彻底和用户友好。

---

## 改进内容

### 1. **新增删除 `user.ini` 文件功能**
   - **问题**：原脚本未处理 `user.ini` 文件，可能导致残留配置影响后续操作。
   - **改进**：
     - 新增 `Remove_User_Ini` 函数，使用 `find` 命令递归删除 `/www/wwwroot` 目录下所有 `user.ini` 文件。
     - 在主菜单中新增选项 `4`，支持卸载宝塔面板、运行环境、站点数据以及所有 `user.ini` 文件。

### 2. **功能模块化**
   - **问题**：原脚本逻辑较为集中，不利于维护和扩展。
   - **改进**：
     - 将卸载功能拆分为多个模块：
       - `Remove_Bt`：卸载宝塔面板
       - `Remove_Rpm`：卸载宝塔相关 RPM 包
       - `Remove_Service`：卸载宝塔相关服务
       - `Remove_Data`：清除所有站点相关数据
       - `Remove_User_Ini`：删除所有 `user.ini` 文件
     - 提高代码可读性和可维护性。

### 3. **用户交互优化**
   - **问题**：原脚本仅提供 3 种卸载选项，功能较为单一。
   - **改进**：
     - 扩展主菜单，新增选项 `4`，支持更彻底的卸载操作。
     - 在每一步操作中添加提示信息，确保用户了解当前进度。

### 4. **错误处理增强**
   - **问题**：原脚本未充分处理潜在错误（如宝塔未安装或安全插件未关闭）。
   - **改进**：
     - 在 `Remove_Bt` 函数中添加检查逻辑，确保宝塔已安装且未启用系统加固或防篡改插件。
     - 在关键操作中添加错误提示，避免因配置问题导致卸载失败。

### 5. **兼容性优化**
   - **问题**：原脚本对部分 Linux 发行版的兼容性较差。
   - **改进**：
     - 支持 `chkconfig` 和 `update-rc.d` 两种服务管理工具。
     - 支持 `yum` 和 `rpm` 包管理工具。

---

## 使用说明

### 1. **下载脚本**
   ```bash
   wget https://raw.githubusercontent.com/samuel25555/bt-uninstall/main/bt-uninstall.sh
   ```

### 2. **赋予执行权限**
   ```bash
   chmod +x bt-uninstall.sh
   ```

### 3. **运行脚本**
   ```bash
   ./bt-uninstall.sh
   ```

### 4. **选择卸载选项**
   - `1`：仅卸载宝塔面板
   - `2`：卸载宝塔面板及运行环境
   - `3`：卸载宝塔面板、运行环境并清除所有站点数据
   - `4`：卸载宝塔面板、运行环境、站点数据以及所有 `user.ini` 文件

---

## 感谢原作者
本项目基于 [TeamVastsea/bt-uninstall](https://github.com/TeamVastsea/bt-uninstall) 进行改进，感谢原作者的开源贡献。原项目为宝塔面板卸载提供了基础功能，本次改进在此基础上进一步优化了卸载流程和用户体验。

---

## 许可证
本项目遵循 [MIT 许可证](https://opensource.org/licenses/MIT)，欢迎贡献和改进。

---

## 贡献者
- [samuel25555](https://github.com/samuel25555)

---

## 反馈与支持
如有任何问题或建议，请提交 [Issue](https://github.com/samuel25555/bt-uninstall/issues)

---

希望这份文档能清晰地说明改进内容，并表达对原作者的感谢！如果需要进一步调整或补充，请随时告诉我。
