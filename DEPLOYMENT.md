# LikeGirl v5.2.0 部署指南

---

## 环境要求

| 组件 | 要求 |
|------|------|
| Web服务器 | Nginx 或 Apache |
| PHP版本 | 7.0 或更高版本 |
| 数据库 | MySQL 5.5 或更高版本 |
| 其他 | PHP需要开启 mysqli 扩展 |

---

## 部署步骤

### 步骤 1：准备环境

**本地开发环境推荐：**
- **phpStudy** / **XAMPP** / **WampServer** 等集成环境
- 或者使用 **Docker**

**生产环境推荐：**
- 云服务器（阿里云、腾讯云等）+ LNMP/LAMP 环境

### 步骤 2：配置数据库

1. **创建数据库**
   - 登录 MySQL 数据库管理工具（phpMyAdmin、Navicat 等）
   - 创建一个新数据库，例如命名为 `likegirl`

2. **导入数据库文件**
   
   根据需求选择以下其中一个 SQL 文件导入：
   
   - `LikeGirl v5.2.0 AllData.sql` - 包含默认数据（推荐新手使用）
   - `LikeGirl v5.2.0 Purity.sql` - 纯净版（无默认数据）

   **导入方法：**
   ```sql
   -- 使用命令行导入
   mysql -u用户名 -p密码 数据库名 < "LikeGirl v5.2.0 AllData.sql"
   ```
   或者在 phpMyAdmin 中通过"导入"功能导入 SQL 文件。

### 步骤 3：修改数据库配置

打开文件：[admin/Config_DB.php](file:///d:/第一个游戏/like-girl-v5.2.0-master/like-girl-v5.2.0-master/admin/Config_DB.php)

修改以下配置项：

```php
//数据库地址
$db_address = "localhost";        // 一般保持不变

//数据库用户名
$db_username = "你的数据库用户名";  // 修改为实际用户名

//数据库密码
$db_password = "你的数据库密码";    // 修改为实际密码

//数据库名称
$db_name = "你创建的数据库名";      // 修改为你创建的数据库名

//设置安全码（必须修改！）
$Like_Code = "设置一个复杂的安全码"; // 修改为自定义安全码
```

**⚠️ 重要提醒：**
- 请务必修改安全码 `$Like_Code`，使用复杂且难以猜测的字符组合
- 安全码用于修改密码等敏感操作，请妥善保管

### 步骤 4：上传文件到服务器

将项目所有文件上传到 Web 服务器的网站根目录或子目录。

**目录结构应类似：**
```
网站根目录/
├── index.php
├── about.php
├── leaving.php
├── little.php
├── loveImg.php
├── list.php
├── page.php
├── admin/
│   ├── Config_DB.php
│   └── ...
├── Style/
└── Botui/
```

### 步骤 5：访问网站

1. 在浏览器中访问您的网站地址
2. 后台管理地址：`http://您的域名/admin/`
3. 默认管理员账号：`admin`
4. 默认管理员密码：`loveww`

**⚠️ 首次登录后请立即修改默认密码！**

---

## 本地开发部署（Windows）

### 使用 phpStudy 部署

1. 下载并安装 phpStudy
2. 启动 Apache/Nginx 和 MySQL 服务
3. 将项目文件复制到 phpStudy 的 `WWW` 目录下
4. 按照上面的步骤 2-3 配置数据库
5. 浏览器访问 `http://localhost/项目目录`

### 使用 XAMPP 部署

1. 下载并安装 XAMPP
2. 启动 Apache 和 MySQL 服务
3. 将项目文件复制到 `htdocs` 目录下
4. 按照上面的步骤 2-3 配置数据库
5. 浏览器访问 `http://localhost/项目目录`

---

## 常见问题

### Q：出现数据库连接失败怎么办？

A：请检查：
1. `admin/Config_DB.php` 中的数据库配置是否正确
2. MySQL 服务是否已启动
3. 数据库用户是否有足够的权限

### Q：页面显示乱码怎么办？

A：请确保：
1. 数据库使用 `utf8mb4` 或 `utf8` 字符集
2. 导入的 SQL 文件编码为 UTF-8

### Q：如何修改网站基本信息？

A：登录后台管理系统，在系统设置中修改：
- 网站标题
- 情侣昵称
- 恋爱时间
- 背景图片
- 等其他配置信息

### Q：QQ头像和昵称获取失败？

A：这是由于第三方API变更导致的。可以：
- 使用后台手动修改
- 或自行更换为其他可用的QQ信息API

---

## 安全建议

1. **修改默认密码** - 首次登录后立即修改管理员密码
2. **设置复杂安全码** - 在 `Config_DB.php` 中设置强密码
3. **定期备份数据库** - 防止数据丢失
4. **配置HTTPS** - 如果在公网部署，建议配置SSL证书
5. **限制后台访问** - 可以通过IP白名单等方式限制后台访问

---

## 项目文件说明

| 文件/目录 | 说明 |
|-----------|------|
| index.php | 首页 |
| little.php | 点点滴滴 |
| leaving.php | 留言祝福 |
| loveImg.php | 恋爱相册 |
| list.php | 恋爱列表 |
| about.php | 关于我们 |
| page.php | 文章详情页 |
| admin/ | 后台管理目录 |
| Style/ | 样式和资源文件 |
| Botui/ | 聊天机器人组件 |

---

## 技术支持

如遇到问题，请参考：
- 原作者博客：https://blog.kikiw.cn/index.php/archives/52/
- 演示站：https://lovey.kikiw.cn

---

**文档版本**：v1.0  
**创建日期**：2026-05-18  
**项目名称**：LikeGirl v5.2.0