## INFRAESTRUCTURE NGINX-LETSENCRYPT + WORDPRESS*2 + MOODLE
Thanks to kevingo710 for this project.
(just trying to use the latest version of moodle)

Clone this project
  1. Clone repo
  2. Change domains in docker-compose
  2. `docker-compose up -d` ./
  3. `docker-compose up -d` /anyService
  4. Moodle after install error IP-> check nginx_container IP & exec in moodleDB_container `docker exec -it moodleDB_container mysql -uroot -p`  -> `use moodledb`;
  --> `UPDATE mdl_user set lastip='172.docker.nginx.IP' where username='admin';`
  5. WordPress Plugin e-mail -> [WP Mail SMTP by WPForms](https://es.wordpress.org/plugins/wp-mail-smtp/)
  6. WordPress Plugin contact-form -> [Contact Form 7](https://es.wordpress.org/plugins/contact-form-7/)
  7. * Change Upload Max File Size
    ## NGINX (nginx container)
      -> docker exec -it nginx-proxy bash
      -> cd /etc/nginx/conf.d
      -> cat > my.conf
      -> client_max_body_size 100M;
      close (ctrl + D)
    ## MOODLE (moodle container)
      -> docker exec -it moodle_moodleapp_1 bash
      -> cd etc/php/7.4/apache2
      -> sed -i 's/PHP_UPLOAD_MAX_FILESIZE=2M/PHP_UPLOAD_MAX_FILESIZE=100M/' php.ini
      -> sed -i 's/PHP_POST_MAX_SIZE=8M/PHP_POST_MAX_SIZE=100M/' php.ini
      close (ctrl + D)

### _Resources_:
* DigitalOcean 🛫
* Docker 🐳



![schema](./schema.png)




## Expressions of gratitude 🎁

* Share this project 📢
* Invite me a coffee ☕  
* Give me a star ⭐




---


<p>
    <a href="https://twitter.com/intent/follow?screen_name=kevingrac7">
    <img src="https://img.shields.io/twitter/follow/kevingrac7?style=social"
    alt="follow on Twitter">
    </a>
<p>
