---
layout: post
title: How to debug ruby tasks on Rubymine
categories: [rubymine]
tags: [rubymine, ruby, rails, tasks, tips, debug]
fullview: true
comments: true
---

**Lets do an example creating a new task**

First create a task file in your rails project, for example:

```bash
touch lib/tasks/debug.rake
```

And add one task in this file:

```ruby
namespace :debug do
  desc 'Test rubymine debug feature'
  task :something => :environment do
    hello = 'world'

    p hello
  end
end
```

Now put a breakpoint on the line that we print the variable hello, and lets config the debugger.

To config the debugger, first go to menu "Run/Edit Configurations..." and add a new configuration using a rake template.

![Configure Debugger]({{ site.url }}/assets/images/debug-tasks-setup.png){:height="30%" width="30%"}

Now fill the first field with you task name.

![Configure Debugger 2]({{ site.url }}/assets/images/debug-tasks-fill.png){:height="70%" width="70%"}

And now you're ready to debug, you just need to click on the bug button with your task selected.

![Configure Debugger 2]({{ site.url }}/assets/images/debug-tasks-sample.png){:height="50%" width="50%"}

You can use the interactive console, see the traces and see the log console too.

It's a wonderful tool and you can use for solving problems in a "clean environment" and make sure your tasks works good.

Have fun!!!
