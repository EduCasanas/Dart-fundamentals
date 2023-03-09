# Futures

El `Future` es una promesa de que se recibira un valor, la promesa puede fallar, y hay que manejar la excepcion.

```Dart
void main() {
  print('Inicio del programa');

  httpGet('https://educa.com/cursos').then((value) {
    print(value);
  }).catchError((err) {
    print('Error: $err');
  });

  print('Fin del programa');
}

Future<String> httpGet(String url) {
  return Future.delayed(const Duration(seconds: 1), () {
    throw 'Error en la peticion http';

    //return 'Respuesta de la peticion http';
  });
}
```
