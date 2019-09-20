#!/bin/bash

cd / \
&& apt update && apt install -y  gcc-6 g++-6 libcairo2-dev libjpeg-turbo8-dev libpng-dev \
libossp-uuid-dev libavcodec-dev libavutil-dev libswscale-dev libfreerdp-dev \
libpango1.0-dev libssh2-1-dev libvncserver-dev libssl-dev libvorbis-dev libwebp-dev \
tomcat8 tomcat8-admin tomcat8-common tomcat8-user nginx software-properties-common certbot \
&& git clone https://github.com/mattdavis0351/guacfiles && cd guacfiles/guacamole-server-1.0.0 \
&& ./configure --with-init-dir=/etc/init.d \
&& make && make install && ldconfig && systemctl enable guacd && systemctl start guacd \
&& mkdir /etc/guacamole && mv /guacfiles/guacamole.war /etc/guacamole \
&& ln -s /etc/guacamole/guacamole.war /var/lib/tomcat8/webapps/ \
&& systemctl restart tomcat8 && systemctl restart guacd && mkdir /etc/guacamole/{extensions,lib} \
&& echo "GUACAMOLE_HOME=/etc/guacamole" >> /etc/default/tomcat8 && echo "guacd-hostname:    localhost" >> /etc/guacamole/guacamole.properties \
&& echo "guacd-port:    4822" >> /etc/guacamole/guacamole.properties \
&& echo "user-mapping:  /etc/guacamole/user-mapping.xml" >> /etc/guacamole/guacamole.properties \
&& echo "auth-provider:    net.sourceforge.guacamole.net.basic.BasicFileAuthenticationProvider" >> /etc/guacamole/guacamole.properties \
&& ln -s /etc/guacamole /usr/share/tomcat8/.guacamole
