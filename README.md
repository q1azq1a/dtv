# dtv

自动镜像 IPTV 播放列表与电子节目单（EPG），由 GitHub Actions 每 8 小时更新一次
（北京时间 01:00 / 09:00 / 17:00），每次更新后自动清理 CDN 缓存。

## 订阅地址（推荐：jsDelivr CDN，国内可直连）

| 文件 | 地址 |
|---|---|
| playlist.m3u | https://gcore.jsdelivr.net/gh/q1azq1a/dtv@main/playlist.m3u |
| epg.xml.gz | https://gcore.jsdelivr.net/gh/q1azq1a/dtv@main/epg.xml.gz |

备用域名（路径不变）：`cdn.jsdelivr.net`，如
https://cdn.jsdelivr.net/gh/q1azq1a/dtv@main/playlist.m3u

## 其他地址

| 渠道 | playlist.m3u | epg.xml.gz |
|---|---|---|
| GitHub Raw | https://raw.githubusercontent.com/q1azq1a/dtv/main/playlist.m3u | https://raw.githubusercontent.com/q1azq1a/dtv/main/epg.xml.gz |
| Gitee Raw | https://gitee.com/danfengdd/dtv/raw/main/playlist.m3u （注：Gitee 内容审核会拦截此文件，返回 451，一般不可用） | https://gitee.com/danfengdd/dtv/raw/main/epg.xml.gz |
| 源站 | https://iptv.yang-1989.xyz/playlist.m3u | https://iptv.yang-1989.xyz/epg.xml.gz |

Gitee 仓库（镜像）：https://gitee.com/danfengdd/dtv

## 更新机制

- 工作流：`.github/workflows/update.yml`
- 触发：定时（cron `0 1,9,17 * * *`，UTC）+ 可在 Actions 页手动触发
- 每次运行下载最新文件并做完整性校验（m3u 标记、gzip 合法性），有变化才提交，
  提交后请求清理 jsDelivr 缓存，保证 CDN 拿到的是最新版。
