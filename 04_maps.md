# Maps

Los `maps` se componen de `clave` y `valor` y se colocan con llaves {}

```Dart
void main() {
  final pokemon = {
    'name' : 'Ditto',
    'hp' : 100,
  };
}
```

Es comun encontrar un `map` asi:

```Dart
final Map<String, dynamic> pokemon{
    'clave' : 'valor'
}
```

>donde <String, dynamic> `String` es el tipo de variable de la clave y `dynamic` es el tipo de variable del valor.

Pero tambien hay otros tipos de `maps` con clave `entero` y valor `string`.

```Dart
final pokemons = {
    1 : 'ABC',
    2 : 'XYZ',
    3 : '123',
    150 : 'AGJH'
};
```

Aqui vemos un `map` que contiene otros tipos de variables e incluso un `map` dentro de otro `map`.

```Dart
void main() {
  final pokemon = {
    'name' : 'Ditto',
    'hp' : 100,
    'isAlive' : true,
    'abilities' : <String>['impostor'],
    'sprites' : {
        1 : 'ditto/front.png',
        2 : 'ditto/back.png'
    }
  };
}
```

>podemos agregar el `map` tambien de la siguiente forma, pero la forma que se establecio arriba, permite que dart infiera el tipo, ya vimos que dart es bueno infiriendo los tipos de `clave` y `valor`.

```Dart
'sprites' : Map<int, String>{
        1 : 'ditto/front.png',
        2 : 'ditto/back.png'
    }
```

Para imprimir el valor de la variable name que esta dentro del `map`, hariamos lo siguiente:

```Dart
print(pokemon);//esto imprime todo el map
print('Name: ${pokemon['name']}');//esto imprime: Name: Ditto
```

Ahora si queremos acceder a los valores del `map sprites` lo haremos de la siguiente manera:

```Dart
print('Back: ${pokemon['sprites'][2]}');
print('Front: ${pokemon['sprites'][1]}');
```
