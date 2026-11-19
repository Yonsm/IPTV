# [IPTV](https://yonsm.github.io/IPTV/)

IPTV 直播源、频道图标与 Nginx 转发配置。

[网页播放](iptv.htm) · [问题反馈](https://github.com/Yonsm/IPTV/issues)

网页播放推荐使用 **Safari**，其原生 HLS 支持较好；**Chrome** 通过 hls.js 播放，可能受直播源跨域配置、音视频编码等限制。HTTPS 页面中的 HTTP 直播源还可能被浏览器拦截，无法播放时建议使用独立播放器。

## 播放源

在播放器中添加订阅地址：

| 类型 | 地址 | 最近更新 |
| --- | --- | --- |
| 来源列表（Televe） | `https://yonsm.github.io/IPTV/lists.m3u8` | 2026-11-19 |
| 公网频道 | `https://yonsm.github.io/IPTV/iptv.m3u8` | 2026-11-05 |

地区源：[杭州](hangzhou/) · [江西](jiangxi/) · [上海](shanghai/) · [苏州](suzhou/)；[在线源](online/)汇集公开直播地址及运营商网络来源，公共频道指向其中的快活直播。在线源最近一次连通性与台标扫描：2026-11-17，部分频道未能确认。不支持来源列表的播放器，请直接导入对应的频道列表。组播列表统一以 `*2.m3u8` 命名，来源列表中的名称以「组」结尾；组播需路由器转发或 udpxy。上海电信分单播与组播两份：`telecom.m3u8` 为单播回放地址，`telecom2.m3u8` 为组播地址，均需在上海电信 IPTV 网络中使用。

| 地区频道列表 | 最近更新 |
| --- | --- |
| [杭州联通](hangzhou/unicom.m3u8) | 2026-11-05 |
| [江西移动](jiangxi/mobile.m3u8) | 2026-11-05 |
| [杭州电信](hangzhou/telecom.m3u8)、[杭州移动](hangzhou/mobile.m3u8) | 2023-01-06 |
| [江西电信](jiangxi/telecom.m3u8) | 2023-01-03 |
| [上海联通](shanghai/unicom.m3u8) | 2026-11-12 |
| [上海联通组](shanghai/unicom2.m3u8)（组播） | 2026-11-19 |
| [上海移动](shanghai/mobile.m3u8) | 2026-11-19 |
| [上海电信](shanghai/telecom.m3u8)（单播） | 2026-11-19 |
| [上海电信组](shanghai/telecom2.m3u8)（组播） | 2026-11-19 |
| [苏州移动](suzhou/mobile.m3u8) | 2020-02-15 |

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

## 台标与图标

| 资源 | 目录 | 示例 |
| --- | --- | --- |
| JPG 台标 | [logo/](logo/) | [CCTV1](logo/CCTV1.jpg) · [央视综合](logo/央视综合.jpg) · [湖南卫视](logo/湖南卫视.jpg) |
| PNG 图标 | [icon/](icon/) | [CCTV1](icon/CCTV1.png) · [央视综合](icon/央视综合.png) · [湖南卫视](icon/湖南卫视.png) |

可通过 `https://yonsm.github.io/IPTV/logo/频道名.jpg` 或 `https://yonsm.github.io/IPTV/icon/频道名.png` 引用，文件名以目录为准。

## 其它资源

[在线节目单（XMLTV）](https://live.fanmingming.cn/e.xml) · [APTV 源集合](https://github.com/Kimentanm/aptv)
