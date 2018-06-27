# Redis short guide

## What is Redis?

- Redis is a map (key-value pairs set)
- Redis keys and values can be only strings


## How to enter redis client in console? 
```
> resis-cli
```

## Whats next?

Use theese commands:
- `> GET key`
- `> SET mykey "string"`
- `> RENAME key newkey` (warn: if newkey already exists - overwrites value)
  - `> RENAMENX key newkey` - if newkey does not exist
- `> DEL key`
  - `> UNLINK key` - nonblocking acync DEL
- `> KEYS regexp`
  - `> KEYS *` - all keys

---

> Redis values can be only strings

I lied. Value can also be a hashmap.

Then each value of hashmap has 2 keys: name of hashmap and field name. Hmap values are really only strings.

- `> HGET key field`
- `> HSET key field value`
- `> HDEL key field` 
  and so on...

---

[All Redis commands](https://redis.io/commands)