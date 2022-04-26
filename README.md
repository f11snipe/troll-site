# troll-site
Simple tricks &amp; lol's with nginx configs

https://f11snipe.sh
update


/etc/nginx/sites-available cat http 
server {
	listen 80;
	listen [::]:80;

	server_name thm.f11snipe.cloud;

	return 301 https://$host$request_uri;
}

/etc/nginx/sites-available cat https
server {
	listen 443 ssl;
	listen [::]:443 ssl;

	server_name thm.f11snipe.cloud;

	ssl_certificate     /etc/dehydrated/certs/thm.f11snipe.cloud/fullchain.pem;
	ssl_certificate_key /etc/dehydrated/certs/thm.f11snipe.cloud/privkey.pem;
	ssl_protocols       TLSv1 TLSv1.1 TLSv1.2;
	ssl_ciphers         HIGH:!aNULL:!MD5;	

	root /var/www/thm.f11snipe.cloud;
	index index.html;

	location / {
		try_files $uri $uri/ =404;
	}
}