#一键安装Hysteria2

```
bash <(curl -fsSL https://get.hy2.sh/)
```

#生成自签证书

```
openssl req -x509 -nodes -newkey ec:<(openssl ecparam -name prime256v1) -keyout /etc/hysteria/server.key -out /etc/hysteria/server.crt -subj "/CN=bing.com" -days 36500 && sudo chown hysteria /etc/hysteria/server.key && sudo chown hysteria /etc/hysteria/server.crt
```

#启动Hysteria2
```
systemctl start hysteria-server.service
```
#重启Hysteria2
```
systemctl restart hysteria-server.service
```
#查看Hysteria2状态
```
systemctl status hysteria-server.service
```
#停止Hysteria2
```
systemctl stop hysteria-server.service
```
#设置开机自启
```
systemctl enable hysteria-server.service
```
#查看日志
```
journalctl -u hysteria-server.service
```

服务器配置文件

```
cat << EOF > /etc/hysteria/config.yaml
listen: :443 #监听端口

#使用CA证书
#acme:
#  domains:
#    - a.com #你的域名，需要先解析到服务器ip
#  email: test@sharklasers.com

#使用自签证书
#tls:
#  cert: /etc/hysteria/server.crt
#  key: /etc/hysteria/server.key

auth:
  type: password
  password: 123456 #设置认证密码
  
masquerade:
  type: proxy
  proxy:
    url: https://bing.com #伪装网址
    rewriteHost: true
EOF
```

客户端配置文件

```
server: ip:443
auth: 123456

bandwidth:
  up: 20 mbps
  down: 100 mbps
  
tls:
  sni: a.com
  insecure: false #使用自签时需要改成true

socks5:
  listen: 127.0.0.1:1080
http:
  listen: 127.0.0.1:8080
  ```

# ![Hysteria 2](logo.svg)

[![License][1]][2] [![Release][3]][4] [![Telegram][5]][6] [![Discussions][7]][8]

[1]: https://img.shields.io/badge/license-MIT-blue
[2]: LICENSE.md
[3]: https://img.shields.io/github/v/release/apernet/hysteria?style=flat-square
[4]: https://github.com/apernet/hysteria/releases
[5]: https://img.shields.io/badge/chat-Telegram-blue?style=flat-square
[6]: https://t.me/hysteria_github
[7]: https://img.shields.io/github/discussions/apernet/hysteria?style=flat-square
[8]: https://github.com/apernet/hysteria/discussions

<h2 style="text-align: center;">Hysteria is a powerful, lightning fast and censorship resistant proxy.</h2>

### [Get Started](https://v2.hysteria.network/)

### [中文文档](https://v2.hysteria.network/zh/)

### [Hysteria 1.x (legacy)](https://v1.hysteria.network/)

---

<div class="feature-grid">
  <div>
    <h3>🛠️ Packed to the gills</h3>
    <p>Expansive range of modes including SOCKS5, HTTP proxy, TCP/UDP forwarding, Linux TProxy - not to mention additional features continually being added.</p>
  </div>

  <div>
    <h3>⚡ Lightning fast</h3>
    <p>Powered by a custom QUIC protocol, Hysteria delivers unparalleled performance over even the most unreliable and lossy networks.</p>
  </div>

  <div>
    <h3>✊ Censorship resistant</h3>
    <p>Our protocol is designed to masquerade as standard HTTP/3 traffic, making it very difficult to detect and block without widespread collateral damage.</p>
  </div>
  
  <div>
    <h3>💻 Cross-platform</h3>
    <p>We have builds for all major platforms and architectures. Deploy anywhere & use everywhere.</p>
  </div>

  <div>
    <h3>🔗 Easy integration</h3>
    <p>With built-in support for custom authentication, traffic statistics & access control, Hysteria is easy to integrate into your infrastructure.</p>
  </div>
  
  <div>
    <h3>🤗 Open standards</h3>
    <p>We have well-documented specifications and code for developers to contribute and build their own apps.</p>
  </div>
</div>

---

**If you find Hysteria useful, consider giving it a ⭐️!**

[![Star History Chart](https://api.star-history.com/svg?repos=apernet/hysteria&type=Date)](https://star-history.com/#apernet/hysteria&Date)
