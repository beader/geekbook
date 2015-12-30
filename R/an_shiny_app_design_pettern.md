# An Shiny App Design Pettern

一个最简单的ShinyApp由两个文件构成，分别是`ui.R`与`server.R`

```r
# ui.R
library(shiny)

shinyUI(fluidPage(
  titlePanel("Simplest Shiny App"),
  sidebarLayout(
    sidebarPanel(
      sliderInput("bins",
                  "Number of bins:",
                  min = 1,
                  max = 50,
                  value = 30)
    ),
    mainPanel(
      plotOutput("distPlot")
    )
  )
))

```

```r
# server.R
library(shiny)

shinyServer(function(input, output) {
  output$distPlot <- renderPlot({
    x    <- faithful[, 2]
    bins <- seq(min(x), max(x), length.out = input$bins + 1)
    hist(x, breaks = bins, col = 'darkgray', border = 'white')
  })
})
```

但随着页面，功能的增加，这两个页面就会越来越大，越来越不容易管理。比如一个典型的[shinydashboard](https://rstudio.github.io/shinydashboard/)应用:

![](dashboard.png)

每个