---
layout: post
author: Johanan
title: Doing a bit more with nvidia-smi queries
---

`nvidia-smi`, or the Nvidia System Management Interface is a command line utility that is usually used to monitor the status/parameters of an nvidia GPU.
It provides some useful information in the form of a table, of which the most important to me are: 
- the temperature
- the time and memory utilization
- the various processes using it.

You can make the output refresh/loop every second by running `nvidia-smi -l 1`. 
You can also specify the time in milliseconds using `-lms`
Some use the `watch` command, but it's not necessary. 
But this post is not really about all that, it's about **nvidia-smi queries**. 
 

Queries can help you get just the information you need in a csv format. 
But what you do with that information is upto you. 
For example, this query is very useful to me: 
```
nvidia-smi --query-gpu=timestamp,temperature.gpu,utilization.gpu,memory.used --format=csv -l 1
```
It gives me all the information I need.
There are more to choose from, but I don't want to talk about it here since the [documentation](https://nvidia.custhelp.com/app/answers/detail/a_id/3751/~/useful-nvidia-smi-queries) is pretty straight-foward, with good examples.
Look at the tables, and you will most probably find what you need.

Notice the lack of spaces between parameters in the query, that is on purpose. 
The query would not not work otherwise. 
Now, the output is displayed as a series of prompts one below the other, you can also use this query with `watch` to avoid that, for example: 
```
watch -n 1 nvidia-smi --query-gpu=timestamp,temperature.gpu,utilization.gpu,memory.used --format=csv
```
You would have to remove the loop parameter of course.
Use `nvidia-smi --help` to discover other interesting ways to get information about your GPU.

But I hope you realize that this post is not about fancy ways to display information. 
I feel that the default display offered by `nvidia-smi` does a very good job at that. 
This post is more about *what you do with the info*.