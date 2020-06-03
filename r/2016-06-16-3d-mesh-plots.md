---
description: How to make interactive 3D mesh plots in R.
display_as: 3d_charts
language: r
layout: base
name: 3D Mesh Plots
order: 4
output:
  html_document:
    keep_md: true
page_type: example_index
permalink: r/3d-mesh/
redirect_from: r/3d-mesh-plots/
thumbnail: thumbnail/3d-mesh.jpg
---


### Basic 3D Mesh Plot


```r
library(plotly)

x <- runif(50, 0, 1)
y <- runif(50, 0, 1)
z <- runif(50, 0, 1)

fig <- plot_ly(x = ~x, y = ~y, z = ~z, type = 'mesh3d')

fig
```

<div id="htmlwidget-1c3c80c32e9607e7fafe" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-1c3c80c32e9607e7fafe">{"x":{"visdat":{"654f278fd31f":["function () ","plotlyVisDat"]},"cur_data":"654f278fd31f","attrs":{"654f278fd31f":{"x":{},"y":{},"z":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"mesh3d"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"scene":{"xaxis":{"title":"x"},"yaxis":{"title":"y"},"zaxis":{"title":"z"}},"hovermode":"closest","showlegend":false,"legend":{"yanchor":"top","y":0.5}},"source":"A","config":{"showSendToCloud":false},"data":[{"colorbar":{"title":"z","ticklen":2,"len":0.5,"lenmode":"fraction","y":1,"yanchor":"top"},"colorscale":[["0","rgba(68,1,84,1)"],["0.0416666666666667","rgba(70,19,97,1)"],["0.0833333333333333","rgba(72,32,111,1)"],["0.125","rgba(71,45,122,1)"],["0.166666666666667","rgba(68,58,128,1)"],["0.208333333333333","rgba(64,70,135,1)"],["0.25","rgba(60,82,138,1)"],["0.291666666666667","rgba(56,93,140,1)"],["0.333333333333333","rgba(49,104,142,1)"],["0.375","rgba(46,114,142,1)"],["0.416666666666667","rgba(42,123,142,1)"],["0.458333333333333","rgba(38,133,141,1)"],["0.5","rgba(37,144,140,1)"],["0.541666666666667","rgba(33,154,138,1)"],["0.583333333333333","rgba(39,164,133,1)"],["0.625","rgba(47,174,127,1)"],["0.666666666666667","rgba(53,183,121,1)"],["0.708333333333333","rgba(79,191,110,1)"],["0.75","rgba(98,199,98,1)"],["0.791666666666667","rgba(119,207,85,1)"],["0.833333333333333","rgba(147,214,70,1)"],["0.875","rgba(172,220,52,1)"],["0.916666666666667","rgba(199,225,42,1)"],["0.958333333333333","rgba(226,228,40,1)"],["1","rgba(253,231,37,1)"]],"showscale":true,"x":[0.0699980747886002,0.441337105818093,0.945550182601437,0.59201123402454,0.925039197318256,0.123313255608082,0.115283670835197,0.230554095935076,0.53001876338385,0.55229103891179,0.769682549871504,0.171638440806419,0.874574840301648,0.296778661431745,0.673918165732175,0.701382196741179,0.284323644824326,0.432932584080845,0.493955498328432,0.508811192587018,0.690258978400379,0.833515796810389,0.328896149760112,0.259089672472328,0.0655959704890847,0.520227555651218,0.804850645363331,0.483196729561314,0.676664573606104,0.501324981218204,0.433556554140523,0.655255312798545,0.0675081766676158,0.70742576289922,0.0205440169665962,0.260061088483781,0.150268580997363,0.98544930643402,0.903496828395873,0.675607966259122,0.375760850263759,0.177889588987455,0.591173508903012,0.282881444785744,0.527763616526499,0.416044257814065,0.890883688814938,0.555142996832728,0.560424614930525,0.443714370485395],"y":[0.720113841583952,0.363972314633429,0.681864996673539,0.905533761251718,0.139296469045803,0.761672451393679,0.329313516383991,0.336060129338875,0.188665259163827,0.0724320425651968,0.654071953846142,0.883644391549751,0.0724481244105846,0.562860067700967,0.00691750785335898,0.373521608533338,0.0618557177949697,0.869291590992361,0.336536790244281,0.641611500643194,0.516210502246395,0.328720619669184,0.741528483340517,0.157906928332523,0.434013965073973,0.439367198618129,0.448291705688462,0.441268234979361,0.0757968046236783,0.650997693417594,0.425127887632698,0.100676615489647,0.748284338973463,0.339129249099642,0.624194584321231,0.357150484574959,0.832770881941542,0.753447049297392,0.168405897682533,0.109802863327786,0.300424608169124,0.410733956145123,0.190508137689903,0.457037311280146,0.76328265434131,0.850025133928284,0.674348138971254,0.145871355663985,0.7255080237519,0.0831114237662405],"z":[0.171104162698612,0.0740976117085665,0.628282230813056,0.670647801132873,0.94399949000217,0.159917592303827,0.792474436108023,0.95883373869583,0.793701483169571,0.585924442391843,0.986953677842394,0.453730655834079,0.229192967992276,0.937145492061973,0.411933494964615,0.562093598069623,0.183817910030484,0.446313546039164,0.112850387115031,0.138650168897584,0.802524316357449,0.823166692396626,0.676757037872449,0.176514155697078,0.458513105520979,0.135343362111598,0.00614595552906394,0.128639419330284,0.143641236703843,0.778719157446176,0.723143668379635,0.258925689384341,0.62641339795664,0.817188001936302,0.342661360511556,0.657391404267401,0.250885701272637,0.715565877500921,0.770066387718543,0.479089398868382,0.449925881810486,0.277031551115215,0.502704221289605,0.525343709858134,0.415061228908598,0.590523683931679,0.764273818116635,0.0879822948481888,0.536959134507924,0.770103089977056],"type":"mesh3d","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Tetrahedron Mesh Plot


