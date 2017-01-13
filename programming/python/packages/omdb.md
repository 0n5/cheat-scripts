OMDB 
====

#### Installation

    $ pip install omdb

#### Usage

``` python 

import omdb
import requests

omdb_search = omdb.get(imdbid=[IMDB_MOVIE_ID], fullplot=True)
title = omdb_search.title
plot = omdb_search.plot
year = omdb_search.year

```