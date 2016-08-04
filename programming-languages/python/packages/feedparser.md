Feedparser
==========

#### Installation

    $ pip install feedparser
    
#### Usage

``` python

import feedparser

d = feedparser.parse('RSS_LINK')
    for post in d.entries:
        [FIELD] = post.[FIELD]


```