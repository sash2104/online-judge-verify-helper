<!-- mathjax config similar to math.stackexchange -->
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    TeX: { equationNumbers: { autoNumber: "AMS" }},
    tex2jax: {
      inlineMath: [ ['$','$'] ],
      processEscapes: true
    },
    "HTML-CSS": { matchFontHeight: false },
    displayAlign: "left",
    displayIndent: "2em"
  });
</script>

<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/jquery-balloon-js@1.1.2/jquery.balloon.min.js" integrity="sha256-ZEYs9VrgAeNuPvs15E39OsyOJaIkXEEt10fzxJ20+2I=" crossorigin="anonymous"></script>
<script type="text/javascript" src="../../assets/js/copy-button.js"></script>
<link rel="stylesheet" href="../../assets/css/copy-button.css" />


# :warning: examples/segment_tree.range_minimum_query.test.cpp


[Back to top page](../../index.html)

* see: [https://onlinejudge.u-aizu.ac.jp/courses/library/3/DSL/all/DSL_2_A](https://onlinejudge.u-aizu.ac.jp/courses/library/3/DSL/all/DSL_2_A)


## Dependencies
* :warning: [examples/macros.hpp](../../library/examples/macros.hpp.html)
* :warning: [examples/monoids.hpp](../../library/examples/monoids.hpp.html)
* :warning: [examples/segment_tree.hpp](../../library/examples/segment_tree.hpp.html)


## Code
```cpp
#define PROBLEM "https://onlinejudge.u-aizu.ac.jp/courses/library/3/DSL/all/DSL_2_A"
#include <iostream>
#include "./segment_tree.hpp"
#include "./monoids.hpp"
#include "./macros.hpp"
using namespace std;

int main() {
    int n, q; cin >> n >> q;
    segment_tree<min_monoid> segtree(n);
    REP (i, n) {
        segtree.point_set(i, (1u << 31) - 1);
    }
    REP (i, q) {
        int com, x, y; cin >> com >> x >> y;
        if (com == 0) {
            segtree.point_set(x, y);
        } else if (com == 1) {
            cout << segtree.range_concat(x, y + 1) << endl;
        }
    }
    return 0;
}

```

[Back to top page](../../index.html)
