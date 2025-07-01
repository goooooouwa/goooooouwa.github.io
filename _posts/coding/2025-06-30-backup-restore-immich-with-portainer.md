---
title: Restore data for Immich with Portainer
category: coding
tags: immich portainer postgres docker
published: true
---
## 1. Backup Postgres DB
docker exec -t immich_postgres pg_dumpall --clean --if-exists --username=postgres | gzip > "/path/to/backup/dump.sql.gz"

## 2. Restor Postgres DB

### 2.1 Deletes all Immich data to start from scratch

1. Remove all immich related containers from portainer (check option to remove all unamed volumes)
1. Backup named volumes by renaming them to a different name with [this convenient tool](https://www.commands.dev/workflows/rename_docker_volume) (remember to check the generated commands before running, consider remove the last `docker volume rm` command to avoid accidentally data loss)
1. Remove immich named volumes from portainer:
	1. immich_pgdata
	1. immich_model-cache
1. Remove all unused images from portaineer (including `tensorchord/pgvecto-rs` & `redis`)

### 2.2 Start `immich_postgres` alone without starting `immich_server`, `immich_machine_learning` & `immich_redis`

1. Comment out all other services except `immich_postgres` in `docker-compose.yml`
1. Pull & redeploy all immich images & containers to start `immich_postgres` alone without starting other services


  
## References

- https://immich.app/docs/administration/backup-and-restore/
