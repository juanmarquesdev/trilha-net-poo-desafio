# DIO - Trilha .NET - Programação orientada a objetos
www.dio.me

## Desafio de projeto
Para este desafio, você precisará usar seus conhecimentos adquiridos no módulo de orientação a objetos, da trilha .NET da DIO.

## Contexto
Você é responsável por modelar um sistema que trabalha com celulares. Para isso, foi solicitado que você faça uma abstração de um celular e disponibilize maneiras de diferentes marcas e modelos terem seu próprio comportamento, possibilitando um maior reuso de código e usando a orientação a objetos.

## Proposta
Você precisa criar um sistema em .NET, do tipo console, mapeando uma classe abstrata e classes específicas para dois tipos de celulares: Nokia e iPhone. 
Você deve criar as suas classes de acordo com o diagrama abaixo:

![Diagrama classes](Imagens/diagrama.png)

## Regras e validações
1. A classe **Smartphone** deve ser abstrata, não permitindo instanciar e servindo apenas como modelo.
2. A classe **Nokia** e **Iphone** devem ser classes filhas de Smartphone.
3. O método **InstalarAplicativo** deve ser sobrescrito na classe Nokia e iPhone, pois ambos possuem diferentes maneiras de instalar um aplicativo.

## Solução

Implementar as propriedades faltantes de acordo com o diagrama
~~~csharp
    private string _modelo;
    private string _imei;
    private int _memoria;
~~~

Passar os parâmetros do construtor para as propriedades
~~~csharp
    _modelo = modelo;
    _imei = imei;
     _memoria = memoria;
~~~

Herdar da classe "Smartphone"
~~~csharp

    //[...]
    public class Nokia : Smartphone
    //[...]
    public Nokia(string numero, string modelo, string imei, int memoria) : base(numero, modelo, imei, memoria) {}
    //[...]
    public class Iphone : Smartphone
    //[...]
    public Iphone(string numero, string modelo, string imei, int memoria) : base(numero, modelo, imei, memoria) {}
~~~

Sobrescrever o método "InstalarAplicativo"
~~~csharp
    public override void InstalarAplicativo(string aplicativo)
    {
        Console.WriteLine($"Você está instalando '{aplicativo}' no Nokia");
    }
    //[...]
    public override void InstalarAplicativo(string aplicativo)
    {
        Console.WriteLine($"Você está instalando '{aplicativo}' no Iphone");
    }
~~~

Realizar os testes com as classes Nokia e Iphone
~~~csharp
    Console.WriteLine("Smartphone Nokia:");
    Smartphone nokia = new Nokia(numero: "123456", modelo: "Modelo 1", imei: "1111111111", memoria: 64);
    nokia.Ligar();
    nokia.InstalarAplicativo("Whatsapp");

    Console.WriteLine("\n");

    Console.WriteLine("Smartphone Iphone:");
    Smartphone iphone = new Iphone(numero: "4987", modelo: "Modelo 2", imei: "2222222222", memoria: 128);
    iphone.Ligar();
    iphone.InstalarAplicativo("Telegram");
~~~