# lnkchk_test_sites

This is a set of increasing larger websites that can be used for integration/end-to-end testing of link checkers. I created them during a failed attempt to build a highly concurrent, serverless link checker in AWS. But, that checker got into infinite loops with large link counts (10K+) and was actually slowed down by the rate limits of AWS services (granted, I was keeping it cheap). I've since found [Hydra](https://github.com/victoriadrake/hydra-link-checker) which is shaping up to be a fast, lightweight, CLI link checker.

The websites are currently hosted at:

* Simple: http://lnkchk-simple-site-integration.s3-website-us-east-1.amazonaws.com/
* Complex: http://lnkchk-complex-site-integration.s3-website-us-east-1.amazonaws.com/
* 100 pages: http://lnkchk-100-pages.s3-website-us-east-1.amazonaws.com/

The 100 page site uses [lnkchk-100-page/create_pages.py](lnkchk-100-page/create_pages.py) to create the site. About half of the links will be bad (pages numbers greater than 100).

Here are Hydra link check results on the 100 page sites:
```
---
title: Broken Link Report
checked: 200
number of email links: 0
emails: 
broken: 99
---

- code:    404
  url:     http://lnkchk-100-pages.s3-website-us-east-1.amazonaws.com/page_101.html
  parent:  http://lnkchk-100-pages.s3-website-us-east-1.amazonaws.com/page_21.html
  error:   Not Found

- code:    404
  url:     http://lnkchk-100-pages.s3-website-us-east-1.amazonaws.com/page_102.html
  parent:  http://lnkchk-100-pages.s3-website-us-east-1.amazonaws.com/page_21.html
  error:   Not Found

- code:    404
  url:     http://lnkchk-100-pages.s3-website-us-east-1.amazonaws.com/page_103.html
  parent:  http://lnkchk-100-pages.s3-website-us-east-1.amazonaws.com/page_21.html
  error:   Not Found

- code:    404
  url:     http://lnkchk-100-pages.s3-website-us-east-1.amazonaws.com/page_106.html
  parent:  http://lnkchk-100-pages.s3-website-us-east-1.amazonaws.com/page_21.html
  error:   Not Found

...

```
