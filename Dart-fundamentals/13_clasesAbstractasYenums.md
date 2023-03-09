# Clases abstractas y Enums

Las `clases abstractas` se puede ver como un molde que va a ayudar a crear otros moldes. Estas no pueden instanciar nuevos objetos. Los `enums` sirven para delimitar el tipo de opciones disponibles.

```Dart
void main() {}

//cuando quiere delimitar el tipo de opciones
enum PlantType { nuclear, wind, water } //ojo los enums no terminan con ;

//clase abstracta
abstract class EnergyPlant {
  double energyLeft;
  String type; //nuclear, wind, water

  //constructor
  EnergyPlant({required this.energyLeft, required this.type});

  //metodo
  void consumeEnergy(double amount);
}
```

>Si existieran mas metodos comunes a otras clases, se los puede definir en la clase abstracta, pero no se deben `implementar`, con implementacion se refiere a que no se deben realizar calculos aun, solo definir los metodos como lo hicimos con `consumeEnergy`, ya que estos metodos seran sobreescritos con un `@override` en la clase que queremos implementar la clase abstracta.
