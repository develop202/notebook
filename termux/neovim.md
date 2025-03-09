# nvim远程推送GitHub（没有本地仓库的情况下）

### 1. 克隆远程仓库

```shell
git clone git@github.com:develop202/nvim.git
```

### 2. 替换/修改文件

### 3. 远程推送

```shell
git push -u origin main
```

# git从索引中删除已添加并提交的文件，不删除本地文件

```shell
git rm --cached dir
```

# Termux手动编译neovim

### 1.克隆仓库

```shell
git clone https://github.com/neovim/neovim.git
```

### 2.编译命令

```shell
make CMAKE_BUILD_TYPE=RelWithDebInfo CMAKE_INSTALL_PREFIX=/data/data/com.termux/files/usr/share/nvim
```

### 3.安装(在Termux上需要安装后才可使用)

```shell
make install
```

# 删除包含空白字符的空白行，但不删除只有一个换行符的空行

```shell
:%g/^\s\+$/d
```

# 编译lemminx(xml lsp)

### 1.克隆项目

#### 克隆lemminx

```shell
git clone https://github.com/eclipse-lemminx/lemminx.git
```

#### 克隆lemminx-maven

```shell
git clone https://github.com/eclipse-lemminx/lemminx-maven.git
```

### 2.执行编译命令

```shell
mvn clean package -DskipTests
```

### 3.拷贝文件

#### 需要拷贝的文件如下

```shell
# lemminx
org.eclipse.lemminx-uber.jar
org.eclipse.lemminx-0.29.1-SNAPSHOT.jar

# lemminx-maven
lemminx-maven-0.11.2-SNAPSHOT.jar
lemminx-maven-0.11.2-SNAPSHOT-zip-with-dependencies.zip
```

#### 命令

```shell
cp ~/lemminx/lemminx/org.eclipse.lemminx/target/org.eclipse.lemminx-uber.jar .
```

```shell
cp ~/lemminx/lemminx/org.eclipse.lemminx/target/org.eclipse.lemminx-0.29.1-SNAPSHOT.jar .
```

```shell
cp ~/lemminx/lemminx-maven/lemminx-maven/target/lemminx-maven-0.11.2-SNAPSHOT.jar .
```

```shell
cp ~/lemminx/lemminx-maven/lemminx-maven/target/lemminx-maven-0.11.2-SNAPSHOT-zip-with-dependencies.zip .
```

# 获取终端宽度

```lua
vim.api.nvim_win_get_width(0)
```
