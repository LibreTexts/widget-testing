# What is this?

Repo for cataloging the behavior of widgets in Thebe, Libretexts, and on JupyterHub. Reference to [this issue](https://github.com/LibreTexts/metalc/issues/136#issue-575899944).

This repository is built to be [repo2docker compatible](https://repo2docker.readthedocs.io/en/latest/config_files.html). That means you can build it on https://binder.libretexts.org/ by specifying `LibreTexts/widget-testing` in the repository section and choosing whichever git branch you would like. Make sure that the `environment.yml` file in this directory reflects the one you want to build, don't change the file name, and that the contents of the file contains no `name: ` section at the top. You can find other conda-environment `.yml` files in the `conda-environments` directory.

This repository was migrated over from the now archived [sandertyu/widgetstuffs](https://github.com/sandertyu/widgetstuffs) repository.

# How to use

Use `python -m http.server` (`python3` if `python` is an alias for python v2) within the `Thebe/` directory and navigate to localhost:8000 in your web browser to see the Thebe results. Change the url to the different html pages within the `Thebe/` directory or use the directory listing to view them.

# Widget Status

Below is a table which outlines the general functionality of each widget on each platform. :heavy_check_mark: means that the widget works as expected, :white_check_mark: means that only some functionality works, :x: means that the widget basically does not work at all, and :question: means that the status has not been verified. See the sections dedicated to each widget below for more information about the widgets labelled with :white_check_mark: and :x:.

| Widget | JupyterLab=2 | JupyterLab=3 | Thebe | CKEditor Binger Plugin | libretexts.org |
|-|-|-|-|-|-|
| Bokeh | :heavy_check_mark: | :question: | :x: | :x: | :x: |
| ipywidgets | :heavy_check_mark: | :question: | :white_check_mark: | :white_check_mark: | :white_check_mark: |
| bqplot | :heavy_check_mark: | :question: | Waiting on Thebe PR #330 | Waiting on Thebe PR #330 | Waiting on Thebe PR #330 |
| ipyleaflet | :heavy_check_mark: | :question: | :heavy_check_mark: | :white_check_mark: | :white_check_mark: |
| pythreejs | :heavy_check_mark: | :question: | :heavy_check_mark: | :white_check_mark: | :white_check_mark: |
| ipympl | :heavy_check_mark: | :question: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| plotly | :heavy_check_mark: | :question: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| ipycytoscape | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| ipyvolume | :heavy_check_mark: |:question: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| ipygany | :heavy_check_mark: | :question: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| nglview | :heavy_check_mark: | :question: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |

## Widgets with Thebe errors

Widgets with errors in Thebe will have errors on Libretexts because CKEditor Binder Plugin uses Thebe to insert code cells into the HTML webpage.

### [Bokeh](https://github.com/bokeh/bokeh)

Known bugs;

  - Displays "Javascript output is disabled in JupyterLab" when the widgets are ran

Debugging procedures;

  - Test `bokeh.html` using different binder repositories (crossed out means tested, repo is probably not the issue)
    - ~~[default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2)~~
    - ~~[binder-examples/bokeh](https://github.com/binder-examples/bokeh)~~
  - Thebe [issue #112](https://github.com/executablebooks/thebe/issues/112)
    - The error message occurs in [widgets.ts](https://github.com/jupyterlab/jupyterlab/blob/master/packages/rendermime/src/widgets.ts#L421) of the jupyterlab code
      - Info about the [render()](https://reactjs.org/) function call
      - The source for `IRenderMime` code is in the [rendermime-interfaces](https://github.com/LibreTexts/widget-testing/tree/master/rendermime-interfaces) folder of this repository
      - The source for `translator` code comes from `ITranslator` which is downloaded in the [translation](https://github.com/LibreTexts/widget-testing/tree/master/translation) folder of this repository
    - Web console shows that `https://cdn.bokeh.org/bokeh/release/bokeh-gl-2.2.3.min.js` is not loading properly
      - Previous version `https://cdn.bokeh.org/bokeh/release/bokeh-gl-2.1.1.min.js` does get loaded, but same Javascript output disabled message
    - Sometimes the errors in the web console do not show up at all. Don't see any consistent patterns to this.

### [ipywidgets](https://github.com/jupyter-widgets/ipywidgets)

Known bugs;

  - Some widgets work and others don't, `interact()` function does not work at all

Debugging procedures;

  - Thebe [issue #111](https://github.com/executablebooks/thebe/issues/111)
  - Web console says `future.js:179 Uncaught (in promise) Error: Canceled future for kernel_info_request message before replies were done`
    - The error message is triggered by `future.js` which is built from [future.ts](https://github.com/jupyterlab/jupyterlab/blob/master/packages/services/src/kernel/future.ts#L196) in jupyterlab
      - The message printed using the code above contains `kernel_info_request` [from default.ts](https://github.com/jupyterlab/jupyterlab/blob/master/packages/services/src/kernel/default.ts#L558)
  - Sometimes the errors in the web console do not show up at all. Don't see any consistent patterns to this.
  
### [bqplot](https://github.com/bqplot/bqplot)

Known bugs;

  - [PR to fix on Thebe](https://github.com/executablebooks/thebe/pull/330), buttons were not working properly

## Widgets with problems on Libretexts

These widgets work properly in Thebe but not so well on Libretexts due to limitations of the CKEditor Binder Plugin. Cells cannot retroactively change the output of another cell in CKEditor Binder Plugin, so these widgets are severely limited. See [this issue for more info](https://github.com/LibreTexts/ckeditor-binder-plugin/issues/107). Theoretically this issue effects all widgets on Libretexts, but these ones seem most impacted due to how they are used.

### [ipyleaflet](https://github.com/jupyter-widgets/ipyleaflet)

Known bugs;

  - ~~For instance, if you try to add a heatmap to the output of an earlier cell, it will not cause any change.~~ 

Debugging procedures;

  - Tested with ckeditor binder plugin locally - when a new heatmap cell is added, it works if you rerun the previous cell containing the map, and then the heatmap cell. (does not work if you only run the new cell containing the heat map)
  - Tested with thebe locally, default-env 2.3.2 - works fine.

### [pythreejs](https://github.com/jupyter-widgets/pythreejs)

Known bugs;
 
 - Same as ipyleaflet

Debugging procedures;

  - TODO

## Widgets that work or have been fixed

### [ipympl](https://github.com/matplotlib/ipympl)

### [plotly](https://github.com/plotly/plotly.py)

### [ipycytoscape](https://github.com/Quantstack/ipycytoscape)

### [ipyvolume](https://github.com/maartenbreddels/ipyvolume)

### [ipygany](https://github.com/QuantStack/ipygany) (not currently in use in default-env)

### [nglview](https://github.com/nglviewer/nglview)

# Screenshots for widgets with bugs

## ipyleaflet

### In Thebe (works properly)
![ipyleaflet in Thebe](/screenshots/ipyleaflet-thebe.png)
### In Libretexts (cells cannot communicate, so the heatmap and timelapse do not work)*
![ipyleaflet in libretexts](/screenshots/ipyleaflet-libre.png)
*may be a different issue since the heatmap and timelapse do not work even if in the same code cell.

## ipywidgets

### In Thebe (`interact()` does not work, and some widgets give an error when trying to display)
![ipywidgets in thebe with interact()](/screenshots/ipywidgets-thebe-interact.png)
![ipywidgets in thebe with error widget](/screenshots/ipywidgets-thebe-error.png)
### In JupyterLab (works properly)
![ipywidgets in jupyterlab with interact()](/screenshots/ipywidgets-jup-interact.png)
### In Libretexts (same issues as in Thebe)
![ipywidgets in libretexts with interact()](/screenshots/ipywidgets-libre-interact.png)
![ipywidgets in libretexts with error widget](/screenshots/ipywidgets-libre-error.png)

## bqplot

### In JupyerLab (works properly)
![bqplot in jupyterlab](/screenshots/bqplot-jup.png)
### In Libretexts (pan zoom button does not work, so cannot move the plot around. save button does work)
![bqplot in libretexts](/screenshots/bqplot-libre.png)

## nglview

### In ckeditor binder plugin (works properly)
![nglview in ckeditor binder plugin](/screenshots/nglview-thebe-updated.jpg)
### In Thebe (buttons do not display, cannot run the animation)
![nglview in thebe](/screenshots/nglview-thebe.png)
### In JupyerLab (works properly)
![nglview in jupyterlab](/screenshots/nglview-jup.png)
### In Libretexts (buttons do display but not the animation slider, graphic/animation works properly and can be toyed with)
![nglview in libretexts](/screenshots/nglview-libre.png)


## bokeh

### In Thebe (Javascript error)
![bokeh in thebe](/screenshots/bokeh-thebe-error.png)

### In JupyterLab (works properly)
![bokeh in jupyterlab](/screenshots/bokeh-jup.png)
