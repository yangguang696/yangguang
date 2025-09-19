# yangguang
随便玩玩
[Rule]
DOMAIN-SUFFIX,amazonaws.com,PROXY // 亚马逊AWS云服务，国际服后端常用
DOMAIN-SUFFIX,aov-game.com,PROXY // 国际服相关域名
DOMAIN-SUFFIX,aov.garena.com,PROTY // Garena代理的版本
DOMAIN-SUFFIX,garenanow.com,PROXY // Garena域名
DOMAIN-SUFFIX,proximabeta.com,PROXY // 腾讯游戏国际服常用域名
USER-AGENT,Arena%20of%20Valor*,PROXY // 用户代理标识（可选，增强匹配）

# 2. IPCIDR 规则（覆盖游戏服务器IP，防止域名规则失效）
IP-CIDR,8.219.235.0/24,PROXY,no-resolve // Level3通信公司，常被游戏使用
IP-CIDR,47.246.21.0/24,PROXY,no-resolve // 腾讯云香港
IP-CIDR,49.51.42.0/24,PROXY,no-resolve // 腾讯云海外
IP-CIDR,52.76.76.0/24,PROXY,no-resolve // 亚马逊AWS新加坡
IP-CIDR,54.169.76.0/24,PROXY,no-resolve // 亚马逊AWS新加坡
IP-CIDR,54.255.171.0/24,PROXY,no-resolve // 亚马逊AWS新加坡
IP-CIDR,64.233.160.0/19,PROXY,no-resolve // Google云
IP-CIDR,129.226.0.0/16,PROXY,no-resolve // 腾讯云香港
IP-CIDR,139.159.0.0/16,PROXY,no-resolve // 腾讯云海外
IP-CIDR,162.14.0.0/16,PROXY,no-resolve // 腾讯云海外

# 3. GEOIP 规则（兜底，匹配非中国IP走代理，确保国外游戏流量被代理）
GEOIP,CN,DIRECT // 所有中国IP直连（非常重要，保证国服不卡顿）
GEOIP,US,PROXY // 美国IP走代理（示例，可根据你的节点位置调整）
GEOIP,SG,PROXY // 新加坡IP走代理（示例，AOV常用服务器地区）
GEOIP,JP,PROXY // 日本IP走代理（示例）
# ... 可以添加其他游戏服务器所在地的GEOIP规则

# ---------- 必须的最终规则 ----------
FINAL,DIRECT // 最终所有未匹配的流量直连

[Host]
# 可选的本地DNS映射，用于解决某些域名污染（如果需要）
aov-game.com = server:8.8.8.8
proximabeta.com = server:1.1.1.1
