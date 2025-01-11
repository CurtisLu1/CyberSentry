# Backtrance

一个基于 Cowrie 的 SSH 蜜罐部署工具，集成了日志管理和安全防护功能。

## 快速开始

### 一键安装

```bash
bash <(curl -sL https://raw.githubusercontent.com/CurtisLu1/backtrace/main/install.sh)
```

### 系统要求

- Debian/Ubuntu 系统
- Root 权限
- Python 3.x

## 功能特点

- 自动部署 Cowrie SSH 蜜罐
- 集成 Fail2ban 防护
- 自动日志清理（默认保留30天）
- 系统日志自动轮转
- 服务自动启动

## 安装后配置

1. Cowrie 蜜罐运行在端口 2222
2. Fail2ban 配置：
   - 封禁时间：24小时
   - 检测窗口：5分钟
   - 最大重试：3次

## 日志位置

- Cowrie 日志：`/opt/cowrie/var/log/cowrie/`
- 系统日志：`/var/log/`
- 清理日志：`/var/log/cleanup.log`

## 服务管理

```bash
# 查看服务状态
systemctl status cowrie
systemctl status fail2ban

# 重启服务
systemctl restart cowrie
systemctl restart fail2ban
```

## 安全提示

请在生产环境部署前：
1. 修改默认配置
2. 更新系统防火墙规则
3. 定期检查系统日志

## 卸载

如需卸载，请运行以下命令：

```bash
systemctl stop cowrie
systemctl disable cowrie
rm -rf /opt/cowrie
rm /etc/systemd/system/cowrie.service
systemctl daemon-reload
```

## 许可证

MIT License

Copyright (c) 2024

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## 贡献

欢迎提交 Issue 和 Pull Request！
