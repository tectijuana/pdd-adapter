
![Cool Text - ADAPTER 468650823795874](https://github.com/user-attachments/assets/6265842c-be3c-4f14-9a79-e3acfe65fbcd)


![Adapter](https://github.com/user-attachments/assets/425a52f3-966a-44fc-b8a2-dc0a49e80331)

```chsarp
// Patrón de Diseño Adaptador
//
// Intención: Provee una interfaz unificada que permite que objetos con 
// interfaces incompatibles puedan colaborar.

using System;

namespace RefactoringGuru.DesignPatterns.Adapter.Conceptual
{
    // La clase Target define la interfaz específica del dominio que utiliza el
    // código cliente.
    public interface ITarget
    {
        string GetRequest();
    }

    // La clase Adaptee contiene comportamiento útil, pero su interfaz es
    // incompatible con el código cliente existente. Adaptee necesita 
    // adaptación para que el código cliente pueda utilizarlo.
    class Adaptee
    {
        public string GetSpecificRequest()
        {
            return "Solicitud específica.";
        }
    }

    // El Adaptador hace que la interfaz de Adaptee sea compatible con la
    // interfaz de Target.
    class Adapter : ITarget
    {
        private readonly Adaptee _adaptee;

        public Adapter(Adaptee adaptee)
        {
            this._adaptee = adaptee;
        }

        public string GetRequest()
        {
            return $"Esta es '{this._adaptee.GetSpecificRequest()}'";
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Adaptee adaptee = new Adaptee();
            ITarget target = new Adapter(adaptee);

            Console.WriteLine("La interfaz de Adaptee es incompatible con el cliente.");
            Console.WriteLine("Pero con el adaptador, el cliente puede llamar a su método.");

            Console.WriteLine(target.GetRequest());
        }
    }
}
```


