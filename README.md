# What is this?

Repo for cataloging the behavior of widgets in Thebe, Libretexts, and on JupyterHub. Reference to [this issue](https://github.com/LibreTexts/metalc/issues/136#issue-575899944).

This repository is built to be [repo2docker compatible](https://repo2docker.readthedocs.io/en/latest/config_files.html). That means you can build it on https://binder.libretexts.org/ by specifying `LibreTexts/widget-testing` in the repository section and choosing whichever git branch you would like. Make sure that the `environment.yml` file in this directory reflects the one you want to build, don't change the file name, and that the contents of the file contains no `name: ` section at the top. You can find other conda-environment `.yml` files in the `conda-environments` directory.

This repository was migrated over from the now archived [sandertyu/widgetstuffs](https://github.com/sandertyu/widgetstuffs) repository.

# How to use

Use `python -m http.server` (`python3` if `python` is an alias for python v2) within the `Thebe/` directory and navigate to localhost:8000 in your web browser to see the Thebe results. Change the url to the different html pages within the `Thebe/` directory or use the directory listing to view them.

# Widget Status

Below is a table which outlines the general functionality of each widget on each platform. Where applicable, the latest version of the package environment to be verified for that platform has been specified.

  - :heavy_check_mark: means that the widget works exactly as expected 
  - :o: means that the widget itself is fine, but the platform makes it difficult to use
  - :x: means that the widget basically does not work at all, not displaying or something of that sort 
  - :question: means that the status has not been verified. 

The `JupyterLab=2` column means that the widget has been tested in the specified environment which runs on `JupyterLab=2`, and the same for the `JupyterLab=3` column. The `Thebe` column represents widgets tested on HTML pages in the `Thebe/` directory of this repository, or on the example pages for [Thebe's documentation](https://thebelab.readthedocs.io/en/latest/). `CKEditor Binder Plugin` represents running the widget while in the plugin's development mode. Widgets tested on a page in `query.libretexts.org` are in that respective column, and then the libraries which a widget has been verified to be working (or not) on libretexts.org are outlined in the `libretexts.org libraries` column. 

Each widget is tested using the code used in the `<pre data-executable="true" data-language="python">` Thebe cells of the HTML pages contained in the `Thebe/` folder.

| Widget | JupyterLab=2 | JupyterLab=3 | Thebe | CKEditor Binger Plugin | query.libretexts.org | libretexts.org libraries |
|-|-|-|-|-|-|-|
| Bokeh | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [widget-testing](https://github.com/LibreTexts/widget-testing/tree/all-widgets-jlab3) | :x: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :x: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :x: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :x: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) (no specific library) |
| ipywidgets | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [widget-testing](https://github.com/LibreTexts/widget-testing/tree/all-widgets-jlab3) | :o: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :o: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :o: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :o: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) (no specific library)|
| bqplot | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [widget-testing](https://github.com/LibreTexts/widget-testing/tree/all-widgets-jlab3) | Waiting on Thebe PR #330 | Waiting on Thebe PR #330 | Waiting on Thebe PR #330 | Waiting on Thebe PR #330 |
| ipyleaflet | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [widget-testing](https://github.com/LibreTexts/widget-testing/tree/all-widgets-jlab3) | :heavy_check_mark: [jupyter-widgets/ipyleaflet 0.13.3](https://thebelab.readthedocs.io/en/latest/examples/ipyleaflet_example.html) and default-env 2.3.2 | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) (with specific css rule) | :o: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) |
| pythreejs | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2)| :heavy_check_mark: [widget-testing](https://github.com/LibreTexts/widget-testing/tree/all-widgets-jlab3) | :o: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) `render()` calls do not display | :o: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) `render()` calls do not display | :o: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) `render()` calls do not display | :o: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) (no specific library) |
| ipympl | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [widget-testing](https://github.com/LibreTexts/widget-testing/tree/all-widgets-jlab3) | :heavy_check_mark: [matplotlib/ipympl 0.6.1](https://thebelab.readthedocs.io/en/latest/examples/ipympl_example.html) and default-env 2.3.2 | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) (Chemistry Library) |
| plotly | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [widget-testing](https://github.com/LibreTexts/widget-testing/tree/all-widgets-jlab3) | :heavy_check_mark: [plotly/plotly.py doc-prod](https://thebelab.readthedocs.io/en/latest/examples/plotly-example.html) and default-env 2.3.2 | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) (Chemistry Library) |
| ipycytoscape | :heavy_check_mark: [default-env 2.3.3](https://github.com/LibreTexts/default-env/tree/2.3.3) | :heavy_check_mark: [widget-testing](https://github.com/LibreTexts/widget-testing/tree/all-widgets-jlab3) | :x: [QuantStack/ipycytoscape 1.0.4](https://thebelab.readthedocs.io/en/latest/examples/ipycytoscape_example.html) but 1.2.0 works | :x: [default-env 2.3.3](https://github.com/LibreTexts/default-env/tree/2.3.3) | :x: [default-env 2.3.3](https://github.com/LibreTexts/default-env/tree/2.3.3) | :x: [default-env 2.3.3](https://github.com/LibreTexts/default-env/tree/2.3.3) (Chemistry Library) |
| ipyvolume | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [widget-testing](https://github.com/LibreTexts/widget-testing/tree/all-widgets-jlab3) (does not work in JupyterLab) | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) (Chemistry Library) |
| ipygany | :heavy_check_mark: [QuantStack/ipygany 0.5.0](https://github.com/QuantStack/ipygany/tree/0.5.0) | :heavy_check_mark: [widget-testing](https://github.com/LibreTexts/widget-testing/tree/all-widgets-jlab3) | :heavy_check_mark: [QuantStack/ipygany 0.5.0](https://github.com/QuantStack/ipygany/tree/0.5.0) | :heavy_check_mark: [QuantStack/ipygany 0.5.0](https://github.com/QuantStack/ipygany/tree/0.5.0) | :heavy_check_mark: [QuantStack/ipygany 0.5.0](https://github.com/QuantStack/ipygany/tree/0.5.0) | :question: |
| nglview | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [widget-testing](https://github.com/LibreTexts/widget-testing/tree/all-widgets-jlab3) | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) | :heavy_check_mark: [default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2) (Chemistry Library) |

See the sections dedicated to each widget below for more information about the widgets labelled with :o: and :x:.

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

### [pythreejs](https://github.com/jupyter-widgets/pythreejs)

Known bugs;
 
 - Thebe can display basic widgets as shown in the first cell of `Thebe/pythreejs.html`, but more complicated mechanisms like using the `display()` function yield `error displaying widget errors` like in ipywidgets.

Debugging procedures;

  - TODO

### [ipycytoscape](https://github.com/Quantstack/ipycytoscape)

I don't even know anymore. Seems to only work consistently with version 1.2.0 which requires jupyterlab=3

## Widgets with problems on Libretexts

These widgets work properly in Thebe but not so well on Libretexts due to limitations of the CKEditor Binder Plugin. Cells cannot retroactively change the output of another cell in CKEditor Binder Plugin, so these widgets are severely limited. See [this issue for more info](https://github.com/LibreTexts/ckeditor-binder-plugin/issues/107). Theoretically this issue effects all widgets on Libretexts, but these ones seem most impacted due to how they are used.

### [ipyleaflet](https://github.com/jupyter-widgets/ipyleaflet)

Known bugs;

  - Overlays do not show.

Debugging procedures;

  - The current max-width css rule for `canvas` html objects causes map overlays to not show. Query currently has a fix on it that allows it to work.

## Widgets that work or have been fixed

### [ipympl](https://github.com/matplotlib/ipympl)

### [plotly](https://github.com/plotly/plotly.py)

### [ipyvolume](https://github.com/maartenbreddels/ipyvolume)

### [ipygany](https://github.com/QuantStack/ipygany) (not currently in use in default-env)

### [nglview](https://github.com/nglviewer/nglview)

# Screenshots for widgets with bugs

## ipyleaflet

### In Thebe (works properly)
![ipyleaflet in Thebe](/screenshots/ipyleaflet-thebe.png)
### In Libretexts (css rule that prevents the overlay from showing up)
![ipyleaflet in libretexts](/screenshots/ipyleaflet-libre.png)

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
