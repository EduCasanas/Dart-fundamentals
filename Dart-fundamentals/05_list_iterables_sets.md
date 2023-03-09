# Listas, iterables y sets

## Listas

Las `listas` se representan con [ ]

```Dart
void main() {
  final numbers = [1, 2, 3, 4, 5, 5, 5, 6, 7, 8, 9, 9, 10];
  print('List original $numbers');
}
```

## Metodos de las listas e iterables

**Longitud de una lista: `length`**

```Dart
print('List original ${numbers.length}');//13
```

**Indice de una lista: `first`**

```Dart
print('Index 0: ${numbers[0]}');//Index 0: 1
//tambien se puede obtener el primer elemento de la lista asi:
print('Index 0: ${numbers.first}');
```

**Ultimo elemento de la lista: `last`**

```Dart
print('Index 0: ${numbers.last}');
```

**Invertir listado: `reversed`**

```Dart
print('Reversed: ${numbers.reversed}');
//Lista original: [1, 2, 3, 4, 5, 5, 5, 6, 7, 8, 9, 9, 10]
//Reversed: (10, 9, 9, 8, 7, 6, 5, 5, 5, 4, 3, 2, 1)
```

>Tomar en cuenta que ahora cambio la lista original paso de tener `[ ]` a `( )`, ahora el listado paso a ser un `iterable`.

Si ahora se quiere recuperar la lista con los [ ].

```Dart
void main() {
  final numbers = [1, 2, 3, 4, 5, 5, 5, 6, 7, 8, 9, 9, 10];
  final reversedNumbers = numbers.reversed;
  //(10, 9, 9, 8, 7, 6, 5, 5, 5, 4, 3, 2, 1)
  print('List: ${reversedNumbers.toList()}');
  //[10, 9, 9, 8, 7, 6, 5, 5, 5, 4, 3, 2, 1]
}
```

## Sets

Los `sets` se colocan entre llaves { }

```Dart
void main() {
  final numbers = [1, 2, 3, 4, 5, 5, 5, 6, 7, 8, 9, 9, 10];
  final reversedNumbers = numbers.reversed;
  print('List: ${reversedNumbers.toList()}');
  //[10, 9, 9, 8, 7, 6, 5, 5, 5, 4, 3, 2, 1]
  print('Set: ${reversedNumbers.toSet()}');
  //Set: {10, 9, 8, 7, 6, 5, 4, 3, 2, 1}
}
```

>Notar que los `sets` son un conjunto de elementos unicos, como podemos ver el listado original contenia elementos repetidos,ahora en el `set` solo aparecen valores unicos sin repetirse.

Si quisiera quitar elementos repetidos de una lista, manteniendo su tipo de variable Lista, haria lo siguiente:

```Dart
void main() {
  final numbers = [1, 2, 3, 4, 5, 5, 5, 6, 7, 8, 9, 9, 10];
  print('List original no repetion: ${numbers.toSet().toList()}');
  //List original no repetion: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
}
```

## Mas metodos de los Iterables `where`

```Dart
void main() {
  final numbers = [1, 2, 3, 4, 5, 5, 5, 6, 7, 8, 9, 9, 10];
  final numbersGreaterThan5 = numbers.where((int num) {
    return num > 5;
  });
  print('>5 iterable: $numbersGreaterThan5');
  //>5 iterable: (6, 7, 8, 9, 9, 10)
}
```

>Lo anterior me dio un iterable, pero tiene elementos repetidos, ahora lo quiero sin esos elementos repetidos, aplico un `set`.

```Dart
void main() {
  final numbers = [1, 2, 3, 4, 5, 5, 5, 6, 7, 8, 9, 9, 10];
  final numbersGreaterThan5 = numbers.where((int num) {
    return num > 5;
  });
  print('>5 iterable: $numbersGreaterThan5');
  //>5 iterable: (6, 7, 8, 9, 9, 10)
  print('>5 set: ${numbersGreaterThan5.toSet()}');
  //>5 set: {6, 7, 8, 9, 10}
}
```
