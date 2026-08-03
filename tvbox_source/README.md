# 黄豆短剧 - TVBox 静态源

## 使用方法

1. 将本目录上传到任意静态托管平台（Cloudflare Pages、GitHub Pages、Nginx、Vercel 等）
2. 修改 `config.json` 和所有 json 文件中的 `.` 为你的实际域名
3. 在 TVBox 中导入配置地址：`https://你的域名/config.json`

## 目录结构

```
tvbox_source/
├── config.json          # TVBox 主配置文件
└── api/
    ├── index.json       # 分类入口
    ├── cat_1.json       # 分类1列表
    ├── cat_2.json       # 分类2列表
    ├── ...
    └── detail/          # 影片详情页
        ├── xxx.json
        └── ...
```

## 数据统计

- 总剧目数: 810 部
- 总集数: 53645 集
- 分类数: 7 个

## 分类列表

- 古装穿越: 165 部
- 其他: 318 部
- 都市情感: 112 部
- 玄幻修仙: 89 部
- 年代怀旧: 35 部
- 都市爽文: 69 部
- 悬疑惊悚: 22 部

## 注意事项

1. 所有播放链接来自原 m3u 文件，可用性不保证
2. 静态源不支持搜索功能（searchable 已设为0）
3. 如需搜索功能，需要后端支持
4. 请确保托管平台支持 HTTPS
5. 请确保托管平台配置了正确的 CORS 跨域头

## 替换域名脚本

Linux/Mac:
```bash
find . -name "*.json" -exec sed -i 's|https://your-domain.com/tvbox|https://你的域名|g' {} +
```

Windows PowerShell:
```powershell
Get-ChildItem -Recurse -Filter *.json | ForEach-Object {
    (Get-Content $_.FullName) -replace 'https://your-domain.com/tvbox', 'https://你的域名' | Set-Content $_.FullName
}
```
