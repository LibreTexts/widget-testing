# What is this?

Repo for cataloging the behavior of widgets in Thebe, libretexts, and on jupyterhub. Reference to [this issue](https://github.com/LibreTexts/metalc/issues/136#issue-575899944).

This repository was migrated over from the now archived [sandertyu/widgetstuffs](https://github.com/sandertyu/widgetstuffs) repository.

# How to use

Use `python3 -m http.server` within the `Thebe/` directory and navigate to localhost:8000 to see the Thebe results. Change the url to the different html pages within the `Thebe/` directory or use the directory listing to view them.

# Checklist

|Widget|Thebe|JupyterHub|Libretexts|
|-|-|-|-|
|bokeh|Does not display any output, says "JavaScript output is disabled in JupyterLab"|Works properly|Does not display any output, says "JavaScript output is disabled in JupyterLab" (same as Thebe)|
|ipympl|Works properly, needs some handlers and `Awesome Font`|Works properly|Works properly|
|ipyleaflet|Works properly|Works properly|Displays, but cells cannot communicate as seen in heatmap example (this is a limitation of current CKeditor plugin)|
|pythreejs|Works properly|Works properly|Works properly (heavily limited by lack of cell communication)|
|ipywidgets|`interact()` does not display the widget. Some widgets work on their own (BoundedIntText), and others do not (IntSlider).|Works Properly|`interact()` does not display the widget, same error as Thebe|
|bqplot|Needs `Awesome Font` and pan zoom button to move the plot around does not work. Otherwise seems to work properly|Works properly|Pan zoom button does not work, but save button does, same as Thebe|
|ipyvolume|figure displays, but sliders and buttons do not render properly, also gives a python error|gives same error as ipyvolume-image, very buggy in general but does "work"|buttons do render but sliders do not, same issues as Thebe (not installed)|
|nglview|buttons do not display so the animation cannot be run, otherwise works properly. **Note:** This issue seems to be solved in a later version of Thebe. |Works properly|Does not display animation slider, but everything (including animation) works properly otherwise (not installed)|
|ipycytoscape|Works properly|Works properly|Works properly (not installed)|
|ipygany|Works properly except for ipywidget sliders do not show (if you choose to use them with [thresholds, for example](https://ipygany.readthedocs.io/en/latest/api_reference/threshold.html)|||
|plotly|Works properly|Works properly|Plots do not display|

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

## plotly

### In Thebe (works properly)
![plotly in thebe](/screenshots/plotly-thebe.png)

### In Jupyterlab (works properly)
![plotly in jupyterlab](/screenshots/plotly-jup.png)

### In LibreTexts (doesn't show plots)
![plotly in libretexts](/screenshots/plotly-libre.png)
