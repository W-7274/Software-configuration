<h1>首先</h1>

在当前根目录下打开终端（Terminal 或 Git Bash），执行初始化命令：

Bash

```
git init
```

这将创建一个隐藏的 `.git` 文件夹，让这个目录变成一个 Git 本地仓库。

### 第一步：创建 `.gitignore` 文件

1. 在 VS Code 左侧的资源管理器（Explorer）空白处**右键**，选择 **新建文件 (New File)**。

2. 输入文件名 `.gitignore` 并回车。

3. 在打开的文件编辑窗口中，根据你的需求输入以下内容（假设你只想上传 `ACME_vc` 和 `ACMEv2-src`）：

   ```
   # 忽略根目录下所有文件和文件夹
   /*
   
   # 排除（即不要忽略）以下内容
   !.gitignore
   !/ACME_vc/**   //**代表追踪所有文件
   !/ACMEv2-src/**
   ```

4. 按下 `Ctrl + S` 保存。此时你会发现 VS Code 左侧树状图中，被忽略的文件夹颜色会变淡。

------

### 第二步：暂存文件 (git add)

在 VS Code 中，你可以用图形化操作：

1. 点击左侧侧边栏的 **源代码管理 (Source Control)** 图标（看起来像一个分叉的图标，或者按 `Ctrl + Shift + G`）。
2. 你会看到“更改 (Changes)”列表中，只出现了 `.gitignore`、`ACME_vc` 文件夹下的文件。
3. 点击“更改”列表旁边的 **`+` (加号)**。这相当于执行了 `git add .`。此时文件会移动到“暂存的更改 (Staged Changes)”一栏。

------

### 第三步：提交更改 (git commit)

1. 在“源代码管理”视图顶部的输入框中，输入你的提交信息，例如：`首次上传指定文件夹`。
2. 点击上方的 **提交 (Commit)** 按钮（勾选图标）。

------

<h1>注意</h1>

如果只是更改某个已经上传的文件里的内容，二三步可能不显示

可以

```
\# 1. 移除所有已缓存的追踪（注意末尾有一个点，这不会删除物理文件） git rm -r --cached .
```

然后提交一次，就恢复正常了

或者在第一步追踪的时候加上**（我一开始没加）

### 第四步：关联并推送到远程仓库

这一步需要用到 VS Code 的内置终端。

1. 按 `Ctrl + `` (反引号) 打开终端。

2. **关联远程地址**（请将下面的 URL 换成你自己在 GitHub/Gitee 创建的仓库地址）：

   Bash

   ```
   git remote add origin https://github.com/你的用户名/仓库名.git
   ```

3. **推送到远程**（如果是新仓库，通常分支名是 `main`）：

   ```
   git branch             //可以查看分支
   ```

   Bash

   ```
   git push -u origin main
   ```

   要是覆盖之前的内容可以选择强制执行

   ```
   git push -u origin main -f
   ```

   或者（有可能报错会提示用pull）

   ```
   git pull origin main --rebase
   ```

   选择想要的合并再继续push

   *如果提示分支不存在，可以试试 `git push -u origin master`。*

------

