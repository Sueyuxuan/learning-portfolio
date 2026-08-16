# Anaconda Installation Checklist
### 从两次真实安装中总结的踩坑清单

> 背景说明（Context）：这份 checklist 基于我两次真实的 Anaconda 安装经历总结出来的。
> 第一次是在原来的电脑上安装时踩了不少坑（权限问题、PATH 没配、Jupyter 缺失、浏览器不自动打开）；
> 第二次是换了一台新电脑重装，Kaggle 三门课程已经学完，这次我对照第一次的坑，提前规避了大部分问题，也验证了当时的解决办法是否真的有效。
> This document distills two real installation experiences (one on my original machine, one after switching computers) into a reusable reference — the goal is not just to record what went wrong, but to prevent it from happening again.

---

## 使用方法

以后不管在哪台电脑上装 Anaconda，按下面的顺序走一遍，理论上能避开我踩过的全部坑。

---

## ✅ Step 1：安装模式选 Just Me，不要选 All Users

安装向导第一步会问 **"Just Me" 还是 "All Users"**。

- **一律选 Just Me。** 个人电脑装给单个用户就够了。
- 第一次我选了 All Users，装进了系统保护目录，后续几乎所有操作（装包、改配置）都会碰到权限不足的问题。
- *English note: "All Users" installs Anaconda into a system-protected directory (e.g. Program Files), which requires admin rights for almost every subsequent action. "Just Me" installs into the user directory instead, avoiding this entirely — the officially recommended option for personal machines.*

## ✅ Step 2：安装时勾选 "Add Anaconda to my PATH environment variable"

- 安装器默认**不勾选**这一项，并且会标红提示"不推荐"。第一次我照做没勾，结果命令行完全认不出 `conda`、`jupyter` 这些命令。
- 这次重装我**主动勾选**了它，装完直接在普通命令行（cmd / PowerShell）里就能用，不用再去系统设置里手动加环境变量。
- 如果这次也没勾、或者勾了还是不认命令，手动补救的位置：把 **Anaconda 安装目录** 和它下面的 **Scripts 子文件夹** 两条路径，加进系统环境变量的 `Path` 里。
- *English note: PATH is essentially a list of folders the OS searches through when you type a command. Checking this option during install saves the manual step of adding `<Anaconda install path>` and `<Anaconda install path>\Scripts` to the system PATH afterwards.*
- 另外提醒：即使不勾这个选项，开始菜单里自带的 **Anaconda Prompt** 也是可以直接用的，因为它启动时会自动加载好环境——只是普通 cmd 用不了而已。

## ✅ Step 3：装完先检查 Navigator 里有没有 Jupyter Notebook / Jupyter Lab

- 第一次安装完，Navigator 首页**没有** Jupyter Notebook 和 Jupyter Lab 的启动卡片，需要额外手动装。
- 打开 **Anaconda Prompt**，运行：

```bash
conda install jupyter
conda install jupyterlab
```

- 装完刷新 Navigator（或重新打开），两个卡片应该就出现了。
- 这次重装时我第一时间就检查了这一步，确认缺失后直接执行上面两条命令，几分钟就解决了，没再走弯路。

## ✅ Step 4：确认 Jupyter Lab 能启动，并检查浏览器是否自动打开

在 Anaconda Prompt 里运行：

```bash
jupyter lab
```

- 正常情况下会自动弹出浏览器窗口。如果命令行打印出一串 `http://localhost:8888/...` 的地址但浏览器没反应：
  1. 先手动复制地址到浏览器，确认服务本身是正常的（能打开就说明只是"自动打开"这一步的问题，不是安装失败）。
  2. 可以运行 `jupyter lab --generate-config` 生成配置文件，在里面指定默认浏览器。
  3. 更省事的办法：做一个 **.bat 文件**（Windows 批处理脚本），内容大致是一行 `jupyter lab` 启动命令，以后双击它就能直接打开，不用每次都敲 Anaconda Prompt。
- *English note: A `.bat` file is a simple Windows script that runs a sequence of commands automatically. Saving one line like `jupyter lab` into a `.bat` file turns a multi-step manual launch into a single double-click.*

## ✅ Step 5：验证安装是否完整

装完后，建议依次运行下面几条命令做个"体检"，全部有正常输出才算真正装好：

```bash
conda --version      # 确认 conda 本身可用
python --version     # 确认 Python 版本
jupyter --version    # 确认 Jupyter 相关组件齐全
```

---

## 两次安装的对比小结

| 问题 | 第一次（原电脑） | 第二次（新电脑） |
| --- | --- | --- |
| 安装模式 | 选了 All Users，后续处处受权限限制 | 直接选 Just Me，未再遇到权限问题 |
| PATH 环境变量 | 装完才发现没勾，事后手动添加 | 安装时主动勾选，省去手动步骤 |
| Jupyter 缺失 | 事后在 Prompt 里补装，命令凭记忆搜索，没记录下来 | 提前检查、直接执行 `conda install jupyter(lab)`，两分钟解决 |
| 浏览器自动启动 | 不生效，最后靠做 bat 文件解决 | 同样用 bat 文件方案，直接复用第一次的思路 |

**最大的收获**：不是记住了几条命令，而是明白了"装环境"这件事本身也值得像调试代码一样——遇到问题先定位（是权限？是路径？是缺组件？），再针对性解决，而不是瞎试。第一次几乎每一步都在"边装边搜"，第二次基本是照着自己写的清单走完，全程不到 15 分钟。

*The biggest takeaway wasn't memorizing specific commands, but learning to treat environment setup like debugging — identify whether the issue is a permissions problem, a PATH problem, or a missing package, then address it specifically rather than guessing. The second install, guided by this checklist, took under 15 minutes with zero unexpected issues.*
