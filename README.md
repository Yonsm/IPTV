<h1 align="center">IPTV</h1>

<p align="center">IPTV 直播源、频道图标与 Nginx 转发配置</p>

<p align="center">
  <a href="iptv.htm">网页播放</a>
  · <a href="https://github.com/Yonsm/IPTV/issues">问题反馈</a>
</p>

## 播放源

在播放器中添加订阅地址：

| 类型 | 地址 | 最近更新 |
| --- | --- | --- |
| 来源列表（Televe） | `https://yonsm.github.io/IPTV/lists.m3u8` | 2026-11-05 |
| 公网频道 | `https://yonsm.github.io/IPTV/iptv.m3u8` | 2026-11-05 |

地区源：[杭州](hangzhou/) · [江西](jiangxi/) · [上海](shanghai/) · [苏州](suzhou/)。不支持来源列表的播放器，请直接导入对应的频道列表。

| 地区频道列表 | 最近更新 |
| --- | --- |
| [杭州联通](hangzhou/unicom.m3u8) | 2026-11-05 |
| [江西移动](jiangxi/mobile.m3u8) | 2026-11-05 |
| [杭州电信](hangzhou/telecom.m3u8)、[杭州移动](hangzhou/mobile.m3u8) | 2023-01-06 |
| [江西电信](jiangxi/telecom.m3u8) | 2023-01-03 |
| [上海联通](shanghai/unicom.m3u8) | 2022-11-19 |
| [上海电信](shanghai/telecom.m3u8)、[苏州移动](suzhou/mobile.m3u8) | 2020-02-15 |

更新日期以各 M3U8 文件的最近 Git 提交为准，不代表频道可用性验证日期；后续变更可查看各文件的提交历史。

频道能否播放取决于地区、运营商与网络环境；内网源需在对应网络中使用。请仅使用有权访问的来源。

## 推荐播放器

**Android 推荐 [Televe](https://github.com/Yonsm/Televe)，iOS 推荐 [APTV](https://apps.apple.com/app/id1630403500)。**

| 平台 | 播放器 | 说明 |
| --- | --- | --- |
| Android | [Televe](https://github.com/Yonsm/Televe) · [下载 APK](https://github.com/Yonsm/Televe/releases/latest) | 支持手机、平板与电视，遥控器和触屏操作，多源切换、数字选台与播放记忆 |
| iOS | [APTV](https://apps.apple.com/app/id1630403500) | 导入 M3U 频道列表观看直播 |

## Nginx 公网转发

仓库提供 [nginx/iptv.conf](nginx/iptv.conf) 配置文件，支持代理杭州联通与江西移动直播源。

## 其它资源

[频道图标](LOGO/) · [在线节目单（XMLTV）](https://live.fanmingming.cn/e.xml) · [APTV 源集合](https://github.com/Kimentanm/aptv)
