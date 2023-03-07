# Parametros posicionales

>`Parametros posicionales` quiere decir que yo al pasarle a la funcion parametros, estos seran asignados conforme su posicion, por ejemplo, si yo le paso (20,10), dart asignara 20 a la primera variable a, y el otro valor de 10 a la variable b.

```Dart
void main() {
  print('Suma: ${addTwoNumbersOptional(20, 20)}');
}

int addTwoNumbersOptional(int a, [int b = 0]) {
  return a + b;
}
```

## Parametros NO posicionales

Es decir le puedo pasar los valores especificos a cada variable sin importar la posicion.
Las variables opcionales NO posicionales se colocan entre llaves { }, esto me arroja un `error` en las variables ya que Dart dice que pueden ser nulas, la solucion para permitir que sean nulas seria colocar el signo de pregunta `String? name`, pero no quiero trabajar con variables nulas.

```Dart
String greetPearson({String name, String message}) {
  return 'Hola, edu';
}
```

Por ello se hace lo siguiente:
1.-En la variable `message` se agrega un mensaje `'Hola'` este valor es usado por defecto en caso de no recibir ningun valor.
2.-`required` hace que esa variable a pesar de estar dentro de las llaves de opcionales, pida obligatoriamente el valor de `name`.

```Dart
void main() {
  print(greetPearson(name: 'Jorge'));
  //Hola, Jorge
}

String greetPearson({required String name, String message = 'Hola'}) {
  return '$message, $name';
}
```

Como vimos anteriormente, solo le pasamos el valor requerrido `name` y no dio ningun error, ahora le pasaremos el parametro opcional `message`:

```Dart
void main() {
  print(greetPearson(name: 'Jorge', message: 'Hi,'));
  //Hi, Jorge
}

String greetPearson({required String name, String message = 'Hola,'}) {
  return '$message $name';
}
```
