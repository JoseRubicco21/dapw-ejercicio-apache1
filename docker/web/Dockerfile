# Iniciamos desde una Imagen de Debian 12.
FROM debian:12

# Instalamos apache2 y php.
RUN apt update && apt install -y apache2 php

# Modificamos el archivo security.conf para mostrar menos información con el comando sed.

# Limita lo mostrado por la directiva ServerToken a lo mas minimo. 
RUN sed -i -E "s/^ServerTokens OS$/ServerTokens Prod/" /etc/apache2/conf-available/security.conf

# Quita la firma del servidor. Ya no se mostrará que es un servidor apache, simplemente un servidor.
RUN sed -i -E "s/^ServerSignature.*/ServerSignature Off/" /etc/apache2/conf-available/security.conf

# Redirecciona todos los accesos a una carpeta .git/ a un error 404.
RUN sed -i -E "s/^#RedirectMatch 404 \/\\\.git/RedirectMatch 404 \/\\\.git/" /etc/apache2/conf-available/security.conf

# Habilita el módulo SSL de apache2 para utilizar el virtual host con SSL creado.
RUN a2enmod ssl

# Expone los puertos 80 y 443 para poder conectarse por HTTP y HTTPS
EXPOSE 80
EXPOSE 443

# Lanza el servidor apache2 en primer plano.
ENTRYPOINT [ "apachectl", "-D", "FOREGROUND" ]