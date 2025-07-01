---
title: How to restore data for Immich with Portainer
category: coding
tags: immich portainer postgres docker
published: true
---
## 1. Backup Postgres DB
docker exec -t immich_postgres pg_dumpall --clean --if-exists --username=postgres | gzip > "/path/to/backup/dump.sql.gz"

## 2. Restore Postgres DB

### 2.1 Deletes all Immich data to start from scratch

1. Remove all immich related containers from portainer (check the option to "Automatically remove non-persistent volumes")
1. Backup named volumes by renaming them to a different name with [this convenient tool](https://www.commands.dev/workflows/rename_docker_volume) (remember to check the generated commands before running, consider remove the last `docker volume rm` command to avoid accidentally data loss)
1. Remove immich named volumes from portainer:
	1. immich_pgdata
	1. immich_model-cache
1. Remove all unused images from portaineer (including `tensorchord/pgvecto-rs` & `redis`)

### 2.2 Start `immich_postgres` alone

1. Comment out all other services except `immich_postgres` in `docker-compose.yml`
1. Pull & redeploy all immich images & containers to start `immich_postgres` alone without starting other services
1. Wait for `immich_postgres` to be fully running (`immich_postgres` might only show "starting" status, it's normal. Check the log, if it says `PostgreSQL init process complete; ready for start up.`, it should be good to go, or just wait for another 10 seconds.)

### 2.3 Restore Postgres DB from dump
1. Run the following command with the dump file location to restore Postgres DB from dump:  
  `gunzip --stdout "/home/admin/immich/2025-07-01-dump.sql.gz" | sed "s/SELECT pg_catalog.set_config('search_path', '', false);/SELECT pg_catalog.set_config('search_path', 'public, pg_catalog', true);/g" | sudo docker exec -i immich_postgres psql --dbname=postgres --username=postgres`

### 2.4 Start immich as normal

1. Uncomment all other services in `docker-compose.yml`
1. Pull & redeploy all immich images & containers to start immich as normal
1. Restart nginx
1. Open immich & check if everything working as expected (scan library & regenerate thumbnails & transcode videos if necessary) 

Done!

## References

- https://immich.app/docs/administration/backup-and-restore/
