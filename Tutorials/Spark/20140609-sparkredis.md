title: SparkRedis
link: https://docs.gamesparks.net/documentation/cloud-code-api/spark-cloud-code-api/sparkredis
author: GameSparks
description: 
post_id: 4032
created: 2014/06/09 09:33:06
created_gmt: 2014/06/09 09:33:06
comment_status: closed
post_name: sparkredis
status: publish
post_type: post

<!--Provides access to the Games Redis Instance. -->

# SparkRedis

[toc] 

Provides access to the Games Redis Instance.

Rather than copy and paste the excellent documentation from the Redis site, we've opted to link to the relevant page through the documentation.

e.g.
    
    
    var redis = Spark.getRedis();

* * *

### append

**signature** append(string key, string value)

**returns** number

See <http://redis.io/commands/append>

* * *

### bitcount

**signature** bitcount(string key, number start, number end)

**returns** number

See <http://redis.io/commands/bitcount>

* * *

**signature** bitcount(string key)

**returns** number

See <http://redis.io/commands/bitcount>

* * *

### bitop

**signature** bitop(string op, string destKey, string[] srcKeys)

**returns** number

See <http://redis.io/commands/bitop>

* * *

### decr

**signature** decr(string key)

**returns** number

See <http://redis.io/commands/decr>

* * *

### decrBy

**signature** decrBy(string key, number integer)

**returns** number

See <http://redis.io/commands/decrBy>

* * *

### del

**signature** del(string[] keys)

**returns** number

See <http://redis.io/commands/del>

* * *

### exists

**signature** exists(string key)

**returns** boolean

See <http://redis.io/commands/exists>

* * *

### expire

**signature** expire(string key, number seconds)

**returns** number

See <http://redis.io/commands/expire>

* * *

### expireAt

**signature** expireAt(string key, number unixTime)

**returns** number

See <http://redis.io/commands/expireAt>

* * *

### get

**signature** get(string key)

**returns** string

See <http://redis.io/commands/get>

* * *

### getbit

**signature** getbit(string key, number offset)

**returns** boolean

See <http://redis.io/commands/getbit>

* * *

### getrange

**signature** getrange(string key, number startOffset, number endOffset)

**returns** string

See <http://redis.io/commands/getrange>

* * *

### hdel

**signature** hdel(string key, string[] fields)

**returns** number

See <http://redis.io/commands/hdel>

* * *

### hexists

**signature** hexists(string key, string field)

**returns** boolean

See <http://redis.io/commands/hexists>

* * *

### hget

**signature** hget(string key, string field)

**returns** string

See <http://redis.io/commands/hget>

* * *

### hgetAll

**signature** hgetAll(string key)

**returns** string[]

See <http://redis.io/commands/hgetAll>

* * *

### hincrBy

**signature** hincrBy(string key, string field, number value)

**returns** number

See <http://redis.io/commands/hincrBy>

* * *

### hincrByFloat

**signature** hincrByFloat(string key, string field, number increment)

**returns** number

See <http://redis.io/commands/hincrByFloat>

* * *

### hkeys

**signature** hkeys(string key)

**returns** string[]

See <http://redis.io/commands/hkeys>

* * *

### hlen

**signature** hlen(string key)

**returns** number

See <http://redis.io/commands/hlen>

* * *

### hmget

**signature** hmget(string key, string[] fields)

**returns** string[]

See <http://redis.io/commands/hmget>

* * *

### hmset

**signature** hmset(string key, JSON hash)

**returns** string

See <http://redis.io/commands/hmset>

* * *

### hset

**signature** hset(string key, string field, string value)

**returns** number

See <http://redis.io/commands/hset>

* * *

### hsetnx

**signature** hsetnx(string key, string field, string value)

**returns** number

See <http://redis.io/commands/hsetnx>

* * *

### hvals

**signature** hvals(string key)

**returns** string[]

See <http://redis.io/commands/hvals>

* * *

### incr

**signature** incr(string key)

**returns** number

See <http://redis.io/commands/incr>

* * *

### incrBy

**signature** incrBy(string key, number integer)

**returns** number

See <http://redis.io/commands/incrBy>

* * *

### incrByFloat

**signature** incrByFloat(string key, number increment)

**returns** number

See <http://redis.io/commands/incrByFloat>

* * *

### keys

**signature** keys(string pattern)

**returns** string[]

See <http://redis.io/commands/keys>

* * *

### lindex

**signature** lindex(string key, number index)

**returns** string

See <http://redis.io/commands/lindex>

* * *

### linsert

**signature** linsert(string key, string where, string pivit, string value)

**returns** number

See <http://redis.io/commands/linsert>

* * *

### llen

**signature** llen(string key)

**returns** number

See <http://redis.io/commands/llen>

* * *

### lpop

**signature** lpop(string key)

**returns** string

See <http://redis.io/commands/lpop>

* * *

### lpush

**signature** lpush(string key, string[] strings)

**returns** number

See <http://redis.io/commands/lpush>

* * *

### lpushx

**signature** lpushx(string key, string[] strings)

**returns** number

See <http://redis.io/commands/lpushx>

* * *

### lrange

**signature** lrange(string key, number start, number end)

**returns** string[]

See <http://redis.io/commands/lrange>

* * *

### lrem

**signature** lrem(string key, number count, string value)

**returns** number

See <http://redis.io/commands/lrem>

* * *

### lset

**signature** lset(string key, number index, string value)

**returns** string

See <http://redis.io/commands/lset>

* * *

### ltrim