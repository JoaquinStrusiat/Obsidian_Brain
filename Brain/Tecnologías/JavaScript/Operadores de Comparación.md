## Operadores de Comparación
#operadores #comparación
Los operadores de comparación se utilizan para comparar dos valores. Devuelven un valor booleano (`true` o `false`).

### Tipos de operadores y sus ejemplos:
##### **Igualdad** 
- `==` : Compara dos valores para ver si son iguales (sin tener en cuenta el tipo).
``` js
console.log(5 == '5'); // true
```
 
##### **Estrictamente Igual** 
 - `===` : Compara dos valores para ver si son exactamente iguales (incluyendo el tipo).
``` js
console.log(5 === '5'); // false
console.log(5 === 5); // true
```

##### **Desigualdad** 
- `!=` : Compara dos valores para ver si son diferentes (sin tener en cuenta el tipo).
``` js
console.log(5 != '5'); // false
```

##### **Desigualdad Estricta** 
- `!==` : Compara dos valores para ver si son exactamente diferentes (incluyendo el tipo).
``` js
console.log(5 !== '5'); // true
console.log(5 !== 5); // false
```

##### **Mayor que** 
- `>`: Compara si el valor de la izquierda es mayor que el valor de la derecha.
``` js
console.log(10 > 5); // true
```

##### **Menor que** 
- `<`: Compara si el valor de la izquierda es menor que el valor de la derecha.
``` js
console.log(5 < 10); // true
```

##### **Mayor o igual que** 
- `>=`: Compara si el valor de la izquierda es mayor o igual que el valor de la derecha.
``` js
console.log(10 >= 5); // true
console.log(5 >= 5); // true
```

##### **Menor o igual que** 
- `<=`: Compara si el valor de la izquierda es menor o igual que el valor de la derecha.
``` js
console.log(5 <= 10); // true
console.log(5 <= 5); // true
```
