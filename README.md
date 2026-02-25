# lljb
一个自用的端口流量监控脚本（暂未实现流量限制）   

***不知道修改了多少次了readme也不用read了，直接下载赋权运行就行了***   

🐶 l l j b - 轻量级端口流量监控与防火墙管理工具   
🐶由ai辅助优化    
防火墙和监控用的nft   
自动下载依赖   
剩下的看代码吧   
有ssh保护   
支持debian/Alpine   
🚀 快速安装

方法一：使用 curl（推荐）带防火墙版本

```bash
curl -sSL -o /usr/local/bin/lljb https://raw.githubusercontent.com/looopy66/lljb/main/lljb && chmod +x /usr/local/bin/lljb && lljb
```
不带防火墙纯监控
```bash
curl -sSL -o /usr/local/bin/lljb https://raw.githubusercontent.com/looopy66/lljb/main/clljb && chmod +x /usr/local/bin/lljb && lljb
```

方法二：使用 wget 带防火墙版本

```bash
wget -qO /usr/local/bin/lljb https://raw.githubusercontent.com/looopy66/lljb/main/lljb && chmod +x /usr/local/bin/lljb && lljb
```

方法三：手动下载

1. 下载脚本到 /usr/local/bin/lljb：
   ```bash
   sudo curl -o /usr/local/bin/lljb https://raw.githubusercontent.com/looopy66/lljb/main/lljb
   sudo chmod +x /usr/local/bin/lljb
   ```
2. 运行：
   ```bash
   sudo lljb
   ```

安装后，脚本会自动启动守护进程，您可以直接输入 sudo lljb 进入主菜单。

📖 使用方法

运行 sudo lljb 后，您将看到类似***改了好几回了***主菜单：

```
=================================
       l l j b   主菜单
=================================
当前监控端口: 22 80 443

1. 显示监听端口流量使用量
2. 显示总流量使用量
3. 增加监听端口
4. 删除监听端口
5. 彻底卸载脚本
6. 配置防火墙
0. 退出
=================================
```

端口流量监控

· 选项 1：查看每个监控端口的当日累计流量（入站/出站）。   
· 选项 2：查看所有监控端口的累计总流量。   
· 选项 3：添加要监控的端口（可一次添加多个）。   
· 选项 4：删除已监控的端口。   

防火墙配置

进入防火墙子菜单后：

```
--- 防火墙配置 ---
1. 显示当前防火墙状态 (详细模式)
2. 显示当前防火墙状态 (简洁模式)
3. 修改放行端口（增加/删除）
4. 修改拒绝端口（增加/删除）
5. 一键拒绝所有入站 (自动放行SSH端口)
6. 一键拒绝所有出站 (自动放行SSH端口)
0. 返回主菜单
```

· 增/删放行/拒绝端口：可指定 TCP/UDP 协议（默认两者）。   
· 一键拒绝所有入站：将 INPUT 链默认策略设为 DROP，并确保 SSH 端口放行。   
· 一键拒绝所有出站：将 OUTPUT 链默认策略设为 DROP，同时放行已建立连接、回环接口和 SSH 出站。

🧹 卸载

在主菜单中选择 5. 彻底卸载脚本，或直接执行：

```bash
sudo lljb --uninstall
```

卸载脚本会：

· 停止守护进程。   
· 删除所有带 lljb-managed 注释的 iptables 规则。   
· 删除配置目录 /etc/lljb 和日志文件。   
· 确保 SSH 端口仍被放行。   
· 删除自身脚本文件。   

⚠️ 注意事项

· 必须使用 root 权限运行脚本。   
· 防火墙修改直接操作 iptables，请确保理解每条命令的含义。误操作可能导致 SSH 断开，请务必保留带外管理（VNC/IPMI）或提前测试。   
· 守护进程的 PID 文件位于 /var/run/lljb.pid，日志位于 /var/log/lljb.log。   
· 如果系统缺少 bc、procps 等工具，首次运行时会自动安装。   
· 在 Alpine Linux 中，若内核未加载 iptables 模块，需手动加载或重新编译内核。   

📝 许可证

MIT © looopy66

🤝 贡献

欢迎提交 Issue 和 Pull Request！如果您觉得这个工具有用，请给一个 ⭐ 鼓励一下。

---
