# curl

### common arguments

```zsh
-s, --silent silent mode
```

### post with json data

```zsh
curl -H "Content-Type: application/json" -X POST -d '{"username":"xyz","password":"xyz"}' http://localhost:3000/api/login

```