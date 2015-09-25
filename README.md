# R-tips-and-tricks

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
outdir.tables = "C:\mydata\"
setwd(outdir.tables)
sink("mytable.html")
print(mytableout,type="html",useViewer=FALSE)
sink()
```

Sometimes you want a specific number of significant digits.

```R
mytable = matrix(rep(c(2,2.58495),times=2),nrow=2,ncol=2)
mytable.txt = apply(mytable,2,function(x) as.character(format(x,digits=2)))
```
