FROM httpd:2.4

RUN sed -i \
  -e 's!/usr/local/apache2/htdocs!/usr/local/apache2/htdocs/public!g' \
  -e 's/^#\(LoadModule .*mod_rewrite.so\)/\1/' \
  -e 's/^#\(LoadModule .*mod_mpm_event.so\)/\1/' \
  -e 's/^#\(LoadModule .*mod_proxy.so\)/\1/' \
  -e 's/^#\(LoadModule .*mod_proxy_fcgi.so\)/\1/' \
  /usr/local/apache2/conf/httpd.conf && \
  echo '<Directory "/usr/local/apache2/htdocs/public">\n\
  AllowOverride All\n\
  <FilesMatch \.php$>\n\
    SetHandler "proxy:fcgi://127.0.0.1:9000"\n\
  </FilesMatch>\n\
</Directory>\n\
IncludeOptional conf/custom_httpd.conf' >> /usr/local/apache2/conf/httpd.conf
