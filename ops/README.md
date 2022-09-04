# Create user

```javascript
db.createUser(
  {
    user: "studen",
    pwd: "…",
    roles: [ { role: "readWrite", db: "TP" } ]
  }
)
```