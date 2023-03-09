# Streams

Los `streams` son como un flujo de datos que van a estar pasando, si ejecutamos el codigo de abajo, no pasara nada, porque los `streams` necesita de `listeners`.`print('desde periodic $value');` deberia haber impreso esto en consola pero no paso nada. Haciendo una analogia, es como estar en un auditorio a punto de dar una charla pero si no va nadie para que empezar la charla.

```Dart
void main() {
  emitNumbers();
}

Stream<int> emitNumbers() {
  return Stream.periodic(Duration(seconds: 1), (value) {
    print('desde periodic $value');
    return value;
  });
}
```

Ahora agregamos el `listen()` y ademas agregamos el `take()`, el `take` le dice al `stream` ejecuta 5 veces y luego cierra el `stream`.

```Dart
void main() {
  emitNumbers().listen((value) {
    print('Stream value: $value');
  });
}

Stream<int> emitNumbers() {
  return Stream.periodic(Duration(seconds: 1), (value) {
    //print('desde periodic $value');
    return value;
  }).take(5);
}
```

El codigo de arriba imprimira esto:

```md
Stream value: 0
Stream value: 1
Stream value: 2
Stream value: 3
Stream value: 4
```
