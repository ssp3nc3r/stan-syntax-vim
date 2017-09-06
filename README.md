# stan-syntax-vim
Stan syntax highlighting for vim

The Stan names of functions, distributions and such identified in the syntax file for vim were pulled from RStan version 2.16.2 using rstan::lookup() in R as follows:

d <- c(rstan::lookup("_lpmf$")$StanFunction, sub("_lpmf", "", rstan::lookup("_lpmf$")$StanFunction),
          rstan::lookup("_lpdf$")$StanFunction, sub("_lpdf", "", rstan::lookup("_lpdf$")$StanFunction),
          rstan::lookup("_lcdf$")$StanFunction, sub("_lcdf", "", rstan::lookup("_lcdf$")$StanFunction),
          rstan::lookup("_lccdf$")$StanFunction, sub("_lccdf", "", rstan::lookup("_lccdf$")$StanFunction),
          rstan::lookup("_cdf$")$StanFunction, sub("_cdf", "", rstan::lookup("_cdf$")$StanFunction),
          rstan::lookup("_rng$")$StanFunction, sub("_rng", "", rstan::lookup("_rng$")$StanFunction))

d <- unique(d)
f <- rstan::lookup("[:alnum:]*")$StanFunction
f <- unique(f)
f <- f[-grep("operator", f)]
f <- f[!(f %in% d)]

The other keywords were gathered from the Stan Manual.
