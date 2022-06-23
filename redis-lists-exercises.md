**1. Criar a chave "views:ultimo_usuario" e insira nesta ordem os seguintes valores como lista:**
```
Final da lista "Joao"
Final da lista "Ana"
Inicio da lista "Carlos"
Final da lista "Carol"
```
```
127.0.0.1:6379> lpush views:ultimo_usuario Carlos
(integer) 1
127.0.0.1:6379> rpush views:ultimo_usuario Joao
(integer) 2
127.0.0.1:6379> rpush views:ultimo_usuario Ana
(integer) 3
127.0.0.1:6379> rpush views:ultimo_usuario Carol
(integer) 4

```

**2. Visualizar todos os elementos da lista**

```
127.0.0.1:6379> lrange views:ultimo_usuario 0 -1
1) "Carlos"
2) "Joao"
3) "Ana"
4) "Carol"
```

3. Visualizar todos os elementos da lista, com exceção do último

```
127.0.0.1:6379> lrange views:ultimo_usuario 0 -2
1) "Carlos"
2) "Joao"
3) "Ana"
```

4. Visualizar o tamanho da lista

```
127.0.0.1:6379> llen views:ultimo_usuario
(integer) 4 
```

5. Redefinir o tamanho da lista, removendo o primeiro elemento (Sem usar o pop)

6. Visualizar o tamanho da lista

7. Recuperar os elementos da lista da seguinte ordem:

Primeiro
Último
Primeiro com bloqueio de 5 segundos se a lista estiver vazia
Primeiro com bloqueio de 5 segundos se a lista estiver vazia