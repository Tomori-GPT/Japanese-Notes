# Softbank现场日语笔记
- [Poderosa](#poderosa)
- [JFrog Artifactory](#jfrog-artifactory)
- [Ansible](#ansible)
- [WinSCP](#winscp)
- [Linux](#linux)

## 日语读法确认
|||
|--|--|
|Git  |ギット
|GitLab  |ギットラボ
|Ansible | アンシブル
|WinSCP | ウィン・エス・シー・ピー
|PuTTY | パティ
|Poderosa | ポデローサ
|JFrog | ジェイフロッグ
|Artifactory | アーティファクトリー
|YAML (.yml)|
|Tab|


## Poderosa
- ポデローサ 西班牙语（意为“强大的”“有力量的”）

### [Top](#softbank现场日语笔记)

## JFrog Artifactory
- 公司 的 制品/软件包 仓库（Artifact Repository）
```
    GitLab  存放源代码
```
```
    JFrog Artifactory   存放编译后的软件、依赖包和镜像
```

- Artifact（制品）: 开发过程中生成或使用的文件
```
    * .jar .war
    * Maven 依赖
    * npm 包
    * Docker 镜像
    * ZIP 压缩包
    * Ansible Role
```

- 公司部署 Artifactory 代替 Maven Central 
- 统一从 公司内部的私有库 下载依赖

```
    Maven Central
        │
        ▼
    JFrog Artifactory
        │
    ┌─────┼─────┐
    ▼     ▼     ▼
    开发者  CI   服务器
```

- 搭配CI/CD（持续集成/持续部署）
```
    开发者
        │
        ▼
    GitLab（提交源码）
        │
        ▼
    CI/CD（Jenkins、GitLab CI 等）
        │
        ▼
    编译、打包
        │
        ▼
    上传到 JFrog Artifactory
        │
        ▼
    Ansible
        │
        ▼
    从 Artifactory 下载制品
        │
        ▼
    部署到测试或生产服务器
```

### [Top](#softbank现场日语笔记)

## Ansible
- 自动登录很多服务器，然后按照 PlayBook 剧本（YAML）去执行命令
```
SSH（远程登录）
   │
Linux
   │
YAML（配置文件）
   │
Ansible（自动执行）
```
- 控制节点（Control Node） 
- 受控节点（Managed Node）

|名称|是什么|作用
|--|--|--|
YAML (.yml)|配置文件|告诉 Ansible 要做什么
|SSH|远程登录协议|Ansible 用它连接服务器
|Inventory|服务器清单|告诉 Ansible 要连哪些机器
|Playbook|自动化剧本|一份 .yml 文件，描述一系列任务
|Role|模块化剧本|把 Playbook 按功能拆分，便于复用
|Module|功能模块|Ansible 内置的操作，例如复制文件、安装软件、创建目录等

### [Top](#softbank现场日语笔记)

## WinSCP
- Windows 上文件传输工具
- 用于在本地电脑和远程 Linux/Unix 服务器之间传输文件
- 相当于 Windows 资源管理器 + SSH 文件管理器

### 用途
1. 上传文件
    * 例如把 Ansible 的 Playbook 上传到 Linux 服务器。
2. 下载文件
    * 把服务器上的日志（log）下载到本地查看。
3. 编辑服务器上的文件
    * 双击服务器上的配置文件（如 hosts、nginx.conf），修改后保存，WinSCP 会自动上传。
4. 删除、复制、移动文件
    * 像 Windows 文件管理器一样操作远程服务器。
5. 修改文件权限（chmod）
    * 在 Linux 上经常需要。
6. 创建目录
7. 与 PuTTY 集成
    * 直接打开 SSH 终端。

### [Top](#softbank现场日语笔记)

## Linux
- SSH (远程登录 Linux 服务器的协议)
- Linux 常用命令

### [Top](#softbank现场日语笔记)