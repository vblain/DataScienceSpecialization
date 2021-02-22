#
# This is the server logic of a Shiny web application. You can run the
# application by clicking 'Run App' above.
#
# Find out more about building applications with Shiny here:
#
#    http://shiny.rstudio.com/
#

library(shiny)
library(leaflet)
library(ggmap)
library(magrittr)
library(maps)
library(maptools)
library(raster)
library(rgeos)
library(sp)
library(readr)
library(dplyr)


generateMap <- function(monument){
  myText = paste("<b>", monument$Monuments, "</b>")
  latitude = monument$Latitude
  longitute = monument$Longitude
  
  renderLeaflet({
    m <- leaflet() %>%
      # Now add tiles to it
      addTiles() %>%  
      # Setting the middle of where the map should be and the zoom level
      setView(lng=longitute, lat=latitude, zoom = 16) %>%
      # Now, add a marker with a popup, 
      addMarkers(lng=longitute, lat=latitude, popup=myText)
    
    m
  }) 
}

shinyServer(function(input, output, session) {
  
  myData <- read_csv("US_Monuments.csv")
  
  monument <- filter(myData, Id == 1)
  
  output$selectUI <- renderUI({ 
    selectInput("Id", "Select your choice", unique(myData$Monuments), selected = 1 )
  })
  
  observeEvent(input$Id ,{
    val <- input$Id
    monument <- filter(myData, Monuments == val)
    output$map <- generateMap(monument) 
  }, ignoreInit = TRUE)  
  
  myText = paste("<b>", monument$Monuments, "</b>")
  latitude = monument$Latitude
  longitute = monument$Longitude
  
  output$map <- generateMap(monument) 
  
})
