# Hey Rbenv 100

|本期版本|上期版本
|:---:|:---:
`Sat Aug  2 14:21:08 CST 2025` | -


## rbenv-doctor

```
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/HEAD/bin/rbenv-doctor | bash
```

## macOS

> `15.6`

```bash
brew install rbenv
```

```bash
git clone https://github.com/AndorChen/rbenv-china-mirror "$(rbenv root)"/plugins/rbenv-china-mirror
git clone https://github.com/rbenv/rbenv-vars.git "$(rbenv root)"/plugins/rbenv-vars
```



**Fish**

> `~/.config/fish/config.fish`

```bash
# rbenv init
# 略显冗余，可以采用下面方法手动处理
status --is-interactive; and rbenv init - --no-rehash fish | source

rbenv init - --no-rehash fish | source
```



## ruby-build

> [Suggested build environment](https://github.com/rbenv/ruby-build/wiki#suggested-build-environment)

```bash
export RUBY_CONFIGURE_OPTS="--disable-install-doc --disable-install-rdoc"
```


```bash
set -Ux RUBY_CONFIGURE_OPTS --disable-install-doc --disable-install-rdoc 
```



### 🧨 小内存相关

```bash
# 跳过 YJIT 编译（不推荐，除非你不需要 JIT）
export RUBY_CONFIGURE_OPTS="--disable-yjit"

# 降低并发度，减少内存使用
export MAKEOPTS="-j1"
```

---

```
--enable-shared
- libjemalloc1
- libjemalloc-dev
```



## Ubuntu

> Ansible 仅安装了  `rbenv`运行环境(一些插件) 与编译依赖。

为每个用户单独编译自己的版本

```bash
~/.rbenv/bin/rbenv init
rbenv install -kv 3.4.8
rbenv global 3.4.8
```


```bash
export RUBY_CONFIGURE_OPTS="--disable-install-doc --disable-install-rdoc"
export MAKEOPTS="-j1"
export RUBY_CFLAGS="-O2"
```

参数|说明
---｜---
`--disable-install-doc` |         不安装文档（ri）
`--disable-install-rdoc` |         不生成 rdoc 文档
`    -j1` | 单线程编译
`-j$(nproc)` | CPU 核心数并行编译
`-O2` | 优化等级




## Ref

* <https://github.com/rbenv/rbenv>、<https://github.com/rbenv/rbenv-installer>
* <https://github.com/rbenv/ruby-build>
* <https://github.com/AndorChen/rbenv-china-mirror>
* <https://github.com/rbenv/rbenv-vars>
* [How to automate rbenv installations](https://relativkreativ.at/articles/how-to-automate-rbenv-installations)
* [zzet/rbenv](https://github.com/zzet/rbenv)