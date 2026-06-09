# Claude Code 官方安装时报错解决

## 1. 国内科学上网下载 Claude Code 时，使用官方安装脚本（原生安装）

```powershell
irm https://claude.ai/install.ps1 | iex
```

会报错：

![原生安装报错](image/image_1.png)

---

## 2. 解释说明

通常是因为科学上网时没有开启全局代理，仅有浏览器可以科学上网。

例如浏览器可以正常访问 Google：

![浏览器访问 Google](image/image_2.png)

但在本地 PowerShell 中无法 ping 通 Google：

```powershell
ping google.com
```

![PowerShell 无法访问 Google](image/image_3.png)

这就说明科学上网没有开启全局代理，仅有浏览器能够科学上网，而 PowerShell 等系统程序无法通过代理访问外网。

---

## 3. 解决方法

通过科学上网软件开启 TUN 模式（虚拟网卡）。

下面列举几个常用软件的配置方式。

### Clash Party

关闭「系统代理」，开启「虚拟网卡（TUN 模式）」。

![Clash Party 操作步骤 1](image/image_4.png)

### v2rayN

开启 TUN 模式：

![v2rayN 操作](image/image_6.png)

---

## 4. 验证是否生效

重新打开 PowerShell，执行：

```powershell
ping google.com
```

如果能够正常解析 Google 域名并返回结果，说明 TUN 模式已经生效。
> [!WARNING]
> 还有一种可能，虽然 ping 不通 Google，但 Claude Code 安装命令仍然可以正常执行。
随后重新执行 Claude Code 官方安装命令：

```powershell
irm https://claude.ai/install.ps1 | iex
```

即可正常下载安装。
