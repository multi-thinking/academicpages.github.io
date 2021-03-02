---
title: 'Jekyll serve fails on Ruby 3.0'
date: 2021-03-01
permalink: /posts/2021/03/jekyll serve fails on ruby 3.0-3/
tags:
  - blog
  - jekyll
  - ruby3.0
---

1. 问题描述：Jekyll 本地运行的时候报错
2. 解决方法：在Gemfile中添加 <font color=Coral>gem "webrick"</font>，重新运行 <font color=Coral>bundle install</font>，该问题解决。
   

### 本地环境

| 软件 | 版本 |
|:--------|:-------:|
| 操作系统   | MacOS Mojave 10.14.6 |
| Ruby   | 3.0.0   |
|-----------------------------|
| jekyll   | 3.9.0    |
|=============================|

预期结果
======
```ruby
bundle exec jekyll serve
```
---
实际结果
======
```c++
bundle exec jekyll serve fails with the following stack trace:

bundler: failed to load command: jekyll (/Users/david/.rvm/gems/ruby-3.0.0/bin/jekyll)
/Users/david/.rvm/gems/ruby-3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve/servlet.rb:3:in `require': cannot load such file -- webrick (LoadError)
from /Users/david/.rvm/gems/ruby-3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve/servlet.rb:3:in `<top (required)>'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:184:in `require_relative'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:184:in `setup'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:102:in `process'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:93:in `block in start'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:93:in `each'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:93:in `start'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve.rb:75:in `block (2 levels) in init_with_program'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/mercenary-0.3.6/lib/mercenary/command.rb:220:in `block in execute'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/mercenary-0.3.6/lib/mercenary/command.rb:220:in `each'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/mercenary-0.3.6/lib/mercenary/command.rb:220:in `execute'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/mercenary-0.3.6/lib/mercenary/program.rb:42:in `go'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/mercenary-0.3.6/lib/mercenary.rb:19:in `program'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/jekyll-3.9.0/exe/jekyll:15:in `<top (required)>'
from /Users/david/.rvm/gems/ruby-3.0.0/bin/jekyll:23:in `load'
from /Users/david/.rvm/gems/ruby-3.0.0/bin/jekyll:23:in `<top (required)>'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/bundler-2.2.11/lib/bundler/cli/exec.rb:63:in `load'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/bundler-2.2.11/lib/bundler/cli/exec.rb:63:in `kernel_load'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/bundler-2.2.11/lib/bundler/cli/exec.rb:28:in `run'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/bundler-2.2.11/lib/bundler/cli.rb:494:in `exec'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/bundler-2.2.11/lib/bundler/vendor/thor/lib/thor/command.rb:27:in `run'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/bundler-2.2.11/lib/bundler/vendor/thor/lib/thor/invocation.rb:127:in `invoke_command'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/bundler-2.2.11/lib/bundler/vendor/thor/lib/thor.rb:392:in `dispatch'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/bundler-2.2.11/lib/bundler/cli.rb:30:in `dispatch'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/bundler-2.2.11/lib/bundler/vendor/thor/lib/thor/base.rb:485:in `start'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/bundler-2.2.11/lib/bundler/cli.rb:24:in `start'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/bundler-2.2.11/exe/bundle:49:in `block in <top (required)>'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/bundler-2.2.11/lib/bundler/friendly_errors.rb:130:in `with_friendly_errors'
from /Users/david/.rvm/gems/ruby-3.0.0/gems/bundler-2.2.11/exe/bundle:37:in `<top (required)>'
from /Users/david/.rvm/gems/ruby-3.0.0/bin/bundle:23:in `load'
from /Users/david/.rvm/gems/ruby-3.0.0/bin/bundle:23:in `<main>'
```
---
如何解决
------
在Gemfile中添加如下代码：
```ruby
gem "webrick"
```
---
## 参考链接
 [1. Jekyll serve fails on Ruby 3.0 #8523](https://github.com/jekyll/jekyll/issues/8523)

