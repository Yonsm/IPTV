# [IPTV](https://yonsm.github.io/IPTV/)

IPTV 直播源、频道图标与 Nginx 转发配置。源码托管于 [GitHub 仓库](https://github.com/Yonsm/IPTV)。

[网页播放](iptv.htm) · [问题反馈](https://github.com/Yonsm/IPTV/issues)

网页播放推荐使用 **Safari**，其原生 HLS 支持较好；**Chrome** 通过 hls.js 播放，可能受直播源跨域配置、音视频编码等限制。HTTPS 页面中的 HTTP 直播源还可能被浏览器拦截，无法播放时建议使用独立播放器。

## 播放源

在播放器中添加订阅地址：

| 类型 | 地址 | 最近更新 |
| --- | --- | --- |
| 来源列表（M3U8） | `https://yonsm.github.io/IPTV/lists.m3u8` | 2026-11-20 |
| 来源列表（TXT） | `https://yonsm.github.io/IPTV/lists.txt` | 2026-11-20 |
| 公网频道 | `https://yonsm.github.io/IPTV/iptv.m3u8` | 2026-11-14 |

`lists.m3u8` 与 `lists.txt` 收录相同的来源，不含组播列表；前者为 M3U 格式，后者每行「名称,地址」，只支持 TXT/CSV 的播放器可直接导入 `lists.txt`，其中的相对地址按该文件的订阅地址解析。

地区目录按 IPTV 接入网络和运营商收录频道，仅对应运营商专网可访问；[在线源](online/)为公网可访问地址，包括[公网精选](online/gwjx.m3u8)。默认公网频道表指向快活直播。在线源最近一次连通性与台标扫描：2026-11-17，部分频道未能确认。不支持来源列表的播放器，请直接导入对应的频道列表。组播列表统一以 `*2.m3u8` 命名，一般需接在光猫 IPTV 口，或在路由器上用 udpxy（更推荐 [rtp2httpd](https://github.com/stackia/rtp2httpd)）聚合为单播后使用，可在对应运营商网络内直接导入。上海电信专网分单播与组播两份：`telecom.m3u8` 为单播回放地址，`telecom2.m3u8` 为组播地址，均需在上海电信 IPTV 网络中使用。

| 地区 | 频道列表 | 更新时间 | 实测验证 |
| --- | --- | --- | --- |
| 杭州 | [杭州联通专网](hangzhou/unicom.m3u8) | 2026-11-12 | ✅ |
|  | [杭州电信组播](hangzhou/telecom2.m3u8) | 2026-11-19 |  |
|  | [杭州移动专网](hangzhou/mobile.m3u8) | 2026-11-06 |  |
| 上海 | [上海电信专网](shanghai/telecom.m3u8) | 2026-11-19 |  |
|  | [上海电信组播](shanghai/telecom2.m3u8) | 2026-11-19 |  |
|  | [上海联通专网](shanghai/unicom.m3u8) | 2026-11-11 | ✅ |
|  | [上海联通组播](shanghai/unicom2.m3u8) | 2026-11-19 |  |
|  | [上海移动专网](shanghai/mobile.m3u8) | 2026-11-19 |  |
| 江西 | [江西电信专网](jiangxi/telecom.m3u8) | 2026-11-19 |  |
|  | [江西联通专网](jiangxi/unicom.m3u8) | 2026-11-19 |  |
|  | [江西移动专网](jiangxi/mobile.m3u8) | 2026-11-14 | ✅ |
| 北京 | [北京电信组播](beijing/telecom2.m3u8) | 2026-11-19 |  |
|  | [北京联通组播](beijing/unicom2.m3u8) | 2026-11-19 |  |
|  | [北京移动组播](beijing/mobile2.m3u8) | 2026-11-19 |  |
| 广州 | [广州电信组播](guangzhou/telecom2.m3u8) | 2026-11-19 |  |
|  | [广州联通专网](guangzhou/unicom.m3u8) | 2026-11-19 |  |
| 南京 | [南京电信组播](nanjing/telecom2.m3u8) | 2026-11-19 |  |
|  | [南京联通专网](nanjing/unicom.m3u8) | 2026-11-19 |  |
|  | [南京移动专网](nanjing/mobile.m3u8) | 2026-11-19 |  |
| 宁波 | [宁波电信专网](ningbo/telecom.m3u8) | 2026-11-19 |  |
|  | [宁波电信组播](ningbo/telecom2.m3u8) | 2026-11-19 |  |
|  | [宁波联通专网](ningbo/unicom.m3u8) | 2026-11-19 |  |
| 苏州 | [苏州电信专网](suzhou/telecom.m3u8) | 2026-11-19 |  |
|  | [苏州移动专网](suzhou/mobile.m3u8) | 2026-11-19 |  |
| 无锡 | [无锡电信组播](wuxi/telecom2.m3u8) | 2026-11-19 |  |
| 深圳 | [深圳移动组播](shenzhen/mobile2.m3u8) | 2026-11-19 |  |
| 成都 | [成都电信组播](chengdu/telecom2.m3u8) | 2026-11-19 |  |
| 在线 | [在线快活直播](online/khzb.m3u8) | 2026-11-14 | ☑️ |
|  | [在线北方视窗](online/bfsc.m3u8) | 2026-11-14 | ☑️ |
|  | [在线电视大全](online/dsdq.m3u8) | 2026-11-14 | ☑️ |
|  | [在线电视精选](online/dsjx.m3u8) | 2026-11-14 | ☑️ |
|  | [在线公网精选](online/gwjx.m3u8) | 2026-11-21 | ☑️ |
|  | [在线桂移电视](online/gyds.m3u8) | 2026-11-14 | ☑️ |
|  | [在线晋电电视](online/jdds.m3u8) | 2026-11-14 | ☑️ |
|  | [在线堪城电视](online/kcds.m3u8) | 2026-11-14 | ☑️ |
|  | [在线堪城直播](online/kczb.m3u8) | 2026-11-14 | ☑️ |
|  | [在线蓝云直播](online/lyzb.m3u8) | 2026-11-14 | ☑️ |
|  | [在线粤电电视](online/ydds.m3u8) | 2026-11-14 | ☑️ |
|  | [在线粤移电视](online/yyds.m3u8) | 2026-11-14 | ☑️ |
|  | [在线直播大全](online/zbdq.m3u8) | 2026-11-14 | ☑️ |
|  | [在线智盟直播](online/zmzb.m3u8) | 2026-11-14 | ☑️ |
|  | [在线综合精选](online/zhjx.m3u8) | 2026-11-14 | ☑️ |
|  | [在线其它频道](https://raw.githubusercontent.com/Kimentanm/aptv/master/m3u/iptv.m3u) | — |  |

更新时间以各 M3U8 文件的最近 Git 提交为准，不代表频道可用性；✅ 表示已在对应运营商网络实测验证，☑️ 表示公网实测可用但加载较慢。后续变更可查看各文件的提交历史。

频道能否播放取决于地区、运营商与网络环境；专网源需在对应网络中使用。请仅使用有权访问的来源。

## 推荐播放器

**推荐 [Televe](https://github.com/Yonsm/Televe) 与 [APTV](https://apps.apple.com/app/id1630403500)，同时支持 [TVBox](https://github.com/FongMi/TV) 与 [IINA](https://iina.io/)。**

| 平台 | 播放器 | 说明 |
| --- | --- | --- |
| Android | [Televe](https://github.com/Yonsm/Televe) · [下载 APK](https://github.com/Yonsm/Televe/releases/latest) | 支持手机、平板与电视，遥控器和触屏操作，多源切换、数字选台与播放记忆 |
| iOS / iPadOS / tvOS / macOS | [APTV](https://apps.apple.com/app/id1630403500) | 导入 M3U 频道列表，支持频道分类与 EPG |
| Android / 电视盒子 | [TVBox](https://github.com/FongMi/TV) | 导入 M3U/TXT 直播源，按分组浏览 |
| macOS | [IINA](https://iina.io/) | 打开 M3U 播放列表切换频道 |

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
