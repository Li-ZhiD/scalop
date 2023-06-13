# scalop
Single Cell Analysis Operations

## edit
from
```r
    if (class(x) == 'matrix') {
        x = .hca_cor(x, method = cor.method)
        res = c(res, list(cr = x))
        if (cor.end) return(res)
        x = .hca_dist(x, method = dist.method, max.dist = max.dist)
        res = c(res, list(dist = x))
        if (dist.end) return(res)
    }

    if (class(x) == 'dist') {
        x = .hca_tree(x, method = cluster.method)
        res = c(res, list(tree = x, order = x$labels[x$order]))
        if (hclust.end) return(res)
    }

    if (class(x) == 'hclust') {
        if (is.null(h)) h = res$tree$height
        x = .hca_cutree(x,
                        k = k,
                        h = h,
                        min.size = min.size, 
                        max.size = max.size)
        res = c(res, list(groups = x))
    }
```
to
```r
    if (is(x, 'matrix')) {
        x = .hca_cor(x, method = cor.method)
        res = c(res, list(cr = x))
        if (cor.end) return(res)
        x = .hca_dist(x, method = dist.method, max.dist = max.dist)
        res = c(res, list(dist = x))
        if (dist.end) return(res)
    }

    if (is(x, 'dist')) {
        x = .hca_tree(x, method = cluster.method)
        res = c(res, list(tree = x, order = x$labels[x$order]))
        if (hclust.end) return(res)
    }

    if (is(x, 'hclust')) {
        if (is.null(h)) h = res$tree$height
        x = .hca_cutree(x,
                        k = k,
                        h = h,
                        min.size = min.size, 
                        max.size = max.size)
        res = c(res, list(groups = x))
    }
```