```r
library(plotly)

fig <- plot_ly(type = 'mesh3d',
  x = c(0, 1, 2, 0),
  y = c(0, 0, 1, 2),
  z = c(0, 2, 0, 1),
  i = c(0, 0, 0, 1),
  j = c(1, 2, 3, 2),
  k = c(2, 3, 1, 3),
  intensity = c(0, 0.33, 0.66, 1),
  color = c(0, 0.33, 0.66, 1),
  colors = colorRamp(c("red", "green", "blue"))
)

fig
```

<div id="htmlwidget-1e014836933e2309ee19" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-1e014836933e2309ee19">{"x":{"visdat":{"654f7268d1f6":["function () ","plotlyVisDat"]},"cur_data":"654f7268d1f6","attrs":{"654f7268d1f6":{"x":[0,1,2,0],"y":[0,0,1,2],"z":[0,2,0,1],"i":[0,0,0,1],"j":[1,2,3,2],"k":[2,3,1,3],"intensity":[0,0.33,0.66,1],"color":[0,0.33,0.66,1],"colors":["function (x) ","roundcolor(cbind(palette[[1L]](x), palette[[2L]](x), palette[[3L]](x), ","    if (alpha) palette[[4L]](x))) * 255"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"mesh3d"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"scene":{"xaxis":{"title":[]},"yaxis":{"title":[]},"zaxis":{"title":[]}},"hovermode":"closest","showlegend":false,"legend":{"yanchor":"top","y":0.5}},"source":"A","config":{"showSendToCloud":false},"data":[{"colorbar":{"title":"","ticklen":2,"len":0.5,"lenmode":"fraction","y":1,"yanchor":"top"},"colorscale":[["0","rgba(255,0,0,1)"],["0.0416666666666667","rgba(234,21,0,1)"],["0.0833333333333333","rgba(212,42,0,1)"],["0.125","rgba(191,64,0,1)"],["0.166666666666667","rgba(170,85,0,1)"],["0.208333333333333","rgba(149,106,0,1)"],["0.25","rgba(128,128,0,1)"],["0.291666666666667","rgba(106,149,0,1)"],["0.333333333333333","rgba(85,170,0,1)"],["0.375","rgba(64,191,0,1)"],["0.416666666666667","rgba(43,212,0,1)"],["0.458333333333333","rgba(21,234,0,1)"],["0.5","rgba(0,255,0,1)"],["0.541666666666667","rgba(0,234,21,1)"],["0.583333333333333","rgba(0,213,42,1)"],["0.625","rgba(0,191,64,1)"],["0.666666666666667","rgba(0,170,85,1)"],["0.708333333333333","rgba(0,149,106,1)"],["0.75","rgba(0,128,128,1)"],["0.791666666666667","rgba(0,106,149,1)"],["0.833333333333333","rgba(0,85,170,1)"],["0.875","rgba(0,64,191,1)"],["0.916666666666667","rgba(0,43,212,1)"],["0.958333333333333","rgba(0,21,234,1)"],["1","rgba(0,0,255,1)"]],"showscale":true,"x":[0,1,2,0],"y":[0,0,1,2],"z":[0,2,0,1],"i":[0,0,0,1],"j":[1,2,3,2],"k":[2,3,1,3],"intensity":[0,0.33,0.66,1],"type":"mesh3d","marker":{"line":{"colorbar":{"title":"","ticklen":2},"cmin":0,"cmax":1,"colorscale":[["0","rgba(255,0,0,1)"],["0.0416666666666667","rgba(234,21,0,1)"],["0.0833333333333333","rgba(212,42,0,1)"],["0.125","rgba(191,64,0,1)"],["0.166666666666667","rgba(170,85,0,1)"],["0.208333333333333","rgba(149,106,0,1)"],["0.25","rgba(128,128,0,1)"],["0.291666666666667","rgba(106,149,0,1)"],["0.333333333333333","rgba(85,170,0,1)"],["0.375","rgba(64,191,0,1)"],["0.416666666666667","rgba(43,212,0,1)"],["0.458333333333333","rgba(21,234,0,1)"],["0.5","rgba(0,255,0,1)"],["0.541666666666667","rgba(0,234,21,1)"],["0.583333333333333","rgba(0,213,42,1)"],["0.625","rgba(0,191,64,1)"],["0.666666666666667","rgba(0,170,85,1)"],["0.708333333333333","rgba(0,149,106,1)"],["0.75","rgba(0,128,128,1)"],["0.791666666666667","rgba(0,106,149,1)"],["0.833333333333333","rgba(0,85,170,1)"],["0.875","rgba(0,64,191,1)"],["0.916666666666667","rgba(0,43,212,1)"],["0.958333333333333","rgba(0,21,234,1)"],["1","rgba(0,0,255,1)"]],"showscale":false,"color":[0,0.33,0.66,1]}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Cube Mesh Plot


