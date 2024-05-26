## 配置文件
`git config`
	配置变量被存储在三个不同的位置

1. /etc/gitconfig：系统配置文件，包含了系统中所有用户及其仓库的值，使用`--system`访问该文件。window系统该文件在git的安装路径中
2. ~/.gitconfig或~/.config/git/config：用户配置文件，针对的是你的这台设备，使用`--global`访问，window系统该文件在`C:User/用户`
3. 当前仓库(.git/config)：当前仓库的git配置

优先级：仓库配置 > 用户配置 > 系统配置

### 配置
 - `user.name`用户名
 - `user.email`邮箱
 - `core.editor`文本编辑器

#### 检查配置
`git config --list`
`git config <key>`来查看这个键的值。如：
`git config user.name`

