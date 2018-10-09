# bazaar.akikieng.com-snapshot-anonymous

Mirror of bazaar.akikieng.com, without user login, i.e. data that is displayed to authenticated user is not shown

Done with wget and nginx

References
* https://fosswire.com/post/2008/04/create-a-mirror-of-a-website-with-wget/
* https://www.nginx.com/resources/wiki/modules/substitutions/#subs-filter


## Requirements

* [aee-saleor](https://github.com/akikieng/aee-saleor) django site served through nginx
* install nginx substitutions filter with `sudo apt-get install libnginx-mod-http-subs-filter`
* edit nginx config to perform the substitution (check repo file `bazaar.akikieng.com-root/etc/nginx/sites-available/bazaar_live`)
  * note that this added section is only needed for running `wget...` below
  * once done, can disable the section


## Usage

```
wget -mk https://bazaar.akikieng.com/
```

## Deploy static site

The wget command above will download all files into a folder `bazaar.akikieng.com`

Serve this file statically with nginx, like it serves `/var/www/html`

Be careful not to have a prefix path in your endpoint, otherwise some css/javascript might not work,
i.e. serve from http://bazaar-snapshot-anonymous.akikieng.com and not from http://bazaar-static.akikieng.com/bazaar-snapshot-anonymous
