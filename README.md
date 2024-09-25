# pdd-assignments-assignment01
Actividad B2.1

Descripción del programa
Este programa es una implementación del patrón de diseño creacional Factory Method en C#. Dado que al girar la ruleta el resultado fue "Creacional, Aviación y Extensibilidad y Mantenibilidad". En este caso, apliqué el patrón en el dominio de la aviación, donde diferentes tipos de aviones (comerciales, de carga) deben crearse de manera flexible y extendible, sin modificar el código principal cuando se añadan nuevos tipos de aviones en el futuro.

Funcionamiento del Programa
El programa modela un sistema de aviación donde:

Se pueden crear diferentes tipos de aviones (comerciales y de carga) usando una fábrica que abstrae la creación de objetos.
El patrón Factory Method permite cambiar o agregar nuevos tipos de aviones sin modificar la lógica existente, lo que mejora la extensibilidad y mantenibilidad del sistema.


#Código
using System;

// Producto: Define la interfaz común para todos los tipos de aviones
public interface IAvion
{
    void Volar();
}

// Producto Concreto: Avión Comercial
public class AvionComercial : IAvion
{
    public void Volar()
    {
        Console.WriteLine("Avión Comercial volando con pasajeros.");
    }
}

// Producto Concreto: Avión de Carga
public class AvionCarga : IAvion
{
    public void Volar()
    {
        Console.WriteLine("Avión de Carga volando con mercancía.");
    }
}

// Creador Abstracto: Define el método de fábrica para crear aviones
public abstract class CreadorAvion
{
    public abstract IAvion CrearAvion();
}

// Creador Concreto: Fábrica de Aviones Comerciales
public class CreadorAvionComercial : CreadorAvion
{
    public override IAvion CrearAvion()
    {
        return new AvionComercial();
    }
}

// Creador Concreto: Fábrica de Aviones de Carga
public class CreadorAvionCarga : CreadorAvion
{
    public override IAvion CrearAvion()
    {
        return new AvionCarga();
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Crear una fábrica de aviones comerciales
        CreadorAvion creadorComercial = new CreadorAvionComercial();
        IAvion avionComercial = creadorComercial.CrearAvion();
        avionComercial.Volar(); // Salida: "Avión Comercial volando con pasajeros."

        // Crear una fábrica de aviones de carga
        CreadorAvion creadorCarga = new CreadorAvionCarga();
        IAvion avionCarga = creadorCarga.CrearAvion();
        avionCarga.Volar(); // Salida: "Avión de Carga volando con mercancía."

        // Evita que la consola se cierre inmediatamente
        Console.ReadLine();
    }
}




#Ejemplo de Uso
En este ejemplo, el sistema crea dos tipos de aviones:

Un avión comercial que transporta pasajeros.
Un avión de carga que transporta mercancías.
Ambos tipos de aviones son creados de manera flexible usando el Factory Method, lo que permite agregar nuevos tipos de aviones sin modificar el código principal. Esto mejora la extensibilidad y mantenibilidad del sistema.

Código ejemplo:

// Crear una fábrica de aviones comerciales
CreadorAvion creadorComercial = new CreadorAvionComercial();
IAvion avionComercial = creadorComercial.CrearAvion();
avionComercial.Volar(); // Salida: "Avión Comercial volando con pasajeros."

// Crear una fábrica de aviones de carga
CreadorAvion creadorCarga = new CreadorAvionCarga();
IAvion avionCarga = creadorCarga.CrearAvion();
avionCarga.Volar(); // Salida: "Avión de Carga volando con mercancía."



#Conclusión
Este proyecto demuestra cómo el patrón Factory Method permite la creación flexible de diferentes tipos de aviones (comerciales y de carga). Este enfoque mejora la extensibilidad y mantenibilidad del sistema, ya que permite agregar nuevos tipos de aviones sin modificar el código existente.

Ventajas del Patrón Factory Method:
Extensibilidad: Se pueden agregar nuevos tipos de aviones sin alterar el código base.
Mantenibilidad: Al tener el código desacoplado, es más fácil mantener y escalar el sistema cuando se agreguen nuevos tipos de aviones o características.

