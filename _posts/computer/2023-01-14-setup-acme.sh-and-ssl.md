---
published: true
title: acme.sh安装和ssl证书使用教程
category: computer
tags: ssl lets-encrypt acme.sh
---

参考资料：

- [How to Install](https://github.com/acmesh-official/acme.sh#1-how-to-install)
- [使用 DNS 作为验证方式](https://github.com/acmesh-official/acme.sh/wiki/%E8%AF%B4%E6%98%8E#2-%E6%89%8B%E5%8A%A8-dns-%E6%96%B9%E5%BC%8F-%E6%89%8B%E5%8A%A8%E5%9C%A8%E5%9F%9F%E5%90%8D%E4%B8%8A%E6%B7%BB%E5%8A%A0%E4%B8%80%E6%9D%A1-txt-%E8%A7%A3%E6%9E%90%E8%AE%B0%E5%BD%95-%E9%AA%8C%E8%AF%81%E5%9F%9F%E5%90%8D%E6%89%80%E6%9C%89%E6%9D%83)
- [Use FreeDNS as DNS provider](https://github.com/acmesh-official/acme.sh/wiki/dnsapi#15-use-freedns)
- [Use Cloudflare as DNS provider](https://github.com/acmesh-official/acme.sh/wiki/dnsapi#dns_cf)
- [更新证书](https://github.com/acmesh-official/acme.sh/wiki/%E8%AF%B4%E6%98%8E#5-%E6%9B%B4%E6%96%B0%E8%AF%81%E4%B9%A6)

### Step 1: 安装 acme.sh

`curl https://get.acme.sh | sh -s email=email@example.com`

Shell Output:

```
[2023年 01月 14日 星期六 11:13:47 CST] Installing from online archive.
[2023年 01月 14日 星期六 11:13:47 CST] Downloading https://github.com/acmesh-official/acme.sh/archive/master.tar.gz
[2023年 01月 14日 星期六 11:13:50 CST] Extracting master.tar.gz
[2023年 01月 14日 星期六 11:13:50 CST] Installing to /home/pi/.acme.sh
[2023年 01月 14日 星期六 11:13:50 CST] Installed to /home/pi/.acme.sh/acme.sh
[2023年 01月 14日 星期六 11:13:50 CST] Installing alias to '/home/pi/.bashrc'
[2023年 01月 14日 星期六 11:13:50 CST] OK, Close and reopen your terminal to start using acme.sh
[2023年 01月 14日 星期六 11:13:50 CST] Installing cron job
29 0 * * * "/home/pi/.acme.sh"/acme.sh --cron --home "/home/pi/.acme.sh" > /dev/null
[2023年 01月 14日 星期六 11:13:50 CST] Good, bash is found, so change the shebang to use bash as preferred.
[2023年 01月 14日 星期六 11:13:52 CST] OK
[2023年 01月 14日 星期六 11:13:52 CST] Install success!
```

Close and reopen your terminal to start using acme.sh.

### Step 2: 使用 FREEDNS or Cloudflare 的DNS验证方式申请 SSL 证书


FreeDNS (doesn't support subdomains)
```
export FREEDNS_User="xxx"
export FREEDNS_Password="xxx"
acme.sh --issue --dns dns_freedns -d 'subdomain.eu.org' -d '*.subdomain.eu.org'
```

Cloudflare (works for subdomains)
```
export CF_Zone_ID="xxx"
export CF_Token="xxx"
acme.sh --issue --dns dns_cf -d 'subdomain.eu.org' -d '*.subdomain.eu.org'
```


Shell Output:

```
[2023年 01月 14日 星期六 11:21:51 CST] Using CA: https://acme.zerossl.com/v2/DV90
[2023年 01月 14日 星期六 11:21:51 CST] Creating domain key
[2023年 01月 14日 星期六 11:21:51 CST] The domain key is here: /home/pi/.acme.sh/your-domain.com/your-domain.com.key
[2023年 01月 14日 星期六 11:21:52 CST] Multi domain='DNS:your-domain.com,DNS:www.your-domain.com'
[2023年 01月 14日 星期六 11:21:52 CST] Getting domain auth token for each domain
[2023年 01月 14日 星期六 11:22:39 CST] Getting webroot for domain='your-domain.com'
[2023年 01月 14日 星期六 11:22:39 CST] Getting webroot for domain='www.your-domain.com'
[2023年 01月 14日 星期六 11:22:39 CST] Adding txt value: xxx for domain:  _acme-challenge.your-domain.com
[2023年 01月 14日 星期六 11:22:39 CST] Add TXT record using FreeDNS
[2023年 01月 14日 星期六 11:22:42 CST] Domain your-domain.com found at FreeDNS, domain_id xxx
[2023年 01月 14日 星期六 11:22:43 CST] Added acme challenge TXT record for _acme-challenge.your-domain.com at FreeDNS
[2023年 01月 14日 星期六 11:22:43 CST] The txt record is added: Success.
[2023年 01月 14日 星期六 11:22:43 CST] Adding txt value: xxx for domain:  _acme-challenge.www.your-domain.com
[2023年 01月 14日 星期六 11:22:43 CST] Add TXT record using FreeDNS
[2023年 01月 14日 星期六 11:23:14 CST] Domain www.your-domain.com not found at FreeDNS, try with next level of TLD
[2023年 01月 14日 星期六 11:23:15 CST] Domain your-domain.com found at FreeDNS, domain_id xxx
[2023年 01月 14日 星期六 11:23:16 CST] Added acme challenge TXT record for _acme-challenge.www.your-domain.com at FreeDNS
[2023年 01月 14日 星期六 11:23:16 CST] The txt record is added: Success.
[2023年 01月 14日 星期六 11:23:16 CST] Let's check each DNS record now. Sleep 20 seconds first.
[2023年 01月 14日 星期六 11:23:37 CST] You can use '--dnssleep' to disable public dns checks.
[2023年 01月 14日 星期六 11:23:37 CST] See: https://github.com/acmesh-official/acme.sh/wiki/dnscheck
[2023年 01月 14日 星期六 11:23:37 CST] Checking your-domain.com for _acme-challenge.your-domain.com
[2023年 01月 14日 星期六 11:23:39 CST] Domain your-domain.com '_acme-challenge.your-domain.com' success.
[2023年 01月 14日 星期六 11:23:39 CST] Checking www.your-domain.com for _acme-challenge.www.your-domain.com
[2023年 01月 14日 星期六 11:23:40 CST] Domain www.your-domain.com '_acme-challenge.www.your-domain.com' success.
[2023年 01月 14日 星期六 11:23:40 CST] All success, let's return
[2023年 01月 14日 星期六 11:23:40 CST] Verifying: your-domain.com
[2023年 01月 14日 星期六 11:23:52 CST] Processing, The CA is processing your order, please just wait. (1/30)
[2023年 01月 14日 星期六 11:24:07 CST] Processing, The CA is processing your order, please just wait. (2/30)
[2023年 01月 14日 星期六 11:24:23 CST] Processing, The CA is processing your order, please just wait. (3/30)
[2023年 01月 14日 星期六 11:24:36 CST] Success
[2023年 01月 14日 星期六 11:24:36 CST] Verifying: www.your-domain.com
[2023年 01月 14日 星期六 11:24:48 CST] Processing, The CA is processing your order, please just wait. (1/30)
[2023年 01月 14日 星期六 11:25:03 CST] Processing, The CA is processing your order, please just wait. (2/30)
[2023年 01月 14日 星期六 11:25:19 CST] Processing, The CA is processing your order, please just wait. (3/30)
[2023年 01月 14日 星期六 11:25:34 CST] Processing, The CA is processing your order, please just wait. (4/30)
[2023年 01月 14日 星期六 11:25:47 CST] Processing, The CA is processing your order, please just wait. (5/30)
[2023年 01月 14日 星期六 11:26:01 CST] Processing, The CA is processing your order, please just wait. (6/30)
[2023年 01月 14日 星期六 11:26:15 CST] Processing, The CA is processing your order, please just wait. (7/30)
[2023年 01月 14日 星期六 11:26:30 CST] Success
[2023年 01月 14日 星期六 11:26:30 CST] Removing DNS records.
[2023年 01月 14日 星期六 11:26:30 CST] Removing txt: xxx for domain: _acme-challenge.your-domain.com
[2023年 01月 14日 星期六 11:26:30 CST] Delete TXT record using FreeDNS
[2023年 01月 14日 星期六 11:26:38 CST] Deleting TXT record for _acme-challenge.your-domain.com, xxx
[2023年 01月 14日 星期六 11:26:40 CST] Deleted acme challenge TXT record for _acme-challenge.your-domain.com at FreeDNS
[2023年 01月 14日 星期六 11:26:40 CST] Removed: Success
[2023年 01月 14日 星期六 11:26:40 CST] Removing txt: xxx for domain: _acme-challenge.www.your-domain.com
[2023年 01月 14日 星期六 11:26:40 CST] Delete TXT record using FreeDNS
[2023年 01月 14日 星期六 11:26:42 CST] Deleting TXT record for _acme-challenge.www.your-domain.com, xxx
[2023年 01月 14日 星期六 11:26:44 CST] Deleted acme challenge TXT record for _acme-challenge.www.your-domain.com at FreeDNS
[2023年 01月 14日 星期六 11:26:44 CST] Removed: Success
[2023年 01月 14日 星期六 11:26:44 CST] Verify finished, start to sign.
[2023年 01月 14日 星期六 11:26:44 CST] Lets finalize the order.
[2023年 01月 14日 星期六 11:26:44 CST] Le_OrderFinalize='https://acme.zerossl.com/v2/DV90/order/xxx/finalize'
[2023年 01月 14日 星期六 11:26:55 CST] Order status is processing, lets sleep and retry.
[2023年 01月 14日 星期六 11:26:55 CST] Retry after: 15
[2023年 01月 14日 星期六 11:27:11 CST] Polling order status: https://acme.zerossl.com/v2/DV90/order/xxx
[2023年 01月 14日 星期六 11:27:23 CST] Downloading cert.
[2023年 01月 14日 星期六 11:27:23 CST] Le_LinkCert='https://acme.zerossl.com/v2/DV90/cert/xxx'
[2023年 01月 14日 星期六 11:27:35 CST] Cert success.
-----BEGIN CERTIFICATE-----
此处省略证书内容
-----END CERTIFICATE-----
[2023年 01月 14日 星期六 11:27:35 CST] Your cert is in: /home/pi/.acme.sh/your-domain.com/your-domain.com.cer
[2023年 01月 14日 星期六 11:27:35 CST] Your cert key is in: /home/pi/.acme.sh/your-domain.com/your-domain.com.key
[2023年 01月 14日 星期六 11:27:35 CST] The intermediate CA cert is in: /home/pi/.acme.sh/your-domain.com/ca.cer
[2023年 01月 14日 星期六 11:27:35 CST] And the full chain certs is there: /home/pi/.acme.sh/your-domain.com/fullchain.cer
```

证书颁发完成。

### Step 3: 更新证书

目前证书在 60 天以后会自动更新, 你无需任何操作. 今后有可能会缩短这个时间, 不过都是自动的, 你不用关心.

请确保 cronjob 正确安装, 看起来是类似这样的:

```
crontab  -l

56 * * * * "/root/.acme.sh"/acme.sh --cron --home "/root/.acme.sh" > /dev/null
```
