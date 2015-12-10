SublimeText 3
=============

#### Package Control 

	ctrl + ~

Paste the following:

``` python

import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)

```

#### SublimeGo

	cmd+shift+p

Select Package Control: Install Package<br>
Select GoSublime


#### Go Formatting

	cmd + . + cmd 5

add to the file:

``` golang 

	{
    "fmt_cmd": ["goimports"]
} 

```