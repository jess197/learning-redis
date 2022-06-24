**1. Deletar a chave "pesquisa:produto"**

```
127.0.0.1:6379> srem pesquisa:produto
(error) ERR wrong number of arguments for 'srem' command
```

**2. Criar a chave "pesquisa:produto" do tipo set com os seguintes valores: monitor, mouse e teclado**

```
127.0.0.1:6379> sadd pesquisa:produto Monitor Mouse Teclado      
(integer) 3
```

**3. Visualizar a quantidade de valores da chave**
```
127.0.0.1:6379> scard pesquisa:produto
(integer) 3
```

**4. Retornar todos os elementos da chave**

```
127.0.0.1:6379> smembers pesquisa:produto
1) "Monitor"
2) "Teclado"
3) "Mouse"
```

**5. Verificar se existe o valor monitor**
```
127.0.0.1:6379> sismember pesquisa:produto Monitor
(integer) 1
```

**6. Remover o valor monitor**
```
127.0.0.1:6379> srem pesquisa:produto Monitor
(integer) 1
```

**7. Recuperar um elemento e remove-lo do set**
```
127.0.0.1:6379> spop pesquisa:produto
"Teclado"
```

**8. Criar a chave "pesquisa:desconto" do tipo set com os seguintes valores: memória RAM, monitor, teclado, HD**

```
127.0.0.1:6379> sadd pesquisa:desconto MemóriaRAM Monitor HD     
(integer) 3
```

**9. Próximas questões fazem uso dos sets pesquisa:produto e pesquisa:desconto**


**Visualizar a interseção entre os 2 sets**
```
127.0.0.1:6379> sinter pesquisa:produto pesquisa:desconto        
(empty array)
```
**Visualizar a diferença entre os 2 sets**
```
127.0.0.1:6379> sdiff pesquisa:produto pesquisa:desconto
1) "Mouse"
```

**Criar o set "pesquisa:produto_desconto" com a união entre os 2 sets**
```
127.0.0.1:6379> sunionstore pesquisa:produto_desconto pesquisa:produto pesquisa:desconto
(integer) 4
```

