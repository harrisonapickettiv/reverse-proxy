# reverse-proxy
## About
A reverse proxy into your docker environment.

## Installing
To install, first pull this repo to the location that best suits your environment. Maybe `/opt/reverse-proxy`.

Next, copy `etc/env.example` to `etc/env` and update with the details from your environment. Likewise copy `etc/digitalocean.ini.example` to `etc/digitalocean.ini` and update with your Digital Ocean API token.

Finally, run `./init` from within `bin/`.

## Usage
### proxy.start
Start the reverse proxy server in detached mode.
```properties
bin/proxy.start 
```

### proxy.stop
Stop the reverse proxy and cleanup unused containers and networks.
```properties
bin/proxy.stop 
```

### site.add
Place an Nginx server block fragment and reload Nginx config.
```properties
bin/site.add /full/path/to/nginx/server-block/file
```

### site.list
List active Nginx server blocks by filename.
```properties
bin/site.list 
```

### site.remove
Remove an Nginx server block by filename.
```properties
bin/site.remove server.block.filename
```

### site.view
View the contents of an Nginx server block by filename.
```properties
bin/site.view server.block.filename
```

### cert.delete
Delete a certificate by cert-name.
```properties
bin/cert.delete cert-name
```

### cert.list
List installed certificates by their cert-name.
```properties
bin/cert.list 
```

### cert.register
Register a new certificate for one or more domains. The cert-name is used for housekeeping and in file paths; it doesn't affect the content of the certificate itself. Multiple domains are supplied as a comma-separated list. Email is used for registration and recovery contact.
```properties
bin/cert.register cert-name domain*[,domain] email@address.tld
```

### cert.renew
This command attempts to renew any previously-obtained certificates that expire in less than 30 days. 
```properties
bin/cert.renew 
```

### cert.renew.one
Force the renewal of a certificate by name.
```properties
bin/cert.renew.one cert-name
```

### cert.view
Show details of a certificate by name.
```properties
bin/cert.view cert-name
```
