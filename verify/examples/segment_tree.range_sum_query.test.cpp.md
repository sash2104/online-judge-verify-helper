---
layout: default
---

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


# :heavy_check_mark: examples/segment_tree.range_sum_query.test.cpp


[Back to top page](../../index.html)

* see: [https://onlinejudge.u-aizu.ac.jp/courses/library/3/DSL/all/DSL_2_B](https://onlinejudge.u-aizu.ac.jp/courses/library/3/DSL/all/DSL_2_B)


## Dependencies
* :heavy_check_mark: [examples/macros.hpp](../../library/examples/macros.hpp.html)
* :heavy_check_mark: [examples/monoids.hpp](../../library/examples/monoids.hpp.html)
* :heavy_check_mark: [examples/segment_tree.hpp](../../library/examples/segment_tree.hpp.html)


## Code
{% raw %}
```cpp
#define PROBLEM "https://onlinejudge.u-aizu.ac.jp/courses/library/3/DSL/all/DSL_2_B"
#include <iostream>
#include "examples/segment_tree.hpp"
#include "examples/monoids.hpp"
#include "examples/macros.hpp"
using namespace std;

int main() {
    int n, q; cin >> n >> q;
    segment_tree<plus_monoid> segtree(n);
    REP (i, n) {
        segtree.point_set(i, 0);
    }
    REP (i, q) {
        int com, x, y; cin >> com >> x >> y;
        -- x;
        if (com == 0) {
            segtree.point_set(x, segtree.range_concat(x, x + 1) + y);
        } else if (com == 1) {
            cout << segtree.range_concat(x, y) << endl;
        }
    }
    return 0;
}

```
{% endraw %}

[Back to top page](../../index.html)
