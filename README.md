> [!CAUTION]
> Fork 自 https://github.com/Loyalsoldier/geoip



# 简介

本项目每天自动生成多种格式 GeoIP 文件，同时提供命令行界面（CLI）工具供用户自行定制 GeoIP 文件，包括但不限于 V2Ray `dat` 格式文件 `geoip.dat`、MaxMind `mmdb` 格式文件 `Country.mmdb`、sing-box `SRS` 格式文件、mihomo `MRS` 格式文件、Clash ruleset 和 Surge ruleset。

This project releases various formats of GeoIP files automatically every Thursday, and provides a command line interface(CLI) tool for users to customize their own GeoIP files, including but not limited to V2Ray `dat` format file `geoip.dat`, MaxMind `mmdb` format file `Country.mmdb`, sing-box `SRS` format files, mihomo `MRS` format files, Clash ruleset files and Surge ruleset files.

## 与上游项目及 IPInfo 官方 GeoIP 数据的区别

经多轮测试比照，[IPInfo Lite](https://ipinfo.io/lite) 相较于上游采用的 MaxMind 免费库，数据准确率提升显著。

本项目默认使用 [IPInfo.io Country MMDB 数据](https://github.com/fastoot/geoip-IPInfo/blob/release/country.mmdb)生成各个国家和地区的 GeoIP 文件。所有可供使用的国家和地区 geoip 类别（如 `geoip:cn`，两位英文字母表示国家和地区），请查看：[https://www.iban.com/country-codes](https://www.iban.com/country-codes)。

另外，本项目对 IPInfo.io 官方 GeoIP 数据做了修改和新增：

- 境外（非中国大陆地区）国家数据移除了 IPv6 以平衡文件体积
- 中国大陆 IPv4 地址数据融合了 [IPIP.net](https://github.com/17mon/china_ip_list/blob/master/china_ip_list.txt) 和 [Skk.moe](https://ruleset.skk.moe/Clash/ip/china_ip.txt)
- 中国大陆 IPv6 地址数据融合了 MaxMind GeoLite2 和 [@gaoyifan/china-operator-ip](https://github.com/gaoyifan/china-operator-ip/blob/ip-lists/china6.txt)
- 新增类别（方便有特殊需求的用户使用）：
  - `geoip:cloudflare`（`GEOIP,CLOUDFLARE`）
  - `geoip:cloudfront`（`GEOIP,CLOUDFRONT`）
  - `geoip:facebook`（`GEOIP,FACEBOOK`）
  - `geoip:fastly`（`GEOIP,FASTLY`）
  - `geoip:google`（`GEOIP,GOOGLE`）
  - `geoip:netflix`（`GEOIP,NETFLIX`）
  - `geoip:telegram`（`GEOIP,TELEGRAM`）
  - `geoip:twitter`（`GEOIP,TWITTER`）
  - `geoip:tor`（`GEOIP,TOR`）

## 下载地址与使用方法

本项目发布的所有 GeoIP 文件，请查看 [release 分支](https://github.com/fastoot/geoip-IPInfo/tree/release)。以下是部分格式 GeoIP 文件的下载地址：

> 如果无法访问域名 `raw.githubusercontent.com`，可以使用第二个地址 `cdn.jsdelivr.net`。
> 如果无法访问域名 `cdn.jsdelivr.net`，可以将其替换为 `fastly.jsdelivr.net`。
>
> *.sha256sum 为校验文件。

### V2Ray dat 格式文件

> 适用于 [V2Ray](https://github.com/v2fly/v2ray-core)、[Xray-core](https://github.com/XTLS/Xray-core)、[mihomo](https://github.com/MetaCubeX/mihomo/tree/Meta)、[hysteria](https://github.com/apernet/hysteria)、[Trojan-Go](https://github.com/p4gefau1t/trojan-go)。

> 此 dat 格式文件不能用于 Nginx。

- **geoip.dat**：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/geoip.dat](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/geoip.dat)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/geoip.dat](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/geoip.dat)
- **geoip.dat.sha256sum**：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/geoip.dat.sha256sum](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/geoip.dat.sha256sum)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/geoip.dat.sha256sum](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/geoip.dat.sha256sum)
- **geoip-only-cn-private.dat**（精简版 GeoIP，只包含 `geoip:cn` 和 `geoip:private`）：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/geoip-only-cn-private.dat](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/geoip-only-cn-private.dat)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/geoip-only-cn-private.dat](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/geoip-only-cn-private.dat)
- **geoip-only-cn-private.dat.sha256sum**：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/geoip-only-cn-private.dat.sha256sum](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/geoip-only-cn-private.dat.sha256sum)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/geoip-only-cn-private.dat.sha256sum](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/geoip-only-cn-private.dat.sha256sum)
- **geoip-asn.dat**（精简版 GeoIP，只包含上述新增类别）：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/geoip-asn.dat](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/geoip-asn.dat)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/geoip-asn.dat](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/geoip-asn.dat)
- **geoip-asn.dat.sha256sum**：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/geoip-asn.dat.sha256sum](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/geoip-asn.dat.sha256sum)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/geoip-asn.dat.sha256sum](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/geoip-asn.dat.sha256sum)
- **cn.dat**（精简版 GeoIP，只包含 `geoip:cn`）：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/cn.dat](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/cn.dat)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/cn.dat](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/cn.dat)
- **cn.dat.sha256sum**：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/cn.dat.sha256sum](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/cn.dat.sha256sum)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/cn.dat.sha256sum](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/cn.dat.sha256sum)
- **private.dat**（精简版 GeoIP，只包含 `geoip:private`）：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/private.dat](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/private.dat)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/private.dat](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/private.dat)
- **private.dat.sha256sum**：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/private.dat.sha256sum](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/private.dat.sha256sum)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/private.dat.sha256sum](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/private.dat.sha256sum)
- **所有国家 / 地区 / 新增类别**的 dat 格式文件，请查看本项目 `release` 分支下的 [dat 目录](https://github.com/fastoot/geoip-IPInfo/tree/release/dat)。

#### dat 格式文件使用方法

<details>
  <summary>点击查看在 <b>V2Ray</b> 和 <b>Xray-core</b> 中的使用方法</summary>
  <br/>
  <p>需要先下载 <code>.dat</code> 格式文件，并放置在程序目录内。</p>


```json
"routing": {
  "rules": [
    {
      "type": "field",
      "outboundTag": "Direct",
      "ip": [
        "geoip:cn",
        "geoip:private",
        "ext:cn.dat:cn",
        "ext:private.dat:private",
        "ext:geoip-only-cn-private.dat:cn",
        "ext:geoip-only-cn-private.dat:private"
      ]
    },
    {
      "type": "field",
      "outboundTag": "Proxy",
      "ip": [
        "geoip:us",
        "geoip:jp",
        "geoip:facebook",
        "geoip:telegram",
        "ext:geoip-asn.dat:facebook",
        "ext:geoip-asn.dat:telegram"
      ]
    }
  ]
}
```

</details>

<details>
  <summary>点击查看在 <b>mihomo</b> 中的使用方法</summary>


```yaml
geodata-mode: true
geox-url:
  geoip: "https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/geoip.dat"
```

</details>

<details>
  <summary>点击查看在 <b>hysteria</b> 中的使用方法</summary>
  <br/>
  <p>需要先下载 <code>.dat</code> 格式文件，并放置在 hysteria 程序目录内。</p>


```
direct(geoip:cn)
proxy(geoip:telegram)
proxy(geoip:us)
```

</details>

<details>
  <summary>点击查看在 <b>Trojan-Go</b> 中的使用方法</summary>
  <br/>
  <p>需要先下载 <code>.dat</code> 格式文件，并放置在 Trojan-Go 程序目录内。</p>


```json
"router": {
  "enabled": true,
  "bypass": ["geoip:cn"],
  "proxy": ["geoip:telegram", "geoip:us"],
  "block": ["geoip:jp"],
  "default_policy": "proxy",
  "geoip": "./geoip.dat"
}
```

</details>

---

### MaxMind mmdb 格式文件

MaxMind 官方版**国家/地区**类型 mmdb 文件：

> 适用于 [Clash](https://github.com/Dreamacro/clash)、[mihomo](https://github.com/MetaCubeX/mihomo/tree/Meta)、[Shadowrocket](https://apps.apple.com/us/app/id932747118)、[Quantumult X](https://apps.apple.com/us/app/id1443988620)、[Surge](https://nssurge.com)、[Leaf](https://github.com/eycorsican/leaf)。

> 适用于 [Nginx](https://nginx.org)，需要配合 [ngx_http_geoip2_module](https://github.com/leev/ngx_http_geoip2_module) 模块使用。

- **GeoLite2-Country.mmdb**：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/GeoLite2-Country.mmdb](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/GeoLite2-Country.mmdb)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/GeoLite2-Country.mmdb](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/GeoLite2-Country.mmdb)
- **GeoLite2-Country.mmdb.sha256sum**：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/GeoLite2-Country.mmdb.sha256sum](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/GeoLite2-Country.mmdb.sha256sum)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/GeoLite2-Country.mmdb.sha256sum](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/GeoLite2-Country.mmdb.sha256sum)

