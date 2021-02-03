# What is this?

Repo for cataloging the behavior of widgets in Thebe, Libretexts, and on JupyterHub. Reference to [this issue](https://github.com/LibreTexts/metalc/issues/136#issue-575899944).

This repository was migrated over from the now archived [sandertyu/widgetstuffs](https://github.com/sandertyu/widgetstuffs) repository.

# How to use

Use `python -m http.server` (`python3` if `python` is an alias for python v2) within the `Thebe/` directory and navigate to localhost:8000 in your web browser to see the Thebe results. Change the url to the different html pages within the `Thebe/` directory or use the directory listing to view them.

# Widget Status

## Widgets with Thebe errors

Widgets with errors in Thebe will have errors on Libretexts because CKEditor Binder Plugin uses Thebe to insert code cells into the HTML webpage.

### [Bokeh](https://github.com/bokeh/bokeh)

Known bugs;

  - Displays "Javascript output is disabled in JupyterLab" when the widgets are ran

Debugging procedures;

  - Test `bokeh.html` using different binder repositories
    - ~~[default-env 2.3.2](https://github.com/LibreTexts/default-env/tree/2.3.2)~~
    - ~~[binder-examples/bokeh](https://github.com/binder-examples/bokeh)~~

### [ipywidgets](https://github.com/jupyter-widgets/ipywidgets)

Known bugs;

  - Some widgets work and others don't, `interact()` function does not work at all

Debugging procedures;

  - TODO

### [bqplot](https://github.com/bqplot/bqplot)

Known bugs;

  - [PR to fix on Thebe](https://github.com/executablebooks/thebe/pull/330), buttons were not working properly

### [ipyvolume](https://github.com/maartenbreddels/ipyvolume)

Known bugs;

  - Sliders and buttons do not render properly, very buggy in general

Debugging procedures;

  - TODO

### [nglview](https://github.com/nglviewer/nglview)

Known bugs;

  - Binder image to run the widgets no longer builds, need to retest. Questionably worked before

Debugging procedures;

  - TODO

### [ipygany](https://github.com/QuantStack/ipygany)

Known bugs;

  - ipywidget sliders do not show (if you choose to use them with [thresholds, for example](https://ipygany.readthedocs.io/en/latest/api_reference/threshold.html))

Debugging procedures;

  - TODO

## Widgets with problems on Libretexts

These widgets work properly in Thebe but not so well on Libretexts due to limitations of the CKEditor Binder Plugin. Cells cannot retroactively change the output of another cell in CKEditor Binder Plugin, so these widgets are severely limited. See [this issue for more info](https://github.com/LibreTexts/ckeditor-binder-plugin/issues/107). Theoretically this issue effects all widgets on Libretexts, but these ones seem most impacted due to how they are used.

### [ipyleaflet](https://github.com/jupyter-widgets/ipyleaflet)

Known bugs;

  - For instance, if you try to add a heatmap to the output of an earlier cell, it will not cause any change

Debugging procedures;

  - TODO

### [pythreejs](https://github.com/jupyter-widgets/pythreejs)

Known bugs;
 
 - Same as ipyleaflet

Debugging procedures;

  - TODO

## Widgets that work or have been fixed

  - [ipympl](https://github.com/matplotlib/ipympl)
  - [ipycytoscape](https://github.com/Quantstack/ipycytoscape)
  - [plotly](https://github.com/plotly/plotly.py)

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

## ipyvolume

### In Thebe (missing button rendering and no sliders as well as python error. buttons probably could be loaded with external scripts, but the sliders are likely bugged the same way `interact()` from ipywidgets is)
![ipyvolume in thebe](/screenshots/ipyvolume-thebe.png)
### In JupyterLab (Everything renders properly, but there is still a python error. this is just buggy source code)
![ipyvolume in jupyterlab](/screenshots/ipyvolume-jup.png)
### In Libretexts (buttons render but sliders do not, similar to Thebe)
![ipyvolume in libretexts](/screenshots/ipyvolume-libre.png)

## nglview

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

## ipygany

### In Thebe (visual loads fine, ipywidget sliders will not)
![ipygany in thebe](/screenshots/ipygany-thebe.png)
