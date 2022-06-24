**1. Deletar a chave "pesquisa:produto"**
```
127.0.0.1:6379> del pesquisa:produto
(integer) 1
```

**2. Criar a chave "pesquisa:produto" do tipo set ordenado com os seguintes valores:**

```
Valor: monitor, Score: 100
Valor: HD, Score: 20
Valor: mouse, Score: 10
Valor: teclado, Score: 50
```
```
127.0.0.1:6379> zadd pesquisa:produto 100 monitor 100 hd 10 mouse 50 teclado
(integer) 4
```

O score representa a quantidade de pesquisas feitas para aquele produto na aplicação

**1. Visualizar a quantidade de produtos**
```
127.0.0.1:6379> zcard pesquisa:produto
(integer) 4
```

**2. Visualizar todos os produtos do mais pesquisado ao menos pesquisado**

```
127.0.0.1:6379> zrevrange pesquisa:produto 0 -1 withscores       
1) "monitor"
2) "100"
3) "hd"
4) "100"
5) "teclado"
6) "50"
7) "mouse"
8) "10"
```

**3. Visualizar o rank do produto teclado**
```
127.0.0.1:6379> zrank pesquisa:produto teclado
(integer) 1
```
**4. Visualizar o score do produto teclado**

```
127.0.0.1:6379> zscore pesquisa:produto teclado
"50"
```

**5. Remover o valor HD da chave**
```
127.0.0.1:6379> zrem pesquisa:produto hd
(integer) 1
```

**6. Recuperar e remover do set o produto mais pesquisado**
```
127.0.0.1:6379> zpopmax pesquisa:produto
1) "monitor"
2) "100"
```

**7. Recuperar e remover do set o produto menos pesquisado**
```
127.0.0.1:6379> zpopmin pesquisa:produto
1) "mouse"
2) "10"
```

**8. Visualizar todos os produtos**
```
127.0.0.1:6379> zrange pesquisa:produto 0 -1
1) "teclado"
```