MaxMind 官方版 **ASN** 类型 mmdb 文件：

> 适用于 [mihomo](https://github.com/MetaCubeX/mihomo/tree/Meta)、[Shadowrocket](https://apps.apple.com/us/app/id932747118)、[Surge](https://nssurge.com)。

- **GeoLite2-ASN.mmdb**：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/GeoLite2-ASN.mmdb](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/GeoLite2-ASN.mmdb)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/GeoLite2-ASN.mmdb](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/GeoLite2-ASN.mmdb)
- **GeoLite2-ASN.mmdb.sha256sum**：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/GeoLite2-ASN.mmdb.sha256sum](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/GeoLite2-ASN.mmdb.sha256sum)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/GeoLite2-ASN.mmdb.sha256sum](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/GeoLite2-ASN.mmdb.sha256sum)

本项目生成的**国家/地区**类型 mmdb 文件：

> 适用于 [Clash](https://github.com/Dreamacro/clash)、[mihomo](https://github.com/MetaCubeX/mihomo/tree/Meta)、[Shadowrocket](https://apps.apple.com/us/app/id932747118)、[Quantumult X](https://apps.apple.com/us/app/id1443988620)、[Surge](https://nssurge.com)、[Leaf](https://github.com/eycorsican/leaf)。

> 适用于 [Nginx](https://nginx.org)，需要配合 [ngx_http_geoip2_module](https://github.com/leev/ngx_http_geoip2_module) 模块使用。

> **国家/地区**类别保留了 `Continent` 和 `Country` 里的所有字段。**新增类别**和 **geoip:private** 类别只保留了 `Country` 里的 `iso_code`（两位英文字母表示的国家/地区代号）字段。关于 Maxmind 官方 country MMDB 格式文件完整字段，请[查看代码](https://github.com/oschwald/geoip2-golang/blob/576a46d19bb59f32d0215cb43285b8928891b6bc/reader.go#L139-L171)。

- **Country-without-asn.mmdb**（传统版 GeoIP，只包含国家/地区类别，不包含上述新增类别。建议优先使用）：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country-without-asn.mmdb](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country-without-asn.mmdb)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country-without-asn.mmdb](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country-without-asn.mmdb)
- **Country-without-asn.mmdb.sha256sum**：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country-without-asn.mmdb.sha256sum](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country-without-asn.mmdb.sha256sum)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country-without-asn.mmdb.sha256sum](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country-without-asn.mmdb.sha256sum)
- **Country.mmdb**（增强版 GeoIP，包含国家/地区类别，以及上述新增类别。但由于 MaxMind mmdb 格式限制，部分国家/地区类别的 IP 地址数据不如上述 **Country-without-asn.mmdb** 准确）：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country.mmdb](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country.mmdb)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country.mmdb](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country.mmdb)
- **Country.mmdb.sha256sum**：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country.mmdb.sha256sum](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country.mmdb.sha256sum)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country.mmdb.sha256sum](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country.mmdb.sha256sum)
- **Country-only-cn-private.mmdb**（精简版 GeoIP，只包含 `GEOIP,CN` 和 `GEOIP,PRIVATE`）：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country-only-cn-private.mmdb](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country-only-cn-private.mmdb)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country-only-cn-private.mmdb](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country-only-cn-private.mmdb)
- **Country-only-cn-private.mmdb.sha256sum**：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country-only-cn-private.mmdb.sha256sum](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country-only-cn-private.mmdb.sha256sum)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country-only-cn-private.mmdb.sha256sum](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country-only-cn-private.mmdb.sha256sum)
- **Country-asn.mmdb**（精简版 GeoIP，只包含上述新增类别）：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country-asn.mmdb](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country-asn.mmdb)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country-asn.mmdb](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country-asn.mmdb)
- **Country-asn.mmdb.sha256sum**：
  - [https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country-asn.mmdb.sha256sum](https://raw.githubusercontent.com/fastoot/geoip-IPInfo/release/Country-asn.mmdb.sha256sum)
  - [https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country-asn.mmdb.sha256sum](https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country-asn.mmdb.sha256sum)

#### mmdb 格式文件使用方法

<details>
  <summary>点击查看在 <b>Clash</b> 中的使用方法</summary>
  <br/>
  <p>需要先下载 <code>.mmdb</code> 格式文件，命名为 <code>Country.mmdb</code>，并放置在 Clash 程序目录内。</p>


```yaml
rules:
  - GEOIP,PRIVATE,policy,no-resolve
  - GEOIP,FACEBOOK,policy
  - GEOIP,CN,policy,no-resolve
```

</details>

<details>
  <summary>点击查看在 <b>mihomo</b> 中的使用方法</summary>


```yaml
geodata-mode: true
geox-url:
  mmdb: "https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/Country.mmdb"
  asn: "https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/GeoLite2-ASN.mmdb"
```

</details>

<details>
  <summary>点击查看在 <b>Shadowrocket</b> 中的使用方法</summary>
  <br/>
  <p>需要将下载地址填入到 Shadowrocket 的设置中。</p>


```conf
[Rule]
GEOIP,PRIVATE,DIRECT
GEOIP,FACEBOOK,PROXY
GEOIP,CN,DIRECT
```

</details>

<details>
  <summary>点击查看在 <b>Quantumult X</b> 中的使用方法</summary>
  <br/>
  <p>需要将下载地址填入到 Quantumult X 的设置中。</p>


```conf
[filter_local]
GEOIP,PRIVATE,DIRECT
GEOIP,FACEBOOK,PROXY
GEOIP,CN,DIRECT
```

</details>

<details>
  <summary>点击查看在 <b>Surge</b> 中的使用方法</summary>
  <br/>
  <p>需要将下载地址填入到 Surge 的设置中。</p>


```conf
[Rule]
GEOIP,PRIVATE,policy,no-resolve
GEOIP,FACEBOOK,policy
GEOIP,CN,policy,no-resolve
```

</details>

---

### sing-box SRS 格式文件

> 适用于 [sing-box](https://github.com/SagerNet/sing-box)。

请查看本项目 `release` 分支下的 [srs 目录](https://github.com/fastoot/geoip-IPInfo/tree/release/srs)。

#### SRS 格式文件使用方法

<details>
  <summary>点击查看在 <b>sing-box</b> 中的使用方法</summary>


```json
"route": {
  "rules": [
    {
      "rule_set": "geoip-cn",
      "outbound": "direct"
    },
    {
      "rule_set": "geoip-us",
      "outbound": "block"
    }
  ],
  "rule_set": [
    {
      "tag": "geoip-cn",
      "type": "remote",
      "format": "binary",
      "url": "https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/srs/cn.srs"
    },
    {
      "tag": "geoip-us",
      "type": "remote",
      "format": "binary",
      "url": "https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/srs/us.srs"
    }
  ]
}
```

</details>

---

### mihomo MRS 格式文件

> 适用于 [mihomo](https://github.com/MetaCubeX/mihomo/tree/Meta)。

请查看本项目 `release` 分支下的 [mrs 目录](https://github.com/fastoot/geoip-IPInfo/tree/release/mrs)。

#### MRS 格式文件使用方法

<details>
  <summary>点击查看在 <b>mihomo</b> 中的使用方法</summary>


```yaml
rule-providers:
  cn-cidr:
    type: http
    behavior: ipcidr
    format: mrs
    url: "https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/mrs/cn.mrs"
    path: ./mrs/geoip/cn.mrs
    interval: 86400

  google-cidr:
    type: http
    behavior: ipcidr
    format: mrs
    url: "https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/mrs/google.mrs"
    path: ./mrs/geoip/google.mrs
    interval: 86400

rules:
  - RULE-SET,cn-cidr,DIRECT
  - RULE-SET,google-cidr,PROXY,no-resolve
```

</details>

---

### Clash ruleset 文件

> 适用于 [Clash Premium](https://github.com/Dreamacro/clash)、[mihomo](https://github.com/MetaCubeX/mihomo/tree/Meta)。

请查看本项目 `release` 分支下的 [clash 目录](https://github.com/fastoot/geoip-IPInfo/tree/release/clash)。

#### Clash ruleset 使用方法

<details>
  <summary>点击查看在 <b>Clash Premium</b> 和 <b>mihomo</b> 中的使用方法</summary>


```yaml
rule-providers:
  cn-cidr:
    type: http
    behavior: ipcidr
    format: yaml
    url: "https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/clash/ipcidr/cn.txt"
    path: ./ruleset/ipcidr/cn.yaml
    interval: 86400

  telegram-cidr:
    type: http
    behavior: ipcidr
    format: yaml
    url: "https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/clash/ipcidr/telegram.txt"
    path: ./ruleset/ipcidr/telegram.yaml
    interval: 86400

rules:
  - RULE-SET,cn-cidr,DIRECT
  - RULE-SET,telegram-cidr,PROXY,no-resolve
```

</details>

---

### Surge ruleset 文件

> 适用于 [Surge](https://nssurge.com)。

请查看本项目 `release` 分支下的 [surge 目录](https://github.com/fastoot/geoip-IPInfo/tree/release/surge)。

#### Surge ruleset 使用方法

<details>
  <summary>点击查看在 <b>Surge</b> 中的使用方法</summary>


```conf
[Rule]
RULE-SET,https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/surge/us.txt,REJECT
RULE-SET,https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/surge/cn.txt,DIRECT
RULE-SET,https://cdn.jsdelivr.net/gh/fastoot/geoip-IPInfo@release/surge/telegram.txt,PROXY,no-resolve
```

</details>

---

### 纯文本 txt 格式文件

请查看本项目 `release` 分支下的 [text 目录](https://github.com/fastoot/geoip-IPInfo/tree/release/text)。

---

### Nginx `allow` 和 `deny` 文件

请查看本项目 `release` 分支下的 [nginx 目录](https://github.com/fastoot/geoip-IPInfo/tree/release/nginx)。

---



## License

参照上游项目及 [IPInfo.io](https://ipinfo.io) 的 ToS。
