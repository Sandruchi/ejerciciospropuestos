# ejerciciospropuestos

Ejercicio 1 – Números ganadores de la lotería ordenados
using System;
using System.Collections.Generic;

class Loteria
{
    public List<int> Numeros { get; set; } = new List<int>();

    public void LeerNumeros()
    {
        Console.WriteLine("Ingrese los 6 números ganadores:");
        for (int i = 0; i < 6; i++)
        {
            Console.Write($"Número {i + 1}: ");
            int numero = int.Parse(Console.ReadLine());
            Numeros.Add(numero);
        }
        Numeros.Sort();
    }

    public void Mostrar()
    {
        Console.WriteLine("Números ordenados: " + string.Join(", ", Numeros));
    }
}

class Program
{
    static void Main()
    {
        Loteria loteria = new Loteria();
        loteria.LeerNumeros();
        loteria.Mostrar();
    }
}

Ejercicio 2 – Mostrar del 10 al 1 separados por coma
using System;
using System.Collections.Generic;

class Inversor
{
    public List<int> Numeros { get; set; }

    public Inversor()
    {
        Numeros = new List<int>();
        for (int i = 1; i <= 10; i++)
        {
            Numeros.Add(i);
        }
    }

    public void MostrarInverso()
    {
        Numeros.Reverse();
        Console.WriteLine("Números en orden inverso: " + string.Join(", ", Numeros));
    }
}

class Program
{
    static void Main()
    {
        Inversor inv = new Inversor();
        inv.MostrarInverso();
    }
}

Ejercicio 3 – Eliminar asignaturas aprobadas
using System;
using System.Collections.Generic;

class Asignatura
{
    public string Nombre { get; set; }
    public int Nota { get; set; }

    public Asignatura(string nombre)
    {
        Nombre = nombre;
    }
}

class Curso
{
    public List<Asignatura> Asignaturas { get; set; }

    public Curso()
    {
        Asignaturas = new List<Asignatura>
        {
            new Asignatura("Matemáticas"),
            new Asignatura("Física"),
            new Asignatura("Química"),
            new Asignatura("Historia"),
            new Asignatura("Lengua")
        };
    }

    public void IngresarNotas()
    {
        foreach (var a in Asignaturas)
        {
            Console.Write($"Nota en {a.Nombre}: ");
            a.Nota = int.Parse(Console.ReadLine());
        }
    }

    public void MostrarReprobadas()
    {
        List<string> reprobadas = new List<string>();
        foreach (var a in Asignaturas)
        {
            if (a.Nota < 60)
                reprobadas.Add(a.Nombre);
        }

        Console.WriteLine("Asignaturas reprobadas: " + string.Join(", ", reprobadas));
    }
}

class Program
{
    static void Main()
    {
        Curso curso = new Curso();
        curso.IngresarNotas();
        curso.MostrarReprobadas();
    }
}

Ejercicio 4 – Eliminar letras en posiciones múltiplos de 3
using System;
using System.Collections.Generic;

class Abecedario
{
    public List<char> Letras { get; set; }

    public Abecedario()
    {
        Letras = new List<char>();
        for (char c = 'A'; c <= 'Z'; c++)
        {
            Letras.Add(c);
        }
    }

    public void EliminarMultiplosDeTres()
    {
        for (int i = Letras.Count - 1; i >= 0; i--)
        {
            if ((i + 1) % 3 == 0)
            {
                Letras.RemoveAt(i);
            }
        }
    }

    public void Mostrar()
    {
        Console.WriteLine("Letras restantes: " + string.Join(", ", Letras));
    }
}

class Program
{
    static void Main()
    {
        Abecedario abc = new Abecedario();
        abc.EliminarMultiplosDeTres();
        abc.Mostrar();
    }
}

Ejercicio 5 – Verificar si es palíndromo
using System;

class Palindromo
{
    public static bool EsPalindromo(string palabra)
    {
        palabra = palabra.ToLower();
        char[] letras = palabra.ToCharArray();
        Array.Reverse(letras);
        return palabra == new string(letras);
    }

    static void Main()
    {
        Console.Write("Ingrese una palabra: ");
        string palabra = Console.ReadLine();

        if (EsPalindromo(palabra))
            Console.WriteLine("Es un palíndromo.");
        else
            Console.WriteLine("No es un palíndromo.");
    }
}

Ejercicio 6 – Contar vocales en una palabra (POO en C#)
using System;
using System.Collections.Generic;

namespace ContadorVocales
{
    class VocalCounter
    {
        private string palabra;
        private Dictionary<char, int> conteoVocales;

        public VocalCounter(string palabra)
        {
            this.palabra = palabra.ToLower(); // Convertir a minúsculas
            conteoVocales = new Dictionary<char, int>()
            {
                { 'a', 0 },
                { 'e', 0 },
                { 'i', 0 },
                { 'o', 0 },
                { 'u', 0 }
            };
        }

        public void ContarVocales()
        {
            foreach (char c in palabra)
            {
                if (conteoVocales.ContainsKey(c))
                {
                    conteoVocales[c]++;
                }
            }
        }

        public void MostrarResultado()
        {
            Console.WriteLine($"\nEn la palabra \"{palabra}\" se encuentran:");
            foreach (var kvp in conteoVocales)
            {
                Console.WriteLine($"Vocal '{kvp.Key}': {kvp.Value} veces");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Console.Write("Ingrese una palabra: ");
            string entrada = Console.ReadLine();

            VocalCounter contador = new VocalCounter(entrada);
            contador.ContarVocales();
            contador.MostrarResultado();

            Console.WriteLine("\nPresione una tecla para salir...");
            Console.ReadKey();
        }
    }
}
