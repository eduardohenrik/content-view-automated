# Red Hat Satellite Content-view automation

This bash script aims to automate the process of creating and promoting content-views in Red Hat Satellite 6.x

## Getting Started

These instructions will get you a copy of the project on your local machine. See prerequisites and installing section for notes on how to deploy the project on a live system.

1. Clone this repo: 
   $ git clone https://github.com/eduardohenrik/content-view-automated.git
2. $ cd /content-view-automated

### Prerequisites

First, you have to collect the content-view ID's using the command below:

```
$ hammer content-view list
```

You gonna see an output like this:

```
----------------|---------------------------|--------------------------------------|-----------|---------------------|----------------------------------------------------------------------------
CONTENT VIEW ID | NAME                      | LABEL                                | COMPOSITE | LAST PUBLISHED      | REPOSITORY IDS
----------------|---------------------------|--------------------------------------|-----------|---------------------|----------------------------------------------------------------------------
3               | Default Organization View | 38465732-99dc-431b-8f09-3b47298f5705 |           | 2016/01/29 17:52:56 |
5               | Development Content View  | Development                          |           | 2018/03/23 21:25:56 | 2, 5
6               | Homologation_Content_View | Homologation                         |           | 2019/02/25 13:32:12 | 287, 574, 2688, 2687, 2, 5
4               | Production Content View   | Production                           |           | 2019/02/25 13:27:38 | 2, 5, 2688, 2687, 574
----------------|---------------------------|--------------------------------------|-----------|---------------------|----------------------------------------------------------------------------

```

Choose the content-view that you want to automate, and select the ID showed on the first table.

Use an code editor, and go to line 10 of the script to replace the example id's to yours. 

```
# vim cvautomate
```

```
10: for i in 4 6;
```

Close the file, saving of course! :)

We're almost ready!

### Excecuting 

After the configurations we set before, we only have to run the script and see the tasks executing until the end.

Just run:

```
# ./cvautomate
```

It's will excecute for a little time, and will be possible to follow the procedure through the output given.

Output example:
```
========  Publishing Organization_Production content-view. ============
[....................................................................................................................................................................................................................................] [100%]
{"content_view_id"=>4,
 "content_view_version_id"=>369,
 "composite_version_auto_published"=>[],
 "composite_view_publish_failed"=>[],
 "composite_auto_publish_task_id"=>[]}

========  Promoting Organization_Production content-view. ============
[....................................................................................................................................................................................................................................] [100%]

========  Publishing Organization_Homologation content-view. ============
[....................................................................................................................................................................................................................................] [100%]
{"content_view_id"=>6,
 "content_view_version_id"=>370,
 "composite_version_auto_published"=>[],
 "composite_view_publish_failed"=>[],
 "composite_auto_publish_task_id"=>[]}

========  Promoting Organization_Homologation content-view. ============
[....................................................................................................................................................................................................................................] [100%]
```

## Result

![Expected reasult](http://i63.tinypic.com/2viide1.png)

## Built With

* [Hammer](https://access.redhat.com/documentation/en-us/red_hat_satellite/6.2/html/hammer_cli_guide/index) - Hammer CLI guide

## Limitations

- Only tested with RHEL 7 and Satellite server 6.x
