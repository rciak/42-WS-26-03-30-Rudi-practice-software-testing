# WS

## Start docker service again after boot

In order to make the toolshop available on `http://localhost:4200/` run

```zsh
cd /home/rene/github/42-WS-26-03-30-Rudi-practice-software-testing;
docker compose up -d
docker compose logs -f angular-ui
```

## Places

* `/home/rene/WS` ->  
  `/home/rene/github/42-WS-26-03-30-Rudi-practice-software-testing`

## During Workshop

* Change sprint:
  * `echo "SPRINT=sprint5-with-bugs" > .env`
  * `echo "SPRINT=sprint5" > .env`


## From Francesco's email

### SOLUTION

When I tried to log in with the defined user in the /sprint5/API/.env in  the mariadb the user was rejected as non existing
so I modified the entry with  BD_USERNAME=root
on top of that to make sure the DB_HOST was correct instead of using `127.0.0.1`  I called directly the mariadb container:

```DB_HOST=practice-software-testing-mariadb-1```

I'm attaching the patch I set up yesterday for you to use or inspect.

**DB-settings-sprint5**

```diff
diff --git a/init-data.sh b/init-data.sh
index 192c3fb..8d51b7d 100755
--- a/init-data.sh
+++ b/init-data.sh
@@ -1 +1 @@
-docker-compose exec laravel-api php artisan migrate:fresh --seed --force
\ No newline at end of file
+docker compose exec laravel-api php artisan migrate:fresh --seed --force
diff --git a/sprint5/API/.env b/sprint5/API/.env
index 74067a5..0d1fd1c 100644
--- a/sprint5/API/.env
+++ b/sprint5/API/.env
@@ -16,10 +16,10 @@ LOG_DEPRECATIONS_CHANNEL=null
 LOG_LEVEL=debug
 
 DB_CONNECTION=mysql
-DB_HOST=127.0.0.1
+DB_HOST=practice-software-testing-mariadb-1
 DB_PORT=3306
 DB_DATABASE=toolshop
-DB_USERNAME=user
+DB_USERNAME=root
 DB_PASSWORD=root
 
 BROADCAST_DRIVER=log
```

**VERY IMPORTANT NOTE!**
in case after the data in the main page is displayed you try to open a product and it returns that it is not found it can be a problem with the local cache!
The data is correct but it might point to an older seed... 
to solve this problem just run:

```zsh
docker exec -u root practice-software-testing-web-1 sh -c "rm -rf /var/cache/nginx/*"
```

that will clean the cache
I would also suggest to be on the safe side and do:

```
 docker compose down -v
```
to clean all the container and any volume with it before running again the compose up.

**NOTE n.2**
since I forked the project there has been a substantial set of updates to the website which I just noticed today.. 
Maybe something else has changed, I'll try to merge the changes later today and see if there are any real differences or issues.

**NOTE n.3**
I haven't tried to update the 5-with-bugs sprint, I assume the same changes will do the work in the other folder too.
