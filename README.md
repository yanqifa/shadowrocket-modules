# Shadowrocket 模块

## Spotify 直连

将 Spotify 的服务、登录、图片、音频及专用 CDN 域名设为 `DIRECT`，减少播放流量绕行代理/VPS。

**模块地址（复制到小火箭）：**

```text
https://raw.githubusercontent.com/yanqifa/shadowrocket-modules/main/Spotify-Direct.sgmodule
```

[在支持的设备上一键导入](shadowrocket://install?module=https%3A%2F%2Fraw.githubusercontent.com%2Fyanqifa%2Fshadowrocket-modules%2Fmain%2FSpotify-Direct.sgmodule)

### 使用

1. 小火箭 → 配置 → 模块 → 右上角 `+`，粘贴模块地址并下载。
2. 启用「Spotify 直连」，首页的「全局路由」选择 **配置**。
3. 重新连接小火箭，再彻底退出并重新打开 Spotify，使已有连接重新建立。
4. 播放一首未缓存的歌曲，在小火箭「数据 → 代理日志」检查 Spotify 域名请求的策略是否为 `DIRECT`；已有离线缓存不能用于验证网络分流。

模块规则的优先级高于主配置。如其他模块也匹配 Spotify，请调整顺序，使本模块的规则优先匹配。此模块只包含 29 条域名规则，无需 HTTPS 解密、证书或脚本，也不依赖外部规则集下载。

### 范围与限制

- 直连是否可用取决于当前运营商、网络、账号和服务状态；本模块未在你的 iPhone 或蜂窝网络上实测。
- 这是分流模块，不修改 Spotify 会员、账号地区或广告机制，无法保证无广告。
- 域名表是静态快照，整理日期为 2026-10-24。未来若出现新域名，需更新模块。
- 仅匹配列出的域名及相应子域名，不使用 `DOMAIN-KEYWORD,spotify`、共享 CDN 整站域名或固定共享 IP，以减少误分流。第三方登录、外部播客托管等其他域名沿用原配置。
- DNS 设置沿用当前配置。若上游路由器另有 VPN，`DIRECT` 仅表示绕过本机小火箭代理，不能改变上游路由。
- 如直连导致登录或播放失败，可禁用本模块并重新连接，恢复原有分流。

### 来源

域名参考以下项目，保留来源并对规则作了筛选、合并和 `DIRECT` 策略适配：

- [blackmatrix7/ios_rule_script：Spotify](https://github.com/blackmatrix7/ios_rule_script/blob/master/rule/Shadowrocket/Spotify/Spotify.list)（GPL-2.0）
- [v2fly/domain-list-community：Spotify](https://github.com/v2fly/domain-list-community/blob/master/data/spotify)（MIT）
- [Shadowrocket 社区使用手册：模块](https://github.com/LOWERTOP/Shadowrocket#模块)

本仓库模块按 [GPL-2.0](LICENSE) 提供，属于上述域名规则的适配版本。Spotify 与 Shadowrocket 商标属于各自所有者。
