# The Blog Of Mr.Kuang — Hexo + Butterfly

重建自原静态站，源文件可维护。

## 本地

```powershell
npm install
npx hexo server
```

打开 http://localhost:4000。

## 写文章

```powershell
npx hexo new "文章标题"
```

文章在 `source/_posts/`。目前没有文章；首页是 `source/index.md` 的欢迎页。
如果想让首页显示文章列表，删除 `source/index.md`。

## 构建

```powershell
npx hexo clean
npx hexo generate
```

产物在 `public/`。

## 部署

把 `public/` 同步到阿里云 `/var/www/blog`：

```powershell
tar -C public -czf deploy.tar.gz .
scp -P 22 -i ..\deepseektowechat\secrets\aliyun_being deploy.tar.gz root@47.112.202.19:/root/blog-build.tar.gz
ssh -p 22 -i ..\deepseektowechat\secrets\aliyun_being root@47.112.202.19 "find /var/www/blog -mindepth 1 -delete && tar -xzf /root/blog-build.tar.gz -C /var/www/blog && chown -R www-data:www-data /var/www/blog && systemctl reload nginx"
```

## 备案号

在 `_config.butterfly.yml` 的 `footer.custom_text`，已包含警徽 SVG 和 `渝ICP备2025050714号`。
重新构建不会丢。
