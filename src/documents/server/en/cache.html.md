---
order: 4
title: Enable smart caching
---

The best way to optimize requests made from your page is to not make requests, obviously. And one of the most useful ways to avoid unecessary requests is to let the browser cache assets. By default, the browser is left to decide how long to cache files. But we can control the exact time that a file will be kept in cache.

This type of configuration is done on the server (and will depend on which server setup you have). With Apache, for example, you can add the following configuration in an `.htaccess` file:

```
ExpiresActive On
ExpiresByType image/gif "access plus 6 months"
ExpiresByType image/jpeg "access plus 6 months"
ExpiresByType image/png "access plus 6 months"
ExpiresByType text/css "access plus 6 months"
ExpiresByType text/javascript "access plus 6 months"
ExpiresByType application/javascript "access plus 6 months"
```

These instructions cache images, CSS and JS for 6 months&mdash;it's recommended to cache them for at least one month. Other servers can be similarly configured.

One important thing to remember is that once cached, the browser won't request a new file anymore. If we need to change the content of the file, it won't work in the way we might expect. To send a new version, we need to change the name of the file. One way to do this is to add some form of versioning or a timestamp to the filename. For example, instead of `home.js` you can use `home-v1.js` and when you need to update the file, change the name to `home-v2.js`, etc. Another common form of cache-busting is to use a GET parameter in the URL: `home.js?v=1` and `home.js?v=2`.
