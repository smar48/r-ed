From a question to [r-sig-eco] mailing list:

Just a small function to get the status of a species from the [IUCN Red List](http://www.iucnredlist.org/) API:


```r
require(XML)
get_IUCN_status <- function(x) {
    spec <- tolower(x)
    spec <- gsub(" ", "-", spec)
    url <- paste("http://api.iucnredlist.org/go/", spec, sep = "")
    h <- htmlParse(url)
    status <- xpathSApply(h, "//div[@id =\"red_list_category_code\"]", xmlValue)
    return(status)
}
```



```r
get_IUCN_status("Panthera uncia")
```

```
## [1] "EN"
```


Have also a look at [Kay Cichinis](http://thebiobucket.blogspot.de/2012/06/use-iucn-data-with-r-xpath.html) extended version!





