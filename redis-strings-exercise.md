#### BASIC STRING REDIS EXERCISE 

**Using redis-cli with docker**

```
docker pull redis
docker-compose up -d 
docker exec -it redis bash
redis-cli

```

**1. Criar a chave "usuario:nome" e atribua o valor do seu nome**
``` 
127.0.0.1:6379> set usuario:nome jessica
OK
``` 

**2. Criar a chave "usuario:sobrenome" e atribua o valor do seu sobrenome**
```
127.0.0.1:6379> set usuario:sobrenome costa
OK
```

**3. Busque a chave "usuario:nome"**
```
127.0.0.1:6379> get usuario:nome
"jessica"
```

**4. Verificar o tamanho da chave "usuario:nome"**
```
127.0.0.1:6379> strlen usuario:nome
(integer) 7

```

**5. Verificar o tipo da chave "usuario:sobrenome"**

```
127.0.0.1:6379> type usuario:sobrenome
string
```

**6. Criar a chave "views:qtd" e atribua o valor 100**
```
127.0.0.1:6379> set views:qtd 100
OK
```

**7. Incremente o valor em 10 da chave "views:qtd"**

```
127.0.0.1:6379> incrby views:qtd 10
(integer) 110
```

**8. Busque a chave "views:qtd"**
```
127.0.0.1:6379> get views:qtd
"110"
```

**9. Deletar a chave "usuario:sobrenome"**

```
127.0.0.1:6379> del usuario:sobrenome
(integer) 1
```

**10. Verificar se a chave "usuario:sobrenome" existe**

```
127.0.0.1:6379> exists usuario:sobrenome
(integer) 0
```

**11. Definir um tempo de 3600 segundos para a chave "views:qtd" ser removida**
```
127.0.0.1:6379> expire views:qtd 3600
(integer) 1
```

**12. Verificar quanto tempo falta para a chave "views:qtd" ser removida**
```
127.0.0.1:6379> ttl views:qtd
(integer) 3540
```

**13. Verificar a persistência da chave "usuario:nome"**
```
127.0.0.1:6379> ttl usuario:nome
(integer) -1
```

**14. Definir para a chave "views:qtd" ter persistência para sempre**
```
127.0.0.1:6379> persist views:qtd
(integer) 1
127.0.0.1:6379> ttl views:qtd
(integer) -1
```