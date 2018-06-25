# curl

## Get

```bash
curl --request GET http://localhost:4545/api/values 

# with headers (add -D-)
# curl --request GET http://localhost:4545/api/values -D-
```

## Post

```bash
curl --header "Content-type: application/json" --request POST --data '{"title": "Test Title", "note": "Test note"}' http://localhost:4545/api


# Login with json
curl --header "Content-type: application/json" --request POST --data '{"user": "alvin", "password": "foobar"}' http://localhost:8888/finance/php/login.php

# Login without json
curl --request POST --data "user=alvin&password=foobar" http://localhost:8888/finance/php/login.php

# Add:
# 	-D-
# to see the headers being sent back.
```

## Put

```bash
curl --header "Content-type: application/json" --request PUT --data '{"id": 100, "title": "Test Title", "note": "Test note"}' http://localhost:4545/api

```

## Delete

```bash
curl --header "Content-type: application/json" --request DELETE --data '{"id": 1, "title": "Test Title", "note": "Test note"}' http://localhost:4545/api/
```

