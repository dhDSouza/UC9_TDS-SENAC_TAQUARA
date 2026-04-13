# **Aula de Revisão de POO em C#**

## **0. Criando um Projeto em C#**

Antes de começar, precisamos criar um projeto para rodar os exemplos.

### **✔️ Usando o .NET CLI (terminal)**

1. Verifique se o .NET está instalado:

```bash
dotnet --version
```

2. Crie um novo projeto:

```bash
dotnet new console -n AulaPOO
```

3. Entre na pasta:

```bash
cd AulaPOO
```

4. Execute o projeto:

```bash
dotnet run
```

## **1. O que é POO?**

POO (**Programação Orientada a Objetos**) é um paradigma de programação que organiza o código em **objetos**, que representam **coisas do mundo real** ou **conceitos abstratos**, cada um com **atributos** (características) e **métodos** (ações).

> [!TIP]
> Analogia: pense em um **carro**:
>
> * Atributos: cor, modelo, ano
> * Métodos: ligar(), acelerar(), frear()

**Em C#, **quase tudo gira em torno de classes e objetos**.**

---

## **2. Classes e Objetos**

### **2.1. Classe**

É o **molde ou planta** do objeto.

```csharp
public class Carro
{
    // Atributos (propriedades)
    public string Cor;
    public string Modelo;
    public int Ano;

    // Método (ação)
    public void Ligar()
    {
        Console.WriteLine("O carro está ligado.");
    }

    public void Acelerar()
    {
        Console.WriteLine("O carro está acelerando.");
    }
}
```

### **2.2. Objeto**

É a **instância da classe**, ou seja, um “carro real” criado a partir do molde.

```csharp
Carro meuCarro = new Carro(); // Criando um objeto
meuCarro.Cor = "Vermelho";
meuCarro.Modelo = "Fusca";
meuCarro.Ano = 1970;

meuCarro.Ligar();
meuCarro.Acelerar();
```

✅ Dica: sempre que você cria `new Carro()`, está criando um objeto **independente**.

---

## **3. Construtores**

Construtores são métodos especiais usados para **inicializar objetos** com valores.

```csharp
public class Carro
{
    public string Cor;
    public string Modelo;
    public int Ano;

    // Construtor
    public Carro(string cor, string modelo, int ano)
    {
        Cor = cor;
        Modelo = modelo;
        Ano = ano;
    }
}

Carro meuCarro = new Carro("Azul", "Gol", 2020);
Console.WriteLine(meuCarro.Modelo); // Gol
```

> [!TIP]
> Analogia: o construtor é como o ato de **montar o carro na fábrica**, já saindo pronto com cor, modelo e ano.

---

## **4. Encapsulamento**

Encapsulamento significa **proteger os dados** e controlar como eles são acessados.

Usamos **propriedades (properties)** para isso:

```csharp
using System;

public class Pessoa
{
    private string nome; // privado
    private int idade;

    // Método para obter o nome
    public string getNome()
    {
        return nome;
    }

    // Método para definir o nome
    public void setNome(string novoNome)
    {
        nome = novoNome;
    }

    // Método para obter a idade
    public int getIdade()
    {
        return idade;
    }

    // Método para definir a idade
    public void setIdade(int novaIdade)
    {
        if (novaIdade >= 0)
        {
            idade = novaIdade;
        }
        else
        {
            Console.WriteLine("Idade inválida!");
        }
    }
}

Pessoa p = new Pessoa();
p.Nome = "João";
p.Idade = 25;
```

✅ Benefício: podemos **validar valores** antes de definir atributos.

---

## **5. Herança**

Herança permite que uma classe **herde atributos e métodos de outra**.

```csharp
public class Animal
{
    public string Nome;
    public void Dormir() => Console.WriteLine($"{Nome} está dormindo.");
}

// Herança
public class Cachorro : Animal
{
    public void Latir() => Console.WriteLine($"{Nome} está latindo!");
}

Cachorro dog = new Cachorro();
dog.Nome = "Rex";
dog.Dormir(); // herdado
dog.Latir();  // específico do cachorro
```

> Analogia: Cachorro **é um** Animal, logo herda tudo de Animal.

---

## **6. Polimorfismo**

Polimorfismo significa **um mesmo método agir de formas diferentes**.

### **6.1. Polimorfismo por sobreposição (override)**

```csharp
public class Animal
{
    public virtual void Som() => Console.WriteLine("Som genérico de animal");
}

public class Cachorro : Animal
{
    public override void Som() => Console.WriteLine("Au au!");
}

Animal meuAnimal = new Cachorro();
meuAnimal.Som(); // "Au au!"
```

> `virtual` indica que o método pode ser sobrescrito, `override` sobrescreve.

---

## **7. Abstração**

Abstração é **ocultar detalhes desnecessários** e mostrar apenas o essencial.

```csharp
public abstract class Forma
{
    public abstract double CalcularArea();
}

public class Quadrado : Forma
{
    public double Lado;
    public override double CalcularArea() => Lado * Lado;
}

Quadrado q = new Quadrado { Lado = 4 };
Console.WriteLine(q.CalcularArea()); // 16
```

> Você **não pode criar** um objeto de `Forma`, mas classes derivadas podem implementar o método.

---

## **8. Interfaces**

Interfaces definem **contratos que as classes devem seguir**.

```csharp
public interface IAnimal
{
    void Som();
}

public class Gato : IAnimal
{
    public void Som() => Console.WriteLine("Miau!");
}

IAnimal meuGato = new Gato();
meuGato.Som(); // Miau!
```

> Diferente de abstração, interfaces **não têm implementação**, só definem os métodos.

---

## **9. Exercícios Práticos**

1. Criar uma classe `Livro` com propriedades: `Titulo`, `Autor`, `Ano`.
   Adicione um método `ExibirInfo()` que imprime os detalhes do livro.

2. Criar uma classe `Funcionario` com encapsulamento no atributo `Salario`.
   Se o salário for negativo, mostrar mensagem de erro.

3. Criar herança:

   * Classe `Veiculo` com método `Mover()`.
   * Classe `Bicicleta` que herda `Veiculo` e adiciona `DarGrau()`.

4. Criar polimorfismo:

   * Classe `Forma` abstrata com método `CalcularArea()`.
   * Criar `Circulo` e `Triangulo` que implementam `CalcularArea()`.
