
# Tutorials on updating GSARefDB

Contributor: Chengshu Xie <br>
Date of first version: 2020-05-20 <br>
Date of last review: 2020-07-03 <br>

##### Summary:
This is tutorials about how to update the shiny work "GSARefDB".

##### Contents:

1. global.R

2. ui.R

3. server.R



There are the structure of the whole shiny app:
![jupyter](https://github.com/Chengshu21/gsarefDB/blob/master/Tutorial/pic/str.png)

## 1. global.R

`global.R` contains the following 3 sections:
* libraring the R packages in need
* sourcing R codes required
* importing data

Notes: Importing data is not necessary in `global.R` file, and the data could be loaded in `server.R` file. Users could choose the way to load data.  

![p1](jupypic/global.png)

## 2. ui.R

`ui.R` contains the structure and display of the shiny app:
* Theme and title
* Menus 
* Overview of Data and FAQs

### 2.1 Theme and Title

![p2](jupypic/theme_title.png)

1) As the image shown, the theme could be changed with `try.css` file under the folder `www`. And if you're not familiar with `.css`, you could try `shinytheme()` to select one theme that you like (e.g. shinytheme("cerulean")). <br>
2) About the title, you could change it by `tags$div()`. 

### 2.2 Menus

`navbarPage()` is used to create a page that contains a top level navigation bar that can be used to toggle a set of tabPanel elements. <br> 
And `tabPanel()` is used to add sub pages.

![p3](jupypic/main_menus.png)


### 2.3 Overview of Data and FAQs

As the image shown, `DT::dataTableOutput()` is used to present data tables from .xlsx, .csv or other files; `Shiny::plotOutput()` is used to display plots, and `includeMarkdown()` is used to present plain text.

![p4](jupypic/contents.png)

## 3. server.R

This R file is updated with `ui.R`. 
If add data tables(using `DT::dataTableOutput())`, then the function to export is `DT::renderDataTable(DT::datatable(......))`;<br>
If making plots(using `shiny::plotOutput()`), then the function to export is `renderPlot({})`.


```R
sessionInfo()
```


    R version 3.6.3 (2020-02-29)
    Platform: x86_64-w64-mingw32/x64 (64-bit)
    Running under: Windows 10 x64 (build 18363)
    
    Matrix products: default
    
    locale:
    [1] LC_COLLATE=Chinese (Simplified)_China.936 
    [2] LC_CTYPE=Chinese (Simplified)_China.936   
    [3] LC_MONETARY=Chinese (Simplified)_China.936
    [4] LC_NUMERIC=C                              
    [5] LC_TIME=Chinese (Simplified)_China.936    
    
    attached base packages:
    [1] stats     graphics  grDevices utils     datasets  methods   base     
    
    loaded via a namespace (and not attached):
     [1] compiler_3.6.3  IRdisplay_0.7.0 pbdZMQ_0.3-3    tools_3.6.3    
     [5] htmltools_0.4.0 pillar_1.4.4    base64enc_0.1-3 crayon_1.3.4   
     [9] Rcpp_1.0.4.6    uuid_0.1-4      IRkernel_1.1    jsonlite_1.6.1 
    [13] digest_0.6.25   repr_1.1.0      rlang_0.4.5     evaluate_0.14  

