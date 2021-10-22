# Seminar 4

* Please record your attendance [here](https://forms.office.com/Pages/ResponsePage.aspx?id=_epnVXfnpUKRu5RA_UO4k2iqStX41KNDpkUzhjwCGeNUN01TOTFTWVc0VTVMN0czNExWOUZCMVdZRi4u).

* If you would like to you may fill out an anonymous survey on the seminars; you can find the link [here](https://forms.office.com/Pages/ResponsePage.aspx?id=_epnVXfnpUKRu5RA_UO4k2iqStX41KNDpkUzhjwCGeNUQ0VBRVpOWFI3T1ZYR0hUR09TT0MzNUtQQi4u)
---

## Some exercises from the lectures

1. Convince yourself that the primal and dual SMV problems are equivalent (see ISLR 9.1.4-)
2. Show that fitted SVM parameter can be writted as a linear combination of features (predictors)
3. Show that fitted SVM parameter can be writted as a linear combination of features

---

### Note on the loss function we wrote in class

In the seminar we saw the loss function behave strangely on the following example.

``` r
nn <- 100
pp <- 10

X <- matrix(runif(nn*pp), nrow = nn, ncol = pp)
beta <- rpois(pp, lambda = 5)
y <- X %*% beta + rep(nn, 1)

least_squares_loss(X, y, beta)
least_squares_gradient(X, y, beta)
```


This is because I used the `rep` function incorrectly! I did the following.

``` r
rep(nn, 1)
>>> 100
```
When R noticed I was adding a scalar and a vector it turned the single value `100` to vector of length `nn` with each entry being `100`.

The correct usage is the following.

``` r
rep(1, nn)
>>> 1 1 1 1 1 1 1 1 1 ...
```

The loss and gradient functions we wrote in class should work fine.
