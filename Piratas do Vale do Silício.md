# Atividade sobre o filme Piratas do Vale do Silício 🏴‍☠️🖥️

<div align="center">
  <img src="https://terminalroot.com.br/assets/img/movie/piratas-do-vale-do-silicio.jpg" alt="Capa do filme 'Piratas do Vale do Silício'">
  <p>Capa do filme <em>"Piratas do Vale do Silício"</em></p>
</div>

## Objetivo

Aplicar os conceitos de POO (encapsulamento, herança, polimorfismo e abstração) para construir uma simulação simples do que poderia ser uma representação dos personagens e eventos do filme "Piratas do Vale do Silício".

**Passo 1: Entendendo os Personagens**

Cada grupo será responsável por modelar um personagem principal do filme. Alguns personagens que podem ser escolhidos incluem:

* **Steve Jobs**
* **Bill Gates**
* **Steve Wozniak**
* **Paul Allen**
* **Mike Markkula**
* **Gary Kildall**
* **Roberta Williams**

> [!TIP]
> Realize uma pesquisa auxiliar sobre os personagens, para complementar a atividade

---

**Passo 2: Modelagem das Classes**

Cada grupo deverá criar uma classe em C# para os personagem escolhidos, utilizando conceitos de POO.   
A estrutura mínima de cada classe inclui:

1. **Encapsulamento:**

   * Defina atributos (variáveis) privados para os dados pessoais ou ações do personagem, como nome, idade, cargo, empresa, etc.
   * Crie métodos públicos para acessar (getter) e modificar (setter) esses atributos.
     
2. **Herança:**

   * Crie uma classe base chamada `Personagem`, que tenha atributos e métodos comuns a todos os personagens, como `Nome`, `Idade` e `Falar()`. Depois, crie subclasses específicas para cada personagem, herdando os atributos e métodos de `Personagem` e adicionando comportamentos ou atributos exclusivos.

3. **Polimorfismo:**

   * Implemente o polimorfismo usando métodos que podem ser sobrescritos nas classes filhas. Por exemplo, o método `Falar()`, onde cada personagem pode ter uma forma única de falar ou agir.

4. **Abstração:**

   * Crie métodos ou classes abstratas que representem conceitos gerais. Por exemplo, um método abstrato `CriarProduto()` na classe base `Personagem`, mas cada personagem pode implementá-lo de maneira diferente, como no caso de Jobs criando o iPhone ou Gates criando o Windows.

---

**Passo 3: Exemplo de Implementação**

Aqui está um esqueleto básico de como isso pode ser estruturado em C#:

> [!NOTE]
> _Um exemplo bem simples, diga-se de passagem 😅_

```csharp
using System;

namespace PiratasDoValeDoSilicio
{
    // Classe base
    public abstract class Personagem
    {
        public string Nome { get; set; }
        public int Idade { get; set; }

        // Método abstrato
        public abstract void CriarProduto();

        // Método comum
        public void Falar()
        {
            Console.WriteLine($"{Nome} diz: 'Vamos mudar o mundo!'");
        }
    }

    // Classe filha para Steve Jobs
    public class SteveJobs : Personagem
    {
        public string Empresa { get; set; }

        // Sobrescrita do método abstrato
        public override void CriarProduto()
        {
            Console.WriteLine($"{Nome} criou a {Empresa}.");
        }

        // Método específico
        public void Inspirar()
        {
            Console.WriteLine($"{Nome} inspira a equipe.");
        }
    }

    // Classe filha para Bill Gates
    public class BillGates : Personagem
    {
        public string Produto { get; set; }

        // Sobrescrita do método abstrato
        public override void CriarProduto()
        {
            Console.WriteLine($"{Nome} criou o {Produto}.");
        }

        // Método específico
        public void DoarDinheiro()
        {
            Console.WriteLine($"{Nome} doou dinheiro para a caridade.");
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Criando instâncias dos personagens
            SteveJobs jobs = new SteveJobs { Nome = "Steve Jobs", Idade = 56, Empresa = "Apple" };
            BillGates gates = new BillGates { Nome = "Bill Gates", Idade = 65, Produto = "Windows" };

            // Chamada de métodos
            jobs.Falar();
            jobs.CriarProduto();
            jobs.Inspirar();

            gates.Falar();
            gates.CriarProduto();
            gates.DoarDinheiro();
        }
    }
}
```

> [!IMPORTANT]
> **APESAR DO EXEMPLO ESTAR TODO EM UM ARQUIVO SÓ, LEMBRE-SE QUE DEVE SER UTILZADO UM ARQUIVO PARA CADA CLASSE.**
> **E O ARQUIVO `Program.cs` CONTENDO A CLASSE `Program` QUE EXECUTA O PROJETO.**

> [!CAUTION]
> **NÃO ESQUEÇA DE USAR CORRETAMENTE OS `namespaces` SEM ISSO O CÓDIGO NÃO IRÁ EXECUTAR!**
