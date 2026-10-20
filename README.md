<img src="https://raw.githubusercontent.com/machanghan/2008/refs/heads/main/ScreenShot_2026-07-05_202602_200.png" width="600" />
适配 Windows / Mac / Linux

## 前置准备

### 1. GitHub 新建空仓库

- 仓库名称：`2008`
- 不用勾选 Add README、开源协议、.gitignore 文件
- 直接点击 Create repository 创建纯空白仓库

### 2. 生成 GitHub 私有 Token（操作密钥）

1. GitHub 头像 → Settings → Developer settings
2. Personal access tokens → Tokens(classic)
3. 点击 Generate new token(classic)
4. Note 备注随便填写（例：2008仓库整活）
5. Expiration 有效期选择：**随便**
6. 权限仅勾选 **repo**，并全选 repo 下所有子权限
7. 拉至页面最底部，点击 Generate token
8. **立即复制保存密钥**，关闭页面后无法再次查看

## 步骤 1：打开对应终端

- **Windows**：提前安装 Git，文件夹空白处右键 → Git Bash Here
- **Mac**：启动台打开「终端」
- **Linux**：直接打开系统 Terminal 终端

## 步骤 2：复制一键执行命令

完整通用命令，无需修改任意内容，直接复制：

```bash
sh -c 'YEAR=2008;read -p "请输入你的GitHub用户名：" U;read -p "粘贴你的GitHub Token：" T;mkdir $YEAR;cd $YEAR;git init;echo $YEAR>README;git add .;GIT_AUTHOR_DATE=2008-01-01T18:00:00 GIT_COMMITTER_DATE=2008-01-01T18:00:00 git commit -m $YEAR;git remote add origin https://$T@github.com/$U/$YEAR.git;git push -u origin main'
```

## 步骤 3：终端交互式填写信息

粘贴命令后按回车，根据提示依次输入信息：

1. 提示 `请输入你的GitHub用户名：` 输入 GitHub 主页后缀名称（示例：网址 https://github.com/machanghan ， 只需输入  `machanghan`），回车
2. 提示 `粘贴你的GitHub Token：` 粘贴之前复制的密钥，**屏幕无字符显示为正常现象**，直接回车即可

## 步骤 4：等待自动执行完成

终端全自动执行全套流程，无需手动干预：

1. 自动创建 2008 本地文件夹
2. 初始化 Git 空仓库
3. 生成 2008 年远古时间提交记录
4. 绑定远程 2008 仓库
5. 自动推送代码至 GitHub

**成功判定**：终端输出 `To https://github.com/xxx/2008.git` 且无任何报错，即为部署完成。

## 可选收尾优化

1. 刷新 GitHub 个人主页，贡献日历最左侧年份更新为 **2008**，远古buff永久生效
2. 仓库美化：可将 2008 仓库设置为**私有仓库**，私有仓库提交记录依旧计入主页贡献，年份效果不会消失
3. 安全优化：操作完成后，前往 GitHub 后台删除本次使用的 Token，避免密钥泄露

## 常见报错傻瓜式排查

- **报错：remote origin already exists** 原因：本地残留旧配置 解决：删除本地 2008 文件夹，重启终端重新执行命令
- **报错：404 推送失败** 原因：用户名输入错误 / 未提前创建名为 2008 的空仓库 解决：核对用户名，重新新建空白 2008 仓库
- **报错：401 权限不足** 原因：Token 权限缺失、复制不全或已过期 解决：重新生成带完整 repo 权限的 Token
- **粘贴报错 command not found** 原因：快捷键粘贴带入隐形乱码 解决：右键终端空白处粘贴，不使用 Ctrl+V
- **邮箱隐私拦截推送失败** 解决：GitHub 邮箱设置，关闭「拦截命令行推送暴露邮箱」选项

## 核心原理（极简科普）

依托 Git 官方原生时间戳自定义能力，通过 `GIT_AUTHOR_DATE`、`GIT_COMMITTER_DATE` 双环境变量锁定提交时间，仅修改单次提交记录，**不篡改账号注册时间、无违规风险、永久生效**。
