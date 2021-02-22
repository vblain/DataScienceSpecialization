#
# This is the user-interface definition of a Shiny web application. You can
# run the application by clicking 'Run App' above.
#
# Find out more about building applications with Shiny here:
#
#    http://shiny.rstudio.com/
#

library(leaflet)
library(shiny)

myTitle <- function(){
  HTML("Week 2 - Peer Graded assignment - R Markdown and Leaflet <br /> With US National Monuments Selection <br /> 2/21/2021")
}

# Define UI for application that draws a histogram
shinyUI(fluidPage(
  
      # Application title
    
    titlePanel(
      h1(myTitle(), align = "center")
      ),

    # Sidebar with a slider input for number of bins
    sidebarLayout(
        sidebarPanel(
          
          htmlOutput("selectUI")
        
        ),

        # Show a plot of the generated distribution
        mainPanel(
          leafletOutput("map")
        )
    )
))
