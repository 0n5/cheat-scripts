TMDB simple
==========

Python package URL: [https://pypi.python.org/pypi/tmdbsimple](https://pypi.python.org/pypi/tmdbsimple)<br>
Retrieve [TMDB API key](https://www.themoviedb.org/faq/api) first

#### Installation

    $ pip install tmdbsimple
    
#### Usage

``` python

import tmdbsimple as tmdb

tmdb.API_KEY = '[KEY]'
tmdb_API_KEY = tmdb.API_KEY

tmdb_query = tmdb.Movies([TMDB_MOVIE_ID]).info()
# queries single movie

poster_path = tmdb_query['poster_path']
# returns single movie poster poster URL path

```