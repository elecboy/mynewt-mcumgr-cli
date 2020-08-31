我是光年实验室高级招聘经理。
我在github上访问了你的开源项目，你的代码超赞。你最近有没有在看工作机会，我们在招软件开发工程师，拉钩和BOSS等招聘网站也发布了相关岗位，有公司和职位的详细信息。
我们公司在杭州，业务主要做流量增长，是很多大型互联网公司的流量顾问。公司弹性工作制，福利齐全，发展潜力大，良好的办公环境和学习氛围。
公司官网是http://www.gnlab.com,公司地址是杭州市西湖区古墩路紫金广场B座，若你感兴趣，欢迎与我联系，
电话是0571-88839161，手机号：18668131388，微信号：echo 'bGhsaGxoMTEyNAo='|base64 -D ,静待佳音。如有打扰，还请见谅，祝生活愉快工作顺利。

<!--
#
# Licensed to the Apache Software Foundation (ASF) under one
# or more contributor license agreements.  See the NOTICE file
# distributed with this work for additional information
# regarding copyright ownership.  The ASF licenses this file
# to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance
# with the License.  You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing,
# software distributed under the License is distributed on an
# "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
#  KIND, either express or implied.  See the License for the
# specific language governing permissions and limitations
# under the License.
#
-->

# mcumgr

MCU Manager (`mcumgr`) is the application tool that enables a user to communicate
with and manage remote devices running an
[mcumgr server](https://github.com/apache/mynewt-mcumgr).

The `mcumgr` tool is a thin wrapper over the Apache `newtmgr` tool.  Thus, the
[`newtmgr` documentation](http://mynewt.apache.org/latest/newtmgr/index.html)
provides some useful help with using the `mcumgr` tool.

### Building

Build the mcumgr tool as follows:

1. Unpack mcumgr source.
2. Rename resulting `apache-mynewt-mcumgr-1.3.0` directory to `$GOPATH/src/mynewt.apache.org/mcumgr`
3. `cd $GOPATH/src/mynewt.apache.org/mcumgr/mcumgr`
4. `go build`

### Examples

Here are some example `mcumgr` invocations.

#### Send an echo command over Bluetooth

The following sends an echo command to a Bluetooth device advertising the name
"Zephyr":

```
mcumgr --conntype ble --connstring peer_name=Zephyr echo hello
```

#### Upgrade firmware over Bluetooth

This series of commands performs an image upgrade over Bluetooth.  The device is assumed to be advertising the name "Zephyr".


```
# 1. Query device for its current image list.
mcumgr --conntype ble --connstring 'peer_name=Zephyr' image list

# 2. Upload new image to device.
mcumgr --conntype ble --connstring 'peer_name=Zephyr' image upload <filename>

# 3. Tell the device to run the new image on its next boot ("test" the new
#    image).
mcumgr --conntype ble --connstring 'peer_name=Zephyr' image test <image-hash>

# 4. Reboot the device.
mcumgr --conntype ble --connstring 'peer_name=Zephyr' reset

# 5. Query device for its current image list; ensure new image is running.
mcumgr --conntype ble --connstring 'peer_name=Zephyr' image list

# 6. Make the image swap permanent.
mcumgr --conntype ble --connstring 'peer_name=Zephyr' image confirm
```
