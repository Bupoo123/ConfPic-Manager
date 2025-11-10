# EmailJS 配置说明

## 📧 邮件发送功能配置指南

本工具使用 EmailJS 服务来发送邮件，这是一个免费的前端邮件发送服务。

## 🔧 配置步骤

### 1. 注册 EmailJS 账号

1. 访问 [EmailJS官网](https://www.emailjs.com/)
2. 点击 "Sign Up" 注册免费账号
3. 登录后进入 Dashboard

### 2. 添加邮件服务

1. 在 Dashboard 中点击 "Add New Service"
2. 选择您的邮件服务提供商（Gmail、Outlook等）或选择 "Custom SMTP Server"
3. 按照提示完成服务配置
4. 记录下 **Service ID**（例如：`service_xxxxx`）

### 3. 创建邮件模板

1. 在 Dashboard 中点击 "Email Templates" → "Create New Template"
2. 设置模板名称（例如：`ppt_report`）
3. 在模板中配置以下变量：
   - `{{to_email}}}` - 收件人邮箱
   - `{{subject}}` - 邮件主题
   - `{{message}}` - Markdown格式内容
   - `{{html_content}}` - HTML格式内容（可选）
   - `{{total_images}}` - 图片总数

4. 模板示例：
```
收件人：{{to_email}}
主题：{{subject}}

{{message}}

---
HTML版本内容：
{{html_content}}
```

5. 记录下 **Template ID**（例如：`template_xxxxx`）

### 4. 获取 Public Key

1. 在 Dashboard 中点击 "Account" → "General"
2. 找到 "Public Key"
3. 复制 **Public Key**（例如：`xxxxxxxxxxxxx`）

### 5. 在代码中配置

打开 `index.html` 文件，找到以下代码：

```javascript
const EMAILJS_CONFIG = {
    serviceId: 'YOUR_SERVICE_ID',      // 替换为您的 Service ID
    templateId: 'YOUR_TEMPLATE_ID',    // 替换为您的 Template ID
    publicKey: 'YOUR_PUBLIC_KEY'       // 替换为您的 Public Key
};
```

将 `YOUR_SERVICE_ID`、`YOUR_TEMPLATE_ID` 和 `YOUR_PUBLIC_KEY` 替换为您实际的值。

## 📝 使用说明

1. 上传照片并生成HTML报告
2. 点击 "发送到邮箱" 按钮
3. 系统会自动将内容转换为Markdown格式并发送到配置的邮箱

## ⚠️ 注意事项

- EmailJS 免费版每月有发送限制（200封邮件）
- 确保模板中的变量名称与代码中的 `templateParams` 匹配
- 如果发送失败，请检查浏览器控制台的错误信息

## 🔒 安全提示

- **不要**将包含真实密钥的代码提交到公开的GitHub仓库
- 建议使用环境变量或配置文件来存储敏感信息
- EmailJS的Public Key是公开的，但Service ID和Template ID建议保密

