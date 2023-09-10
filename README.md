# redis_intro

https://www.youtube.com/watch?v=Vx2zPMPvmug&t=2355s

```
docker run -d --name redis-stack -p 6379:6379 -p 8001:8001 redis/redis-stack:latest

```

6379 is for comline

8001 port is to visualize (gui client for understanding) localhost:8001


## 
```
docker exec -it containerid bash
```

```
redis-cli
```
```
ping
```

# data types

## 1st data type strings

### set and get ,mget,setnx ,mset
```
set user:1 sachit
```

```
set user:2 ram
```
```
get user:2
```

### setnx

```
set user:1 jack nx
```
in Redis, when you use the SET command with the NX option (which stands for "Not eXists"), it will only set the value if the key does not already exist. If the key is already present, the SET command with NX will not execute, and the key's value will remain unchanged.

The SET command with NX prevented the modification of user:1 because it already existed.

### mget 
mget to get multiple value
```
mget user:1 user:2
```

### mset

mset-multiple set

```
mset bike:1 "deimos" bike2:2 "ares" bike:3 "vanth"
```

in one transaction set multiple value

### counter

```
set count 0
```

```
incr count
``` 

### limits 


<details>
  <summary>node js code
  </summary>

  mkdir redis playground

  ```
npm init
```

```
npm i ioredis
```

mkdir string.js
mkdir client.js
```
// in client.js

const {Redis} = require ('ioredis')

const client = new Redis()
module.exports=client;
```

```
//string.js
const client = require('./client);

async function init(){
  await client.set('msg:1','hey frpm me') ;
  await client.expire("msg:1",10);
  const result = await client.get("msg:1");
  console.log("Result->",result);
}

init()
```
```
node string.js
```

</details>

# redis list
36.07



