# Slate 工具的使用
Slate 可以帮助你创建美观、智能、响应迅速的 API 文档。

Screenshot of Example Documentation created with Slate

以上 API 示例文档通过 Slate 创建。你可以点击链接 slatedocs.github.io/slate 一探究竟。

# 开始使用 Slate
## 先决条件
你需要:
- Linux or macOS — Windows 系统下可能也可以运行，但并不支持。
- Ruby, version 2.3.1 or newer
- Bundler —如果 bundle 命令不起作用，只需在终端中运行 gem install bundler 安装即可。

```
gem install bundler
gem install bundler --user-install
```



## 开始设置
### 在 GitHub 上 fork 此存储库.
将你 fork 下来的存储库（不是我们原始的存储库）克隆到本地硬盘，可以执行此命令：
```agsl
git clone https://github.com/YOURUSERNAME/slate.git
cd slate
```

### 初始化并启动 Slate。你可以在本地或通过 Vagrant 进行操作:
 - 要么运行以下命令在本地运行 
 - 注：第一次运行这条命令会花很长时间来安装很多包文件。 
 - 建议首先执行以下命令配置路径，将 gems 安装到 ./vendor/bundle/ 目录下，否则系统会经常让你输入密码以获取操作权限，或者遇到没有拷贝权限以至于安装失败的问题。
```
bundle config set path 'vendor/bundle'
bundle config set path 'vendor/bundle'
bundle install ...
bundle exec middleman server
```

### 本地预览
你现在可以在 http://localhost:4567 看到文档了

### 线上部署
执行项目中的 `deploy.sh` 文件即可

### 线上验证
