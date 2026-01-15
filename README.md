# obsidian-livesync
Self hosted livesync for Obsidian

Based off [this guide by vrtmrz](https://github.com/vrtmrz/obsidian-livesync)

## Step 1
#### Creating the save data & configuration directories.

```
mkdir -p couchdb-data \
mkdir -p couchdb-etc
```

## Step 2
#### Create the docker compose file


Found [here](https://github.com/vrtmrz/obsidian-livesync/blob/main/docs/setup_own_server.md#b-using-docker-compose) under the docker compose section.
run the usual `docker compose up -d`
If your container threw an error or exited unexpectedly, please check the permission of couchdb-data, and couchdb-etc.
Once CouchDB starts, these directories will be owned by uid:5984. Please chown it for that uid again.

## Step 3
#### Initialise couchdb


Run this WITHIN the docker container that is running couchdb.
```
curl -s https://raw.githubusercontent.com/vrtmrz/obsidian-livesync/main/utils/couchdb/couchdb-init.sh | hostname=http://<YOUR SERVER IP>:5984 username=<INSERT USERNAME HERE> password=<INSERT PASSWORD HERE> bash
```

Example on localhost with user: praxis and pass: pascale for example

```
curl -s https://raw.githubusercontent.com/vrtmrz/obsidian-livesync/main/utils/couchdb/couchdb-init.sh | hostname=http://localhost:5984 username=pascale password=pascale bash
```

