# Async-await try-catch

`Async-await` se usan en conjunto con los `Futures`, y sirve para especificar a `Dart` que tiene que esperar la promesa de respuesta primero antes de continuar ejecutando el resto de codigo. A diferencia de solo usar el `Future` en el que el codigo se ejecutaba linea por linea sin restriccion alguna mientras tanto esperaba la promesa de respuesta.

```Dart
void main() async {
  print('Inicio del programa');

  try {
    final value = await httpGet('https://educa.com/cursos');
    print(value);
  } catch (err) {
    print('Tenemos un error: $err');
  }

  print('Fin del programa');
}

Future<String> httpGet(String url) async {
  await Future.delayed(const Duration(seconds: 2));

  throw 'Error en la peticion';

  //return 'Tenemos un valor de la peticion';
}
```