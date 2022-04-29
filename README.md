# bot-feeder-www
My way of dealing with exploit bots that attack our WWW servers.
## WARNING: NOT ALL TECHNIQUES ARE USEFUL TO YOUR WEBSITE

### Step 1. Locate the issue...

149.28.132.x - - [28/Apr/2022:06:54:15 -0500] "GET / HTTP/1.1" 200 65764
149.28.132.x - - [28/Apr/2022:06:54:20 -0500] "GET / HTTP/1.1" 200 65787
149.28.132.x - - [28/Apr/2022:06:54:25 -0500] "GET /wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:25 -0500] "GET /xmlrpc.php?rsd HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:26 -0500] "GET / HTTP/1.1" 200 65788
149.28.132.x - - [28/Apr/2022:16:13:34 -0500] "GET /wp-login.php HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:29 -0500] "GET /blog/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:29 -0500] "GET /web/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:30 -0500] "GET /wordpress/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:30 -0500] "GET /website/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:30 -0500] "GET /wp/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:31 -0500] "GET /news/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:31 -0500] "GET /2018/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:31 -0500] "GET /2019/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:32 -0500] "GET /shop/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:32 -0500] "GET /wp1/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:32 -0500] "GET /test/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:33 -0500] "GET /media/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:33 -0500] "GET /wp2/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:33 -0500] "GET /site/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:34 -0500] "GET /cms/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
149.28.132.x - - [28/Apr/2022:06:54:34 -0500] "GET /sito/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59

### Step 2. Come up with solution...

#### Create the file location and file they are searching.
#### So for instance if they are searching /wp-login.php on a NON wordpress page.
#### Create /wp-login.php + /loop.php
##### loop.php <?php echo "<meta http-equiv='refresh' content='0;url=wp-login.php'>"; ?>
##### wp-login.php <?php echo "<meta http-equiv='refresh' content='0;url=loop.php'>"; ?>

/wp-login.php HTTP/1.1" 404 59
/ HTTP/1.1" 200 65764
/ HTTP/1.1" 200 65787
/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/xmlrpc.php?rsd HTTP/1.1" 404 59
/ HTTP/1.1" 200 65788
/blog/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/web/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/wordpress/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/website/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/wp/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/news/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/2018/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/2019/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/shop/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/wp1/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/test/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/media/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/wp2/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/site/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/cms/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59
/sito/wp-includes/wlwmanifest.xml HTTP/1.1" 404 59

### Step 3. Do this for all the following PHP searches that exploit bots are seeking.
