FROM httpd:2.4

RUN sed -i \
  -e 's!/usr/local/apache2/htdocs!/usr/local/apache2/htdocs/public!g' \
  -e 's/^#\(LoadModule .*mod_rewrite.so\)/\1/' \
  -e 's/^#\(LoadModule .*mod_mpm_event.so\)/\1/' \
  -e 's/^#\(LoadModule .*mod_proxy.so\)/\1/' \
  -e 's/^#\(LoadModule .*mod_proxy_fcgi.so\)/\1/' \
  /usr/local/apache2/conf/httpd.conf && \
  echo 'ProxyPassMatch ^/(.*\.php(/.*)?)$ fcgi://app:9000/var/www/html/public/$1\n\
<Directory "/usr/local/apache2/htdocs/public">\n\
  AllowOverride All\n\
</Directory>' >> /usr/local/apache2/conf/httpd.conf
