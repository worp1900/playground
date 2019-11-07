# nginx-php-fpm

A basic 2 container nginx/php-fpm composition that just works.

    $ docker-compose up -d

Go to http://your-host for the nginx default welcome HTML site.

Go to http://your-host/index.php for a phpinfo() output.

Both are based on their docker-hub official base packages so they both have a Debian base. Both have vim installed. Both are built. Check their Dockerfiles.

## Disclaimer:
These images are NOT meant for production as they are large (apt cache is not cleaned, etc.). They are purely meant as a base to start something that actually works. **Do not use them directly.**
