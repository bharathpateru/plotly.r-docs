---
name: geom_errorbar
permalink: ggplot2/geom_errorbar/
description: Examples of geom_errobar in R and ggplot2
layout: base
thumbnail: thumbnail/error-bar.jpg
language: ggplot2
page_type: example_index
display_as: statistics
order: 2
output:
  html_document:
    keep_md: true
---


### Basic Error Bar


```r
library(plotly)

df <- data.frame(x = 1:10,
                 y = 1:10,
                 ymin = (1:10) - runif(10),
                 ymax = (1:10) + runif(10),
                 xmin = (1:10) - runif(10),
                 xmax = (1:10) + runif(10))

p <- ggplot(data = df,aes(x = x,y = y)) + 
    geom_point() + 
    geom_errorbar(aes(ymin = ymin,ymax = ymax)) + 
    geom_errorbarh(aes(xmin = xmin,xmax = xmax))

fig <- ggplotly(p)

fig
```

<div id="htmlwidget-34431915cb2d8a666a3a" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-34431915cb2d8a666a3a">{"x":{"data":[{"x":[1,2,3,4,5,6,7,8,9,10],"y":[1,2,3,4,5,6,7,8,9,10],"text":["x:  1<br />y:  1","x:  2<br />y:  2","x:  3<br />y:  3","x:  4<br />y:  4","x:  5<br />y:  5","x:  6<br />y:  6","x:  7<br />y:  7","x:  8<br />y:  8","x:  9<br />y:  9","x: 10<br />y: 10"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1,2,3,4,5,6,7,8,9,10],"y":[1,2,3,4,5,6,7,8,9,10],"text":["ymin: 0.4474869<br />ymax:  1.208851<br />x:  1<br />y:  1","ymin: 1.2976370<br />ymax:  2.171738<br />x:  2<br />y:  2","ymin: 2.5077186<br />ymax:  3.231669<br />x:  3<br />y:  3","ymin: 3.6984383<br />ymax:  4.221250<br />x:  4<br />y:  4","ymin: 4.0163906<br />ymax:  5.088742<br />x:  5<br />y:  5","ymin: 5.7827046<br />ymax:  6.631770<br />x:  6<br />y:  6","ymin: 6.5273090<br />ymax:  7.434333<br />x:  7<br />y:  7","ymin: 7.9389609<br />ymax:  8.807380<br />x:  8<br />y:  8","ymin: 8.9204419<br />ymax:  9.726432<br />x:  9<br />y:  9","ymin: 9.8556773<br />ymax: 10.019784<br />x: 10<br />y: 10"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_y":{"array":[0.208851327886805,0.17173838801682,0.231669157743454,0.221250401576981,0.0887416400946677,0.631769873201847,0.434333157725632,0.807379663456231,0.726432480383664,0.0197839187458158],"arrayminus":[0.552513064816594,0.702363011892885,0.492281406652182,0.301561659900472,0.98360938904807,0.21729538962245,0.472691041184589,0.0610390675719827,0.0795581298880279,0.144322657492012],"type":"data","width":18.5123966942149,"symmetric":false,"color":"rgba(0,0,0,1)"},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1,2,3,4,5,6,7,8,9,10],"y":[1,2,3,4,5,6,7,8,9,10],"text":["xmin: 0.8481903<br />xmax:  1.559334<br />x:  1<br />y:  1","xmin: 1.4763158<br />xmax:  2.164112<br />x:  2<br />y:  2","xmin: 2.5744074<br />xmax:  3.578142<br />x:  3<br />y:  3","xmin: 3.7084279<br />xmax:  4.260201<br />x:  4<br />y:  4","xmin: 4.3176990<br />xmax:  5.551686<br />x:  5<br />y:  5","xmin: 5.5860591<br />xmax:  6.855060<br />x:  6<br />y:  6","xmin: 6.5747422<br />xmax:  7.976072<br />x:  7<br />y:  7","xmin: 7.0127693<br />xmax:  8.081553<br />x:  8<br />y:  8","xmin: 8.5177818<br />xmax:  9.909837<br />x:  9<br />y:  9","xmin: 9.2166463<br />xmax: 10.331394<br />x: 10<br />y: 10"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_x":{"array":[0.559334382414818,0.16411161981523,0.578142332145944,0.260200754739344,0.551686128601432,0.855060316622257,0.976072465069592,0.0815532887354493,0.909836689708754,0.33139437250793],"arrayminus":[0.151809669099748,0.523684174986556,0.425592553569004,0.291572115849704,0.682301043299958,0.413940858095884,0.425257826223969,0.987230722792447,0.482218218734488,0.783353656996042],"type":"data","width":13.0876200871517,"symmetric":false,"color":"rgba(0,0,0,1)"},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":48.9497716894977},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.0550000000000001,10.945],"tickmode":"array","ticktext":["2.5","5.0","7.5","10.0"],"tickvals":[2.5,5,7.5,10],"categoryorder":"array","categoryarray":["2.5","5.0","7.5","10.0"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"x","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-0.0526387180574238,10.9501256532408],"tickmode":"array","ticktext":["0.0","2.5","5.0","7.5","10.0"],"tickvals":[0,2.5,5,7.5,10],"categoryorder":"array","categoryarray":["0.0","2.5","5.0","7.5","10.0"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"y","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"7b2436a0a064":{"x":{},"y":{},"type":"scatter"},"7b242db8107c":{"ymin":{},"ymax":{},"x":{},"y":{}},"7b24343d241c":{"xmin":{},"xmax":{},"x":{},"y":{}}},"cur_data":"7b2436a0a064","visdat":{"7b2436a0a064":["function (y) ","x"],"7b242db8107c":["function (y) ","x"],"7b24343d241c":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Margin Error Bar


```r
library(plotly)

population <- data.frame(Year=seq(1790, 1970, length.out=length(uspop)), 
                         Population=uspop, 
                         Error=rnorm(length(uspop), 5))

library(ggplot2)
p <- ggplot(population, aes(x=Year, y=Population, 
                       ymin=Population-Error, ymax=Population+Error))+
  geom_line()+
  geom_point(pch=2)+
  geom_errorbar(width=0.9)

fig <- ggplotly(p)

fig
```

<div id="htmlwidget-1bcf1f62e96a03bd1517" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-1bcf1f62e96a03bd1517">{"x":{"data":[{"x":[1790,1800,1810,1820,1830,1840,1850,1860,1870,1880,1890,1900,1910,1920,1930,1940,1950,1960,1970],"y":[3.93,5.31,7.24,9.64,12.9,17.1,23.2,31.4,39.8,50.2,62.9,76,92,105.7,122.8,131.7,151.3,179.3,203.2],"text":["Year: 1790<br />Population:   3.93<br />Population - Error:  -1.7844422<br />Population + Error:   9.644442","Year: 1800<br />Population:   5.31<br />Population - Error:  -0.6080425<br />Population + Error:  11.228042","Year: 1810<br />Population:   7.24<br />Population - Error:   1.9337351<br />Population + Error:  12.546265","Year: 1820<br />Population:   9.64<br />Population - Error:   6.1888823<br />Population + Error:  13.091118","Year: 1830<br />Population:  12.90<br />Population - Error:   7.6887367<br />Population + Error:  18.111263","Year: 1840<br />Population:  17.10<br />Population - Error:  11.8617091<br />Population + Error:  22.338291","Year: 1850<br />Population:  23.20<br />Population - Error:  19.8327485<br />Population + Error:  26.567252","Year: 1860<br />Population:  31.40<br />Population - Error:  26.7402186<br />Population + Error:  36.059781","Year: 1870<br />Population:  39.80<br />Population - Error:  34.6524437<br />Population + Error:  44.947556","Year: 1880<br />Population:  50.20<br />Population - Error:  45.1207598<br />Population + Error:  55.279240","Year: 1890<br />Population:  62.90<br />Population - Error:  56.8934798<br />Population + Error:  68.906520","Year: 1900<br />Population:  76.00<br />Population - Error:  71.9749765<br />Population + Error:  80.025024","Year: 1910<br />Population:  92.00<br />Population - Error:  86.1724751<br />Population + Error:  97.827525","Year: 1920<br />Population: 105.70<br />Population - Error: 100.0403537<br />Population + Error: 111.359646","Year: 1930<br />Population: 122.80<br />Population - Error: 116.7066426<br />Population + Error: 128.893357","Year: 1940<br />Population: 131.70<br />Population - Error: 124.7943657<br />Population + Error: 138.605634","Year: 1950<br />Population: 151.30<br />Population - Error: 147.0517081<br />Population + Error: 155.548292","Year: 1960<br />Population: 179.30<br />Population - Error: 174.3919645<br />Population + Error: 184.208035","Year: 1970<br />Population: 203.20<br />Population - Error: 199.6228898<br />Population + Error: 206.777110"],"type":"scatter","mode":"lines+markers","line":{"width":1.88976377952756,"color":"transparent","dash":"solid"},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"triangle-up-open","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"opacity":1,"error_y":{"array":[5.71444218577363,5.91804248849231,5.3062649114772,3.45111774984937,5.21126334980247,5.2382909034433,3.36725151353532,4.65978139357683,5.14755629784859,5.07924016018754,6.00652016301232,4.02502354299715,5.82752486405738,5.65964630748498,6.0933573632115,6.90563433038818,4.24829189248865,4.90803545654111,3.57711020709232],"arrayminus":[5.71444218577363,5.91804248849231,5.3062649114772,3.45111774984937,5.21126334980247,5.2382909034433,3.36725151353532,4.65978139357683,5.14755629784859,5.07924016018754,6.00652016301231,4.02502354299715,5.82752486405738,5.65964630748498,6.09335736321148,6.90563433038817,4.24829189248865,4.90803545654111,3.57711020709232],"type":"data","width":1.01311623699693,"symmetric":false,"color":"rgba(0,0,0,1)"},"frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":43.1050228310502},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[1780.505,1979.495],"tickmode":"array","ticktext":["1800","1850","1900","1950"],"tickvals":[1800,1850,1900,1950],"categoryorder":"array","categoryarray":["1800","1850","1900","1950"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"Year","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-12.2125198054169,217.205187826736],"tickmode":"array","ticktext":["0","50","100","150","200"],"tickvals":[0,50,100,150,200],"categoryorder":"array","categoryarray":["0","50","100","150","200"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"Population","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"7b2454966d2e":{"x":{},"y":{},"ymin":{},"ymax":{},"type":"scatter"},"7b244b80845a":{"x":{},"y":{},"ymin":{},"ymax":{}},"7b246067478a":{"x":{},"y":{},"ymin":{},"ymax":{}}},"cur_data":"7b2454966d2e","visdat":{"7b2454966d2e":["function (y) ","x"],"7b244b80845a":["function (y) ","x"],"7b246067478a":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

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
