# BuildBot Bootstrap

[Bootstrap] templates for [BuildBot]

Let's give Buildbot some style!

# What is BBB

BBB is a set of templates to be used with [BuildBot] 0.8.7 or newer. They use Twitter [Bootstrap] CSS and JavaScript improve the web interface.

Yes, I know there are some plans to create new [BuildBot] templates using [Bootstrap] in revision 0.9, but now you can use them with 0.8 by using bbb.

The information shown is basically the same than the default templates show (maybe a button more or something like that), but no new information is shown and no old information is hidden.

I tried to add more information (like a dropdown menu with the builder names), but that required to modify the [BuildBot] code itself, and it was out of the scope of this project.

# Installation

## The easy way

1. Copy the "templates" directory content into the "templates" directory in your master installation
1. Restart/reconfigure the master.

Code (be careful, it can override your templates):

```bash
    MASTER_PATH=.
    BBB_PATH=../bbb
    scp -r $BBB_PATH/templates/* $MASTER_PATH/templates
```

## The GIT way

If you are using a Git repository and you do not think about modifying the templates, maybe this can be the best form to install BBB:

1. Add the BBB repository as a module: `git module add https://magmax@github.com/magmax/bbb.git`
1. In your [BuildBot] master directory, create a link "templates" to the "templates" directory in the BBB working copy.
1. Restart/Reconfigure the master.

Code (be careful, it may delete some of your files):

```bash
    MASTER_PATH=.
    BBB_PATH=./bbb
    git submodule add https://magmax@github.com/magmax/bbb.git $BBB_PATH
    git update --init
    rm -rf $MASTER_PATH/templates
    ln -s $BBB_PATH/templates $MASTER_PATH/templates
```

## The BuildBot way

Another option is to configure [BuildBot] in order to retrieve the templates from their location, as it is explained in the [BuildBot Manual]:

```python
    import jinja2
    myloaders = [
        jinja2.FileSystemLoader("/my/bbb/path"),
        ]
    c['status'].append(html.WebStatus(
        …,
        jinja_loaders = myloaders,
    ))
```

Remember to link the static files too!!!

This option can be used mixed with the Git one :D


# Screenshots

And here you are some screenshots:

![Default Waterfall mini] - ![BBB Waterfall mini]

Full sized: [Default Waterfall] - [BBB Waterfall]

![Default Grid mini] - ![BBB Grid mini]

Full sized: [Default Grid] - [BBB Grid]

![Default TGrid mini] - ![BBB TGrid mini]

Full sized: [Default TGrid] - [BBB TGrid]

![Default Builders mini] - ![BBB Builders mini]

Full sized: [Default Builders] - [BBB Builders]

![Default Slaves mini] - ![BBB Slaves mini]

Full sized: [Default Slaves] - [BBB Slaves]


[Default Waterfall mini]: http://magmax.org/images/bbb/default_waterfall_mini.png
[Default Grid mini]:      http://magmax.org/images/bbb/default_grid_mini.png
[Default TGrid mini]:     http://magmax.org/images/bbb/default_tgrid_mini.png
[Default Builders mini]:  http://magmax.org/images/bbb/default_builders_mini.png
[Default Slaves mini]:    http://magmax.org/images/bbb/default_slaves_mini.png
[Default Waterfall]:      http://magmax.org/images/bbb/default_waterfall.png
[Default Grid]:           http://magmax.org/images/bbb/default_grid.png
[Default TGrid]:          http://magmax.org/images/bbb/default_tgrid.png
[Default Builders]:       http://magmax.org/images/bbb/default_builders.png
[Default Slaves]:         http://magmax.org/images/bbb/default_slaves.png
[BBB Waterfall mini]:     http://magmax.org/images/bbb/bbb_waterfall_mini.png
[BBB Grid mini]:          http://magmax.org/images/bbb/bbb_grid_mini.png
[BBB TGrid mini]:         http://magmax.org/images/bbb/bbb_tgrid_mini.png
[BBB Builders mini]:      http://magmax.org/images/bbb/bbb_builders_mini.png
[BBB Slaves mini]:        http://magmax.org/images/bbb/bbb_slaves_mini.png
[BBB Waterfall]:          http://magmax.org/images/bbb/bbb_waterfall.png
[BBB Grid]:               http://magmax.org/images/bbb/bbb_grid.png
[BBB TGrid]:              http://magmax.org/images/bbb/bbb_tgrid.png
[BBB Builders]:           http://magmax.org/images/bbb/bbb_builders.png
[BBB Slaves]:             http://magmax.org/images/bbb/bbb_slaves.png

[BuildBot]:               http://buildbot.net/ "BuildBot page"
[Bootstrap]:              http://twitter.github.io/bootstrap/ "Twitter Bootstrap site"
[BuildBot Manual]:        http://docs.buildbot.net/0.8.7/manual/cfg-statustargets.html#configuration

