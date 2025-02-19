---
layout: default
title: Troubleshooting
tags: developers_troubleshooting
sequence: 10
summary: Solving problems that might arise when trying to run metasfresh from eclipse
lang: en
ref: developers_troubleshooting
---

This article assumes that you more or less followed the "Getting Started" documentation, and ran into problems.

## Eclipse doesn't properly show java packages and classes

Check if you have the java perspective open. In the following screenshot, the Java-EE perspective is open instead:

![troubleshooting_ide_eclipse_java_ee_perspective]({{ site.github.url }}/images/developers/troubleshooting_ide_eclipse_java_ee_perspective.png)

The buttons are visible on the upper right area of your screenshot.
We never used the Java EE perspective, so frankly we can't even tell you if it makes sense to try and get it to work.

## Eclipse shows me thousands of errors and I don't even know where to start

Allmost every project depends on antoher project. Oftentimes, if one of the "root" projects has a possibly trivial problem, this cascades to thousands of secondary problems in the downstream projects.

So, in order to apropoch this kind of problem, it makes sense to go to the root.

We recoment to first check the following projects:

* [metasfresh-parent](https://github.com/metasfresh/metasfresh-parent) (a repo of its own)
* [de.metas.parent](https://github.com/metasfresh/metasfresh/tree/master/de.metas.parent) (comes with the metasfresh repo)
* [de.metas.util](https://github.com/metasfresh/metasfresh/tree/master/backend/de.metas.util) (comes with the metasfresh repo)
* [de.metas.adempiere.adempiere.base](https://github.com/metasfresh/metasfresh/tree/master/backend/de.metas.adempiere.adempiere/base) (also comes with the metasfresh repo)

## So how can I make eclipse showing only the current project's errors?

You can configure eclipse to only show errors from the project that is currently selected.

* To to that, first open the "Problems" view by clicking on its tab:

![troubleshooting_ide_eclipse_problems_10]({{ site.github.url }}/images/developers/troubleshooting_ide_eclipse_problems_10.png)

* Then, open the "Configure.." dialog:

![troubleshooting_ide_eclipse_configure_problems_20_open_configure]({{ site.github.url }}/images/developers/troubleshooting_ide_eclipse_configure_problems_20_open_configure.png)

* ...and change the setting such that only errors from the currently selecte project are displayed:

![troubleshooting_ide_eclipse_configure_problems_30_do_configure]({{ site.github.url }}/images/developers/troubleshooting_ide_eclipse_configure_problems_30_do_configure.png)

## I Get a warning about `Version is duplicate of parent version`

You can ignore the warning. eclipse's maven plugin thinks one should remove the duplication version, but we need it. Details [here](https://docs.metasfresh.org/pages/infrastructure/ci_en).

## I get an error saying `Unsupported major.minor version 52.0`

This error indicates that you are trying to run the metasfresh code with a java version that is less than java-8.

To fix it, make sure to run with java-8

## I get an error about `Plugin execution not covered by lifecycle configuration`

It looks like this:

![troubleshooting_ide_eclipse_missing_m2e_provider]({{ site.github.url }}/images/developers/troubleshooting_ide_eclipse_missing_m2e_provider.png)

It means that your eclipse instalation is missing a particular m2e component. You can search for it in the eclipse market place (it's for free) and install it by right-clicking on the problem and following the "Quick-Fix" item.
