# my-project
好的，以下是完整的README.md文件，使用Markdown格式：

```markdown
# 📚 图书馆管理系统 (Library Management System)

一个基于Java Web的完整图书管理系统，支持图书管理、借阅归还、用户管理等核心功能。

![Java](https://img.shields.io/badge/Java-1.8-orange)
![JSP](https://img.shields.io/badge/JSP-2.3-blue)
![MySQL](https://img.shields.io/badge/MySQL-8.0-lightblue)
![Tomcat](https://img.shields.io/badge/Tomcat-8.0-red)
![License](https://img.shields.io/badge/License-MIT-green)

## ✨ 功能特性

### 📖 核心功能
- ✅ **用户管理**：管理员/普通用户分级权限系统
- ✅ **图书管理**：完整的图书增删改查(CRUD)功能
- ✅ **借阅系统**：借书、还书、库存实时更新
- ✅ **智能搜索**：支持书名、作者、ISBN多条件检索
- ✅ **数据统计**：实时图书借阅情况可视化展示

### 👥 用户角色
| 角色 | 权限 | 功能 |
|------|------|------|
| **管理员** | 所有权限 | 图书管理、用户管理、数据统计 |
| **普通用户** | 基础权限 | 图书查询、借阅、归还 |

### 📊 技术亮点
- 响应式网页设计，适配各种设备
- 数据库连接池优化，提高性能
- 统一编码过滤器(UTF-8)
- 安全的用户认证机制

## 🛠 技术栈

**后端技术**
- Java 1.8
- JSP/Servlet
- JDBC
- MySQL 8.0

**前端技术**
- HTML5/CSS3
- JavaScript
- Font Awesome 图标库
- 响应式布局设计

**服务器**
- Apache Tomcat 8.0
- Maven（可选）

## 📁 项目结构

```
LibraryManagementSystem/
├── src/                            # Java源代码
│   └── com/library/                # 核心包
│       ├── Book.java               # 图书实体类
│       ├── BookDAO.java            # 图书数据访问对象
│       ├── User.java               # 用户实体类
│       ├── UserDAO.java            # 用户数据访问对象
│       ├── DBUtil.java             # 数据库工具类
│       ├── MainServlet.java        # 主控制器
│       └── EncodingFilter.java     # 编码过滤器
├── WebContent/                     # Web资源
│   ├── css/
│   │   └── style.css              # 样式文件
│   ├── js/                        # JavaScript文件
│   ├── WEB-INF/
│   │   ├── lib/                   # 依赖库
│   │   │   ├── mysql-connector-j-8.0.33.jar
│   │   │   └── jstl-1.2.jar
│   │   └── web.xml                # 配置文件
│   ├── login.jsp                  # 登录页面
│   ├── register.jsp               # 注册页面
│   ├── index.jsp                  # 主页
│   └── add_book.jsp               # 添加图书页面
├── .classpath                     # Eclipse项目配置
├── .project                       # Eclipse项目文件
└── README.md                      # 项目说明文档
```

## 🚀 快速开始

### 环境要求
- JDK 1.8+
- MySQL 8.0+
- Apache Tomcat 8.0+
- Eclipse IDE（推荐）

### 安装步骤

1. **克隆项目**
```bash
git clone https://github.com/doudou185123/my-project.git
cd my-project
```

2. **导入数据库**
```sql
-- 创建数据库
CREATE DATABASE library_db CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
USE library_db;

-- 创建用户表
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL UNIQUE,
    password VARCHAR(100) NOT NULL,
    name VARCHAR(100) NOT NULL,
    type ENUM('ADMIN', 'USER') DEFAULT 'USER',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 创建图书表
CREATE TABLE books (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(200) NOT NULL,
    author VARCHAR(100) NOT NULL,
    isbn VARCHAR(20),
    category VARCHAR(50),
    total INT DEFAULT 1,
    available INT DEFAULT 1,
    location VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 插入默认用户
INSERT INTO users (username, password, name, type) VALUES 
('admin', 'admin123', '系统管理员', 'ADMIN'),
('user', 'user123', '普通用户', 'USER');
```

3. **配置数据库连接**
修改 `src/com/library/DBUtil.java`：
```java
private static final String USER = "root";          // 你的数据库用户名
private static final String PASSWORD = "123456";    // 你的数据库密码
```

4. **部署到Tomcat**
- 将项目导入Eclipse
- 配置Tomcat服务器
- 启动Tomcat服务

5. **访问应用**
```
http://localhost:8080/LibraryManagementSystem/
```

## 📱 使用说明

### 默认账号
- **管理员**: admin / admin123
- **普通用户**: user / user123

### 主要操作
1. **登录系统**：输入用户名和密码登录
2. **查看图书**：首页显示所有图书列表
3. **搜索图书**：使用顶部搜索框快速查找
4. **借阅图书**：点击图书旁的"借阅"按钮
5. **归还图书**：点击"归还"按钮完成归还
6. **添加图书**（管理员）：通过导航栏进入添加页面

## 🔧 故障排除

### 常见问题

| 问题 | 解决方案 |
|------|----------|
| 数据库连接失败 | 检查MySQL服务是否启动，用户名密码是否正确 |
| 页面乱码 | 确认数据库和Java文件都是UTF-8编码 |
| Tomcat启动失败 | 检查端口是否被占用，清理Tomcat工作目录 |
| 找不到驱动类 | 确保mysql-connector-java.jar在WEB-INF/lib目录 |

### 日志查看
```bash
# Tomcat日志位置
tomcat/logs/catalina.out
tomcat/logs/localhost.log

# Eclipse控制台
Window → Show View → Console
```

## 📈 项目截图

> 注：此处可以添加项目运行截图

```
登录页面 → 图书列表 → 添加图书 → 搜索功能
```

## 🤝 贡献指南

1. Fork 本仓库
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 📞 联系方式

- **项目作者**: doudou185123
- **GitHub**: [@doudou185123](https://github.com/doudou185123)
- **问题反馈**: [Issues](https://github.com/doudou185123/my-project/issues)

## 🌟 致谢

感谢以下开源项目：
- [Font Awesome](https://fontawesome.com/) - 图标库
- [MySQL](https://www.mysql.com/) - 数据库
- [Apache Tomcat](http://tomcat.apache.org/) - Web服务器

---

**⭐ 如果这个项目对你有帮助，请给我们一个Star！**

_最后更新: 2026年1月4日_
```

## 📋 使用方法

1. 在你的GitHub仓库中，点击 **Add file** → **Create new file**
2. 文件名输入 `README.md`
3. 将上面的代码复制到编辑器中
4. 点击 **Commit changes**

## 🎨 可选的自定义

你可以根据需要修改以下部分：

1. **添加项目截图**：
```markdown
## 📸 项目截图

![登录页面](screenshots/login.png)
![图书列表](screenshots/books.png)
![添加图书](screenshots/add-book.png)
```

2. **添加更多徽章**：
```markdown
![Build Status](https://img.shields.io/badge/build-passing-brightgreen)
![Code Size](https://img.shields.io/github/languages/code-size/doudou185123/my-project)
```

3. **添加部署说明**：
```markdown
## 🌐 在线演示
[点击这里访问在线演示](https://your-demo-url.com)
```

这个README包含了：
- 美观的徽章和图标
- 清晰的项目结构
- 详细的安装步骤
- 使用说明
- 故障排除指南
- 贡献指南
- 联系方式

你需要根据实际情况修改：
- 数据库连接信息
- 项目名称（如果需要）
- 联系方式
- 添加实际的项目截图
