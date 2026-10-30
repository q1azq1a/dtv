# dtv

自动镜像 IPTV 播放列表与电子节目单（EPG），由 GitHub Actions 每 8 小时更新一次
（北京时间 01:00 / 09:00 / 17:00）。

## Raw 下载地址

| 文件 | 来源 | Raw 地址 |
|---|---|---|
| playlist.m3u | https://iptv.yang-1989.xyz/playlist.m3u | https://raw.githubusercontent.com/q1azq1a/dtv/main/playlist.m3u |
| epg.xml.gz | https://iptv.yang-1989.xyz/epg.xml.gz | https://raw.githubusercontent.com/q1azq1a/dtv/main/epg.xml.gz |

在播放器中添加订阅时，直接使用上面的 Raw 地址即可。

## 更新机制

- 工作流：`.github/workflows/update.yml`
- 触发：定时（cron `0 1,9,17 * * *`，UTC）+ 可在 Actions 页手动触发
- 每次运行会下载最新文件，做基本完整性校验（m3u 标记、gzip 合法性），
  仅在内容有变化时才提交，避免无意义的空提交。
