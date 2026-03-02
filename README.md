<div align="center">
<h1>AdGuard Rule</h1>
  <p>
    一个简易的Java程序，用于合并与更新 AdGuard 过滤规则
</p>
</div>


<h2 id="a">📔 说明</h2>

本项目旨在按需求整合 `AdGuard` 规则。定时从上游订阅获取规则，去除`重复`和`不受支持`的规则并进行分类。如果存在误杀请手动放行。  
支持`AdGuard`、`AdGuard Home`,每`24小时`自动更新一次   

<li><a href="https://paileactivist.github.io/toolz/adblock.html">测试广告拦截率</a></li>

#### 上游规则

<details>
<summary>点击查看</summary>
<ul>
    <li><a href="https://raw.githubusercontent.com/uniartisan/adblock_list/master/adblock_privacy.txt">AWAvenue 广告规则</a></li> 
    <li><a href="https://raw.githubusercontent.com/uniartisan/adblock_list/master/adblock.txt">uniartisan 的广告拦截列表</a></li>
    <li><a href="https://raw.githubusercontent.com/TG-Twilight/AWAvenue-Ads-Rule/main/AWAvenue-Ads-Rule.txt">uniartisan 的隐私列表</a></li>
</ul>
</details>

#### 本地规则

- [mylist](#)
> 主要是对上游规则的修正补充，根据日常使用体验，解除一些失误拦截

<h2 id="b">🎯 订阅</h2>

| 名称           | 说明                                                | Github订阅                                                                              | jsDelivr加速订阅                                                                        |
|--------------|---------------------------------------------------|---------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| `all.txt`    | 去重的规则合集，包含以下所有规则，适用于 `AdGuard` 客户端                | [✈️点此查看](https://raw.githubusercontent.com/asdf324lakj/AGH-Rule/master/rule/all.txt)      | [🚀点此查看(延迟)](https://cdn.jsdelivr.net/gh/asdf324lakj/AGH-Rule/rule/all.txt)    |
| `adgh.txt`   | 针对 `AdGuardHome` 的规则，包含 `domain.txt` `regex.txt`和`mylist.txt` | [✈️点此查看](https://raw.githubusercontent.com/asdf324lakj/AGH-Rule/master/rule/adgh.txt)   | [🚀点此查看(延迟)](https://cdn.jsdelivr.net/gh/asdf324lakj/AGH-Rule/rule/adgh.txt)   |
| `domain.txt` | 域名规则，`AdGuard`和`AdGuardHome`都支持                                       | [✈️点此查看](https://raw.githubusercontent.com/asdf324lakj/AGH-Rule/master/rule/domain.txt) | [🚀点此查看(延迟)](https://cdn.jsdelivr.net/gh/asdf324lakj/AGH-Rule/rule/domain.txt) |
| `hosts.txt`  | `hosts` 规则，~~包含一些访问加速~~                           | [✈️点此查看](https://raw.githubusercontent.com/asdf324lakj/AGH-Rule/master/rule/hosts.txt)  | [🚀点此查看(延迟)](https://cdn.jsdelivr.net/gh/asdf324lakj/AGH-Rule/rule/hosts.txt)  |
| `modify.txt` | 修饰规则，`AdGuard`支持                                      | [✈️点此查看](https://raw.githubusercontent.com/asdf324lakj/AGH-Rule/master/rule/modify.txt) | [🚀点此查看(延迟)](https://cdn.jsdelivr.net/gh/asdf324lakj/AGH-Rule/rule/modify.txt) |
| `regex.txt` | 正则规则，`AdGuardHome`支持                                       | [✈️点此查看](https://raw.githubusercontent.com/asdf324lakj/AGH-Rule/master/rule/regex.txt) | [🚀点此查看(延迟)](https://cdn.jsdelivr.net/gh/asdf324lakj/AGH-Rule/rule/regex.txt) |
| `mylist.txt` | 自用补充规则，人工更新                                       | [✈️点此查看](https://raw.githubusercontent.com/asdf324lakj/AGH-Rule/master/rule/mylist.txt) | [🚀点此查看(延迟)](https://cdn.jsdelivr.net/gh/asdf324lakj/AGH-Rule/rule/mylist.txt) |

<br/>
<h2 id="c">🛠️ 配置</h2>

#### 示例配置

```yaml
application:
  rule:       
    #远程规则订阅，仅支持http、https
    remote:
      - 'https://example.com/list.txt'
    #本地规则，请将文件移动到项目路径rule目录中
    local: 
      - 'mylist.txt'
  output:
    path: rule   #规则文件输出路径，相对路径默认从 项目目录开始
    files:
      all.txt:    #输出文件名
        - DOMAIN  #域名规则，仅完整域名
        - REGEX   #正则规则，包含正则的域名规则，AdGH支持
        - MODIFY  #修饰规则，添加了一些修饰符号的规则，AdG支持
        - HOSTS   #Hosts规则
```

#### 使用 Github Action

- fork本项目
- 参照示例配置，修改配置文件: `src/main/resources/application.yml`，注意本地规则文件应放入项目根目录 `rule` 文件夹
- 编辑 `.github/workflows/auto-update.yml` 文件，将 `Commit Changes` 区块下邮箱与用户名修改为自己的（Github邮箱与用户名）
- 提交所有修改并等待 `Github Action` 执行，执行完成后相应规则生成在配置中指定的目录下
- 👉 特别感谢@fordes123

<br/>
<h2 id="c">🧭 支持</h2>

[![Powered by DartNode](https://dartnode.com/_branding/DN-Open-Source-sm.png)](https://dartnode.com "Powered by DartNode - Free VPS for Open Source")
