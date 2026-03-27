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
