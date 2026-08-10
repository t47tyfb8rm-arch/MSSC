# MSSC

美食收藏系统，手机端优先的纯静态部署版本。

## 功能

- 首页编号列表展示收藏店铺
- 搜索店名、地址、来源、必吃菜
- 分类筛选
- 店铺详情页展示必吃菜单、地址、地图预览
- 新增、编辑、删除收藏
- 数据保存到当前浏览器 `localStorage`

## 本地运行

```bash
python3 -m http.server 8005
```

访问：

```text
http://127.0.0.1:8005/
```

## 服务器部署

推荐目录：

```text
/opt/MSSC
```

启动命令：

```bash
cd /opt/MSSC
nohup python3 -m http.server 8005 > server.log 2>&1 &
```

公网访问：

```text
http://服务器IP:8005/
```

## GitHub

仓库：

```text
https://github.com/t47tyfb8rm-arch/MSSC.git
```

注意：`GITHUB/github1.md` 是本地 token 文件，已加入 `.gitignore`，不要提交。
