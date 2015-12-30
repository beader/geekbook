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