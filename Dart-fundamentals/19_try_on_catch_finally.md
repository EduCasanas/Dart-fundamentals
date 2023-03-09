# Try, on, catch, finally

```Dart
void main() async {
  print('Inicio del programa');

  try {
    final value = await httpGet('https://educa.com/cursos');
    print('Exito: $value');
  } on Exception catch (err) {
    print('Tenemos una excepcion: $err');
  } catch (err) {
    print('OOPs! algo terrible paso: $err');
  } finally {
    print('Fin del try and catch');
  }

  print('Fin del programa');
}

Future<String> httpGet(String url) async {
  await Future.delayed(const Duration(seconds: 3));

  throw Exception('No hay parametros en el URL');

  //throw 'Error en la peticion';
  //para un error no controlado imprimta OOPs!..

  //return 'Tenemos un valor de la peticion';
  //cuando todo sale bien, imprimira Exito: Tenemos un valor...
}
```
