```R
library(shiny)

# Nama-nama siswa dalam kelompok
siswa <- c("Muhammad Igo Pratama  (3323600031)", "Aulia Nurzahra Anantiyo (3323600036)", "Elza Hiya Nadhifa (3323600040)", "Kriza Fauzi Nafi'Ubadah (3323600048)", "Athira Zahra Adini  (3323600049)", "Wahyu ikbal maulana (3323600056)", "Sabrina Humaira (3323600057)")

# Define UI for application that draws an exponential distribution histogram
ui <- fluidPage(
  # Application title
  titlePanel(HTML("<u>Distribusi eksponensial</u>")),
  fluidRow(
    column(
      2,
      offset = 1,
      sliderInput(
        inputId = "n",
        label = "Sample size",
        max = 1000,
        min = 10,
        value = 1000
      ),
      p("Jumlah sampel yang akan dihasilkan.")
    ),
    column(
      2,
      offset = 1,
      sliderInput(
        inputId = "lambda",
        label = "Lambda",
        max = 10.0,
        min = 1.0,
        value = 10.0
      ),
      p("Parameter Lambda untuk distribusi eksponensial.")
    ),
    mainPanel(
      plotOutput(outputId = "box"),
      p("Distribusi eksponensial adalah distribusi probabilitas kontinu yang menggambarkan waktu antara dua kejadian sukses."),
      tags$br(), # Ini akan menambahkan baris kosong
      column(
        2,
        offset = 1,
        selectInput(
          inputId = "siswa_group",
          label = "Nama Kelompok Siswa",
          choices = siswa,
          selected = siswa[1] # Pilih siswa pertama sebagai nilai default
        )
      )
    )
  )
)

# Define server logic required to draw an exponential distribution histogram
server <- function(input, output) {
  
  eks = function(n, lambda){
    U = runif(n)
    X = (-log(1 - U)) * (1 / lambda) 
    return(X)
  }
  
  observe({
    n <- input$n
    lambda <- input$lambda
    output$box <- renderPlot({
      y1 = eks(n, lambda)
      hist(y1, main = "Distribusi Eksponensial Metode Invers Transform", xlab = "X", col = "green")
    })
  })
}

# Run the application 
shinyApp(ui = ui, server = server)

```

```R
library(shiny)
library(ggplot2)

# Nama-nama siswa dalam kelompok
siswa <- c("Muhammad Igo Pratama  (3323600031)", "Aulia Nurzahra Anantiyo (3323600036)", "Elza Hiya Nadhifa (3323600040)", "Kriza Fauzi Nafi'Ubadah (3323600048)", "Athira Zahra Adini  (3323600049)", "Wahyu ikbal maulana (3323600056)", "Sabrina Humaira (3323600057)")

# Define UI for application that draws an exponential distribution histogram
ui <- fluidPage(
  # Application title
  titlePanel(HTML("<u>Distribusi eksponensial</u>")),
  fluidRow(
    column(
      2,
      offset = 1,
      sliderInput(
        inputId = "n",
        label = "Sample size",
        max = 1000,
        min = 10,
        value = 1000
      ),
      p("Jumlah sampel yang akan dihasilkan.")
    ),
    column(
      2,
      offset = 1,
      sliderInput(
        inputId = "lambda",
        label = "Lambda",
        max = 10.0,
        min = 1.0,
        value = 10.0
      ),
      p("Parameter Lambda untuk distribusi eksponensial.")
    ),
    tags$br(), # Ini akan menambahkan baris kosong
    mainPanel(
      plotOutput(outputId = "box")
    ),
    tags$br(), # Ini akan menambahkan baris kosong
    column(
      2,
      offset = 1,
      selectInput(
        inputId = "siswa_group",
        label = "Nama Kelompok Siswa",
        choices = siswa,
        selected = siswa[1] # Pilih siswa pertama sebagai nilai default
      )
    )
  )
)

# Define server logic required to draw an exponential distribution histogram
server <- function(input, output) {
  
  eks = function(n, lambda){
    U = runif(n)
    X = (-log(1 - U)) * (1 / lambda) 
    return(X)
  }
  
  observe({
    n <- input$n
    lambda <- input$lambda
    output$box <- renderPlot({
      y1 = eks(n, lambda)
      data <- data.frame(X = y1)
      ggplot(data, aes(x = X)) +
        geom_histogram(fill = "green", color = "black", bins = 20) +
        labs(title = "Distribusi Eksponensial Metode Invers Transform",
             x = "X",
             y = "Frekuensi") +
        theme_minimal() +
        theme(plot.title = element_text(size = 16, face = "bold")) # Mengatur ukuran dan ketebalan teks judul
    })
  })
}

# Run the application 
shinyApp(ui = ui, server = server)

```
