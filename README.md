# My Download Rules

供 Mihomo 使用的海外下载端点规则集，覆盖应用商店、软件更新、软件包仓库和国际游戏下载 CDN。

`my-overseas-download.yaml` 是规则清单的维护入口。通过 `main` 分支的固定文件地址订阅，客户端可定期拉取更新。

清单优先收录可确认用于文件传输的端点和专用软件镜像。共用的网页、API、索引、鉴权、流媒体 CDN 和通用代理服务遵循主配置的其他规则。

```yaml
rule-providers:
  overseas-download:
    type: http
    behavior: classical
    format: yaml
    url: https://raw.githubusercontent.com/szcorsair/my-download-rules/main/my-overseas-download.yaml
    path: ./ruleset/my-overseas-download.yaml
    interval: 86400
```

在主配置中用 `RULE-SET,overseas-download,RACK-DOWNLOAD` 指定出口。规则顺序为国内下载例外优先，其次是本清单，然后是 Google 和通用国内外分流。

游戏 CDN 条目参考 [v2fly domain-list-community](https://github.com/v2fly/domain-list-community)，上游版权与许可见 [NOTICE-v2fly.txt](NOTICE-v2fly.txt)。
