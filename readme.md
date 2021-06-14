[![meowz.moe](https://cdn.meowz.moe/images/logos/meowzmoe.svg)](https://meowz.moe)

Meowz.moe is my personal website.

Its main goal is to be as lightweight and simple as possible to mantain compatibility with lower end devices and slow networks.

Its secondary goal is to look nice and modern-ish.

# Nginx Config

Hides the .html extension and fixes any problems that are caused by doing that.

(You do *not* need the ```absolute_redirect``` directive if you are not behind a reverse proxy)

```nginx
location / {
        absolute_redirect off;
        rewrite ^(/.*)\.html(\?.*)?$ $1$2; #Redirects meowz.moe/$uri.html to meowz.moe/$uri
        rewrite ^/(.*)/$ /$1 permanent; #Redirects meowz.moe/$uri/ to meowz.moe/$uri
        try_files $uri.html $uri/ $uri =404;
}

```
