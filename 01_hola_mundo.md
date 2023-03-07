# DART

## Introduccion

Siempre se recomienda que toda variable o funcion se especifique su tipo de dato, en este caso la funcion principal que ejecuta nuestro programa se llama `main`, la palabra `void` indica que es una funcion que no retorna nada, es decir indicamos a Dart que no espere ningun valor de la funcion.

## Variable tipo `var`

Tipo de variable que va a ser inferido.

```Dart
void main() {
  var myName = 'Edu'; 
  //runtimeType imprime el tipo de dato de myName
  print(myName.runtimeType);//String
  print(myName);
}
```

Como vimos myName se volvio tipo `String` por lo tanto si queremos modificar su tipo ya NO se puede. Pero si podemos modificar su valor por otro del mismo tipo String.

```Dart
void main() {
  var myName = 'Edu';
  print(myName);
  myName = 123;//da error, un tipo int no puede ser asignado a un tipo String. Si en lugar de 123, colocamos '123' ya no daria error porque reconoce como un String.
  print(name);
}
```

## Variable tipo `final`

```Dart
void main() {
  final myName = 'Edu';
  print(myName);
}   
```

Si ahora intento cambiar el valor por uno del mismo tipo, me da error:

```Dart
void main() {
  final myName = 'Edu';
  print(myName);
  myName = 'jorge';//error myName solo puede asignarse una vez
  print(myName);
}
```

## Variable tipo `late final`

Asignacion tardia

```Dart
void main() {
  late final myName;
  myName = 'jorge';
  print(myName);
}
```

>Es util cuando en ese momento no se dispone del dato, pero se sabe que luego se asignara su valor.

## Variable tipo `const`

```Dart
void main() {
  const myName = 'edu';
  print(myName);
}
```

`const` sirve para crear una constante en tiempo de construccion. Si yo se que la variable nunca va a cambiar de valor asigno como constante. Esto ayuda a la velocidad de dart y flutter.

`final` se asigna en tiempo de ejecucion, lo utilizo cuando en un determinado tiempo yo necesito calcular el valor de la variable usaria `final` en lugar de `const`.

## Interpolacion

Cuando se quiere solamente leer la variable dentro de un string:

```Dart
  print('Hola $myName');
```  

Cuando se requierre hacer algun calculo, o aplicar una funcion:

```Dart
  print('Hola ${myName.toUpperCase()}');
  print('Hola ${1 + 1}');
```
