##### Run Shell in php container image
```
docker exec -it [CONTAINER ID] sh
```


##### run database migration
```
docker-compose exec -T php php artisan migrate
```