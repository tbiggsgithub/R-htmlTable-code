# R htmlTable code

I encourage all my students to use R and htmlTable to generate the final tables and figures for their publications.
Below find some simple code to introduce you to htmlTable.
More help can be found at:
https://cran.r-project.org/web/packages/htmlTable/index.html
  See especially the "Vignettes"

htmlTable example

```R
install.packages("htmlTable")  # Only need to do once
library(htmlTable)
mytable = data.frame(matrix(1:4,nrow=2,ncol=2))
names(mytable) = c("Jan","Feb")
rownames(mytable) = c("Rainfall (mm)","Runoff (cms)")
mytableout = htmlTable (mytable)
print(mytableout)
```

To save this to a file, use the following in R:

```R
outdir.tables = "C:/mydata/"  # Any directory
setwd(outdir.tables)
sink("mytable.html")
print(mytableout,type="html",useViewer=FALSE)
sink()
```

Sometimes you want a specific number of significant digits.

```R
mytable = matrix(rep(c(2,2.58495),times=2),nrow=2,ncol=2)
mytable.txt = apply(mytable,2,function(x) as.character(format(x,digits=2)))
mytableout = htmlTable (mytable.txt)
print(mytableout)
```

To convert the html into a pdf, open the html in a web browser and print to pdf.

See "Batch combine pdf files" for how to put all the pdfs together into a final document....
