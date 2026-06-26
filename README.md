# My Web App

基于 **Vue 3 + Vite** 的前端项目，配合 GitHub Actions 实现 CI/CD 自动部署。

## 本地开发

```bash
# 安装依赖
npm install

# 启动开发服务器
npm run dev
# 访问 http://localhost:5173

# 构建生产版本
npm run build

# 预览构建结果
npm run preview
```

## Docker 运行

```bash
docker build -t my-web-app .
docker run -d -p 8080:80 --name my-web-app my-web-app
# 访问 http://localhost:8080
```

## 部署流程

### 1. 初始化 Git 并推送到 GitHub

```bash
git init
git add .
git commit -m "init project with tool"
git branch -M main
git remote add origin <your-github-repo-url>
git push -u origin main
```

### 2. 配置 GitHub Secrets

在 GitHub 仓库 **Settings → Secrets and variables → Actions** 中添加：

| Secret 名称 | 说明 |
|---|---|
| `DOCKER_USERNAME` | Docker Hub 用户名 |
| `DOCKER_PASSWORD` | Docker Hub 密码或 Access Token |
| `SERVER_HOST` | 服务器 IP 或域名 |
| `SERVER_USER` | SSH 用户名（如 `root`） |
| `SERVER_SSH_KEY` | SSH 私钥内容 |

### 3. 服务器准备1

确保服务器已安装 Docker，且 SSH 密钥对应的公钥已添加到 `~/.ssh/authorized_keys`。

### 4. 自动部署

推送代码到 `main` 分支后，GitHub Actions 会自动：

1. 在 Docker 中构建 Vue 项目并打包镜像
2. 推送镜像到 Docker Hub
3. SSH 连接服务器，拉取镜像并重启容器
