# 项目说明

本项目是一个简约的个人主页，基于 Vite 构建，使用 Vite 和 MDUI。萌新第一个前端应用~！

## config.json 配置

`public/config.json` 文件用于配置应用的内容和主题。以下是该文件的结构和各个字段的说明：

```json
{
  "name": "你的名字",
  "avatar": "头像图片的 URL",
  "email": "你的邮箱",
  "description": "个人简介",
  "links": [
    {
      "name": "链接名称",
      "url": "链接地址",
      "icon": "链接图标的 URL"
    }
  ],
  "projects": [
    {
      "name": "项目名称",
      "url": "项目地址",
      "img": "项目图片的 URL",
      "description": "项目描述"
    }
  ],
  "theme": "auto",
  "footer": "页脚内容"
}
```

### 字段说明

- `name`：用户的名字，将在应用中显示。
- `avatar`：用户头像的 URL，建议使用网络可访问的图片链接。
- `email`：用户的邮箱地址，点击后可直接发送邮件。
- `description`：用户的个人简介，将在应用中展示。
- `links`：一个数组，包含多个链接对象，每个对象包含：
  - `name`：链接的名称。
  - `url`：链接的地址。
  - `icon`：链接图标的 URL。
- `projects`：一个数组，包含多个项目对象，每个对象包含：
  - `name`：项目名称。
  - `url`：项目地址。
  - `img`：项目图片的 URL。
  - `description`：项目描述。
- `theme`：应用的主题色调，支持 "auto"（自动，根据头像去色），16 进制颜色码。
- `footer`：应用底部的自定义内容，可以是 HTML 字符串。

## 使用说明

1. 修改配置文件

2. 安装依赖

   ```bash
   npm install
   ```

3. 启动开发服务器

   ```bash
    npm run dev
   ```

4. 构建应用

   ```bash
   npm run build
   ```

5. 部署

   将 `dist` 目录下的文件部署到你的服务器上即可。
