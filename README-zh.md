# SpurtCMS - 基于Golang的开源内容管理系统

<p align="center">
  <a href="https://www.spurtcms.com">
      <img src="https://spurtcms.com/public/img/SpurtCMSlogov1.2.1.svg" width="318px" alt="Spurtcms logo" />
  </a>
</p>

<h3 align="center">开源自托管Golang CMS解决方案</h3>
<p align="center">采用 Golang + PostgreSQL 构建</p>

<br />

<p align="center">
  <a href="https://github.com/spurtcms/spurtcms/releases">
    <img src="https://img.shields.io/github/last-commit/spurtcms/spurtcms/main" alt="GitHub last commit" />
  </a>
  <a href="https://github.com/spurtcms/spurtcms/issues">
    <img src="https://img.shields.io/github/issues/spurtcms/spurtcms/main" alt="GitHub issues" />
  </a>
  <a href="https://github.com/spurtcms/spurtcms/releases">
    <img src="https://img.shields.io/github/repo-size/spurtcms/spurtcms" alt="GitHub repo size" />
  </a>
</p>

<br />

> [!重要]
> 🎉 <strong>SpurtCMS V1.3 现已发布！</strong> 请查看<a target="_blank" href="https://www.spurtcms.com/spurtcms-change-log">发布公告</a>了解更多详情。

<br />

## 📖 系统概述

SpurtCMS 是一个功能强大的开源内容管理系统，专注于用户友好的管理界面，为内容创建、管理和CMS工作空间定义提供强大工具。管理员拥有精确的成员访问控制，确保简化的成员管理。动态频道管理允许有效的内容结构化，增强整体用户体验。

### 🎯 核心特性

#### 📊 内容管理
- **频道管理** - 灵活的内容频道系统，支持多种内容类型
- **条目管理** - 完整的内容生命周期管理，支持草稿、发布和状态控制
- **分类系统** - 多级分类管理，支持内容组织和归类
- **模板系统** - 可自定义的内容模板，支持动态字段配置

#### 👥 用户与权限管理
- **成员管理** - 完整的用户注册、认证和个人资料管理
- **用户组管理** - 基于角色的权限控制系统
- **内容访问控制** - 精细化的内容访问权限管理
- **团队协作** - 多用户协作环境，支持不同权限级别

#### 🎨 网站建设
- **网站管理** - 多网站支持，每个网站独立配置
- **菜单管理** - 动态菜单创建和管理
- **页面管理** - 可视化页面编辑和发布
- **SEO优化** - 内置SEO工具和优化功能

#### 📁 媒体管理
- **文件上传** - 支持图片、音频、文档等多种文件类型
- **云存储** - 集成AWS S3、Azure Blob、Google Drive等多种云存储
- **本地存储** - 本地文件系统存储支持
- **图片处理** - 自动图片压缩和尺寸调整

#### 🔧 表单构建器
- **拖拽式表单** - 可视化表单构建工具
- **自定义字段** - 支持多种字段类型和验证规则
- **表单数据管理** - 表单提交数据的收集和管理

#### 🌐 多语言支持
- **国际化** - 完整的多语言支持系统
- **语言切换** - 前端和后端语言切换
- **本地化** - 支持区域特定设置

#### 📈 仪表板与分析
- **数据统计** - 内容、用户、访问等关键指标统计
- **实时监控** - 系统状态和性能监控
- **报告生成** - 各类运营报告的生成和导出

## 🏗️ 技术架构

### 后端技术栈
- **Go语言** - 高性能的后端开发语言
- **Gin框架** - 轻量级HTTP Web框架
- **GORM** - 强大的Go语言ORM库
- **PostgreSQL/MySQL** - 关系型数据库支持

### 微服务架构
SpurtCMS采用多服务架构，同时运行三个核心服务：
1. **管理面板** (默认端口8082) - CMS管理界面
2. **模板预览** (端口8083) - 网站预览服务
3. **GraphQL API** (端口8084) - 现代化API服务

### 存储系统
- **多云存储支持** - AWS S3、Azure Blob、Google Drive
- **本地文件系统** - 本地存储选项
- **CDN集成** - 内容分发网络支持

### 安全特性
- **JWT认证** - 安全的用户身份验证
- **CSRF保护** - 跨站请求伪造防护
- **会话管理** - 安全的会话处理
- **权限控制** - 细粒度的访问权限控制

## 🚀 快速开始

### 环境要求
- Go 1.24.2 或更高版本
- PostgreSQL 或 MySQL 数据库
- Git

### 安装步骤

#### 步骤1：克隆项目
```bash
git clone https://github.com/spurtcms/spurtcms.git
cd spurtcms
```

#### 步骤2：数据库配置
创建 `.env` 文件并配置数据库连接：

