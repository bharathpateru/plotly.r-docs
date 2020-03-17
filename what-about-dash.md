### What About Dash?

DashR is an open-source framework for building analytical applications, with no Javascript required, and it is tightly integrated with the Plotly graphing library. Everywhere in this page that you see fig, you can display the same figure in a Dash application by passing it to the figure argument of the Graph component from the built-in dashCoreComponents package like this:

```{r eval=FALSE}
library(plotly)

fig <- plot_ly() 
# fig <- fig %>% add_trace( ... )
# fig <- fig %>% layout( ... ) 

library(dash)
library(dashCoreComponents)
library(dashHtmlComponents)

app <- Dash$new()
app$layout (
    dccGraph(figure=fig)
)

app$run_server()
```