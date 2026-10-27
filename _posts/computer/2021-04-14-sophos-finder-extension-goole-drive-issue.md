---
published: true
title: "Workaround: 如何解决OneDrive, Dropbox或Google Sync的文件夹没有同步状态提示的问题"
category: computer
---

TL;DR: 如果你有遇到 OneDrive, Dropbox 或 Google Sync 的文件夹没有同步状态提示的问题，本文提供了一个 workaround。

我的公司电脑很长时间都存在这个问题，而自己其他电脑则正常，苦于网上搜索的方法都无法解决，以为自己是个例。最近由于电脑故障送修，结合期间使用备用机，先后 3 次 setup 电脑的经历中都遇到了同样的问题，就开始怀疑是某种通病，起先怀疑的是 Google File Stream，后来发现原来是 Sophos Finder Scan。这一下子就都解释得通了。好在 Workaround 也比较简单（见文末）。

## 问题描述：

公司电脑上的 OneDrive, Dropbox 或 Google Sync 所同步的文件夹没有同步状态的提示图标。

Expected（正常显示的同步状态的提示图标）:

![Expected]({{site.baseurl}}/assets/images/KZGuyYz.png)

Actual（同步状态的提示图标没有显示）:

![Actual]({{site.baseurl}}/assets/images/jlf1BGf.png)

## 问题原因：

Sophos Finder Scan 的 Finder extension 影响了 OneDrive, Dropbox 和 Google Sync 的 Finder extension 的正常工作，导致同步状态的图标不显示。

后来找到了证实，原来这是一个 Sophos 的 known issue: https://support.sophos.com/support/s/article/KB-000038112

## Workaround:

Step 1: 取消勾选 Sophos Finder Scan

![Step 1]({{site.baseurl}}/assets/images/Kllt6lH.png)

Step 2: 将 Sophos Finder Scan 再勾选回去

![Step 2]({{site.baseurl}}/assets/images/miXpbKF.png)