```r
library(plotly)

fig <- plot_ly(type = 'mesh3d',
  x = c(0, 0, 1, 1, 0, 0, 1, 1),
  y = c(0, 1, 1, 0, 0, 1, 1, 0),
  z = c(0, 0, 0, 0, 1, 1, 1, 1),
  i = c(7, 0, 0, 0, 4, 4, 6, 6, 4, 0, 3, 2),
  j = c(3, 4, 1, 2, 5, 6, 5, 2, 0, 1, 6, 3),
  k = c(0, 7, 2, 3, 6, 7, 1, 1, 5, 5, 7, 6),
  intensity = seq(0, 1, length = 8),
  color = seq(0, 1, length = 8),
  colors = colorRamp(rainbow(8))
)

fig
```

<div id="htmlwidget-f90d5e231d45ccebc890" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-f90d5e231d45ccebc890">{"x":{"visdat":{"654f5e0e5afc":["function () ","plotlyVisDat"]},"cur_data":"654f5e0e5afc","attrs":{"654f5e0e5afc":{"x":[0,0,1,1,0,0,1,1],"y":[0,1,1,0,0,1,1,0],"z":[0,0,0,0,1,1,1,1],"i":[7,0,0,0,4,4,6,6,4,0,3,2],"j":[3,4,1,2,5,6,5,2,0,1,6,3],"k":[0,7,2,3,6,7,1,1,5,5,7,6],"intensity":[0,0.142857142857143,0.285714285714286,0.428571428571429,0.571428571428571,0.714285714285714,0.857142857142857,1],"color":[0,0.142857142857143,0.285714285714286,0.428571428571429,0.571428571428571,0.714285714285714,0.857142857142857,1],"colors":["function (x) ","roundcolor(cbind(palette[[1L]](x), palette[[2L]](x), palette[[3L]](x), ","    if (alpha) palette[[4L]](x))) * 255"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"mesh3d"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"scene":{"xaxis":{"title":[]},"yaxis":{"title":[]},"zaxis":{"title":[]}},"hovermode":"closest","showlegend":false,"legend":{"yanchor":"top","y":0.5}},"source":"A","config":{"showSendToCloud":false},"data":[{"colorbar":{"title":"","ticklen":2,"len":0.5,"lenmode":"fraction","y":1,"yanchor":"top"},"colorscale":[["0","rgba(255,0,0,1)"],["0.0416666666666667","rgba(255,56,0,1)"],["0.0833333333333333","rgba(255,111,0,1)"],["0.125","rgba(255,167,0,1)"],["0.166666666666667","rgba(234,202,0,1)"],["0.208333333333333","rgba(197,220,0,1)"],["0.25","rgba(160,239,0,1)"],["0.291666666666667","rgba(123,255,3,1)"],["0.333333333333333","rgba(85,255,21,1)"],["0.375","rgba(48,255,40,1)"],["0.416666666666667","rgba(11,255,59,1)"],["0.458333333333333","rgba(0,255,104,1)"],["0.5","rgba(0,255,160,1)"],["0.541666666666667","rgba(0,255,215,1)"],["0.583333333333333","rgba(0,239,255,1)"],["0.625","rgba(0,183,255,1)"],["0.666666666666667","rgba(0,128,255,1)"],["0.708333333333333","rgba(0,72,255,1)"],["0.75","rgba(32,48,255,1)"],["0.791666666666667","rgba(69,29,255,1)"],["0.833333333333333","rgba(107,11,255,1)"],["0.875","rgba(144,0,247,1)"],["0.916666666666667","rgba(181,0,228,1)"],["0.958333333333333","rgba(218,0,210,1)"],["1","rgba(255,0,191,1)"]],"showscale":true,"x":[0,0,1,1,0,0,1,1],"y":[0,1,1,0,0,1,1,0],"z":[0,0,0,0,1,1,1,1],"i":[7,0,0,0,4,4,6,6,4,0,3,2],"j":[3,4,1,2,5,6,5,2,0,1,6,3],"k":[0,7,2,3,6,7,1,1,5,5,7,6],"intensity":[0,0.142857142857143,0.285714285714286,0.428571428571429,0.571428571428571,0.714285714285714,0.857142857142857,1],"type":"mesh3d","marker":{"line":{"colorbar":{"title":"","ticklen":2},"cmin":0,"cmax":1,"colorscale":[["0","rgba(255,0,0,1)"],["0.0416666666666667","rgba(255,56,0,1)"],["0.0833333333333333","rgba(255,111,0,1)"],["0.125","rgba(255,167,0,1)"],["0.166666666666667","rgba(234,202,0,1)"],["0.208333333333333","rgba(197,220,0,1)"],["0.25","rgba(160,239,0,1)"],["0.291666666666667","rgba(123,255,3,1)"],["0.333333333333333","rgba(85,255,21,1)"],["0.375","rgba(48,255,40,1)"],["0.416666666666667","rgba(11,255,59,1)"],["0.458333333333333","rgba(0,255,104,1)"],["0.5","rgba(0,255,160,1)"],["0.541666666666667","rgba(0,255,215,1)"],["0.583333333333333","rgba(0,239,255,1)"],["0.625","rgba(0,183,255,1)"],["0.666666666666667","rgba(0,128,255,1)"],["0.708333333333333","rgba(0,72,255,1)"],["0.75","rgba(32,48,255,1)"],["0.791666666666667","rgba(69,29,255,1)"],["0.833333333333333","rgba(107,11,255,1)"],["0.875","rgba(144,0,247,1)"],["0.916666666666667","rgba(181,0,228,1)"],["0.958333333333333","rgba(218,0,210,1)"],["1","rgba(255,0,191,1)"]],"showscale":false,"color":[0,0.142857142857143,0.285714285714286,0.428571428571429,0.571428571428571,0.714285714285714,0.857142857142857,1]}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plotly.com/r/reference/#mesh3d](https://plotly.com/r/reference/#mesh3d) for more information and chart attribute options!
### What About Dash?

[Dash for R](https://dashr.plot.ly/) is an open-source framework for building analytical applications, with no Javascript required, and it is tightly integrated with the Plotly graphing library. 

Learn about how to install Dash for R at https://dashr.plot.ly/installation.

Everywhere in this page that you see `fig`, you can display the same figure in a Dash for R application by passing it to the `figure` argument of the [`Graph` component](https://dashr.plot.ly/dash-core-components/graph) from the built-in `dashCoreComponents` package like this:


```r
library(plotly)

fig <- plot_ly() 
# fig <- fig %>% add_trace( ... )
# fig <- fig %>% layout( ... ) 

library(dash)
library(dashCoreComponents)
library(dashHtmlComponents)

app <- Dash$new()
app$layout(
    htmlDiv(
        list(
            dccGraph(figure=fig) 
        )
     )
)

app$run_server(debug=TRUE, dev_tools_hot_reload=FALSE)
```