```bash
# 数据库配置 (支持 postgres, mysql)
DATABASE_TYPE=postgres
DB_HOST=localhost
DB_PORT=5432
DB_USERNAME=your_username
DB_PASSWORD=your_password
DB_NAME=your_database_name
DB_SSL_MODE=disable
```

#### 步骤3：云存储配置 (可选)
如果需要使用云存储功能，请配置以下环境变量：

```bash
# AWS S3 配置
AWS_ACCESS_KEY_ID=your-access-key-id
AWS_SECRET_ACCESS_KEY=your-secret-access-key
AWS_DEFAULT_REGION=your-region
AWS_BUCKET_NAME=your-bucket-name
```

#### 步骤4：启动应用
```bash
go run main.go
```

应用启动后，会自动在浏览器中打开默认网站模板。

访问管理面板：
```
http://localhost:8082/admin
```

默认登录凭据：
- 用户名：`Admin`
- 密码：`Admin@123`

## 📚 API文档

### RESTful API
SpurtCMS提供完整的RESTful API，支持所有CMS功能的编程访问。

### GraphQL API
现代化的GraphQL API，提供灵活的数据查询和操作能力。

### API认证
所有API请求都需要通过JWT令牌进行认证。

## 🔧 开发指南

### 开发环境搭建
1. 安装Go开发环境
2. 配置数据库连接
3. 克隆项目并安装依赖
4. 运行 `go run main.go` 启动开发服务器

### 项目结构
```
spurtcms/
├── controllers/          # 控制器层
├── models/              # 数据模型
├── routes/              # 路由配置
├── middleware/          # 中间件
├── config/              # 配置文件
├── migration/           # 数据库迁移
├── graphql/             # GraphQL相关
├── storage-controller/   # 存储控制器
├── websites/            # 网站前端
├── page-view/           # 页面视图
├── public/              # 静态资源
├── view/                # 视图模板
├── locales/             # 本地化文件
└── storage/             # 本地存储
```

### 构建和部署
```bash
# 开发模式运行
make run

# 构建Linux版本
make build

# 构建包含视图文件的完整版本
make buildwithview

# 启动系统服务
sudo ./spurtcms.sh start

# 停止系统服务
sudo ./spurtcms.sh stop
```

## 🧪 测试
```bash
# 运行所有测试
go test

# 运行特定测试
go test -run TestSetupRouting
```

## 🌐 功能模块详解

### 1. 仪表板 (Dashboard)
- 系统概览和关键指标展示
- 最新内容、用户和活动统计
- 快速操作入口

### 2. 内容管理 (Content Management)
- **频道管理** - 创建和管理不同类型的内容频道
- **条目管理** - 内容的创建、编辑、发布和管理
- **分类管理** - 内容分类的层级管理
- **模板管理** - 可自定义的内容模板

### 3. 用户管理 (User Management)
- **成员管理** - 用户注册、认证和个人资料
- **用户组管理** - 基于角色的权限分组
- **权限管理** - 细粒度的功能权限控制

### 4. 网站管理 (Website Management)
- **多网站支持** - 管理多个独立网站
- **菜单管理** - 动态导航菜单创建
- **页面管理** - 可视化页面编辑
- **SEO设置** - 搜索引擎优化配置

### 5. 媒体库 (Media Library)
- **文件管理** - 文件上传、组织和删除
- **图片处理** - 自动压缩和尺寸调整
- **云存储集成** - 多种云存储服务支持

### 6. 表单构建器 (Form Builder)
- **可视化构建** - 拖拽式表单设计
- **字段类型** - 支持多种输入字段类型
- **数据收集** - 表单提交数据的收集和分析

### 7. 系统设置 (System Settings)
- **基本设置** - 系统基本配置
- **邮件配置** - SMTP邮件服务设置
- **语言设置** - 多语言环境配置
- **个性化设置** - 界面和功能定制

## 🤝 贡献指南

我们欢迎社区贡献！请遵循以下步骤：

1. Fork 项目
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

## 📞 支持与帮助

### 获取帮助
- **官方文档**: [https://spurtcms.com/documentation](https://spurtcms.com/documentation)
- **Discord社区**: [https://discord.com/invite/9TNgqUY24N](https://discord.com/invite/9TNgqUY24N)
- **视频教程**: [YouTube频道](https://www.youtube.com/@spurtcms/videos)
- **技术支持**: [Piccosoft Support](https://picco.support)

### 报告问题
如果您发现错误，请[提交详细问题](https://github.com/spurtcms/spurtcms-admin/issues/new)。

## 📄 许可证

SpurtCMS 采用 [BSD-3-Clause 许可证](https://github.com/spurtcms/spurtcms/blob/master/LICENSE)。

## 👨‍💻 维护者

SpurtCMS 由 [Piccosoft Software Labs India (P) Limited](https://www.piccosoft.com) 开发和维护。

---

<p align="center">
  <strong>感谢使用 SpurtCMS！🎉</strong>
</p>