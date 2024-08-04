# testdome-dotnet-csharp
## **Lixeira de Reciclagem**

**Considere o seguinte código:**

**C#**

```csharp
public class RecyclingBin
{
    protected List<string> recyclables = new List<string>();

    public void Add(string recyclable)
    {
        if (recyclable.Split(' ').Length > 1 && recyclable.Split(' ')[1].Length > 3)
        {
            recyclables.Add(recyclable);
        }
    }

    public List<IGrouping<string, string>> SortRecyclables()
    {
        return recyclables.GroupBy(recyclable => recyclable.Split(' ').First()).ToList();
    }
}
```

**VB.NET**

```vbnet
Public Class RecyclingBin
    Protected recyclables As List(Of String) = New List(Of String)

    Public Sub Add(recyclable As String)
        If recyclable.Split(" ").Length > 1 And recyclable.Split(" ")[1].Length > 3
            recyclables.Add(recyclable)
        End If
    End Sub

    Public Function SortRecyclables()
        Return recyclables.GroupBy(Function(recyclable) recyclable.Split(" ").First()).ToList()
    End Function
End Class
```

Selecione as afirmações que são verdadeiras se uma nova instância de `RecyclingBin` for criada e o método `Add` for chamado com os seguintes parâmetros de recicláveis: "metal pipe", "plastic toy", "metal bar", "copper wire", "plastic button", "wire" e "brass". (Selecione todas as respostas aceitáveis.)

### **Afirmações:**

1. **Um dos grupos retornados por `SortRecyclables` terá "metal" como sua chave e conterá "metal bar" e "metal pipe".**
    
    ❌ Incorreto. O método `Add` só adiciona recicláveis se a segunda palavra tiver mais de 3 caracteres. Portanto, "metal pipe" e "metal bar" são adicionados, mas "metal pipe" é a única que passa a verificação. "metal bar" não é adicionado porque a segunda palavra ("bar") tem 3 caracteres, não mais.
    
2. **Um dos grupos retornados por `SortRecyclables` terá "copper" como sua chave e conterá "copper wire".**
    
    ✅ Correto. O reciclável "copper wire" é adicionado à lista porque "wire" (a segunda palavra) tem mais de 3 caracteres. Assim, "copper" será a chave para o grupo que contém "copper wire".
    
3. **A lista retornada por `SortRecyclables` não será avaliada no método `SortRecyclables`.**
    
    ❌ Incorreto. O método `SortRecyclables` retorna a lista de grupos criada pelo método `GroupBy`. A lista é efetivamente avaliada quando o método é chamado.
    
4. **O método `Add` adicionará um novo reciclável apenas se ele contiver um espaço e a segunda palavra tiver mais de 3 caracteres.**
    
    ✅ Correto. O método `Add` verifica se a string contém pelo menos dois elementos após o split e se a segunda palavra (elemento do split) tem mais de 3 caracteres antes de adicionar o reciclável à lista.
    
5. **Um dos grupos retornados por `SortRecyclables` terá "plastic" como sua chave e conterá "plastic toy".**
    
    ❌ Incorreto. O grupo com a chave "plastic" deve incluir "plastic toy" e "plastic button". Ambos os recicláveis têm "plastic" como a primeira palavra.
    

---

## **Herança**

Uma classe herda uma classe base e substitui um método dessa classe base. Selecione todas as formas possíveis da classe base e do seu método:

- A classe base pode ser `sealed` em C# (ou `NotInheritable` em Visual Basic). ❌
- A classe base pode ser `abstract` em C# (ou `MustInherit` em Visual Basic). ✅
- O método da classe base pode ser `abstract` em C# (ou `MustOverride` em Visual Basic).  ✅
- O método da classe base pode ser `virtual` em C# (ou `Overridable` em Visual Basic). ✅
- O método da classe base não precisa ter nenhum modificador. ❌
- O método da classe base pode ter apenas um modificador `protected`. ❌
- O método na classe que substitui deve ter o modificador `override` (ou `Overrides` em Visual Basic). ✅

### Explicações das Respostas

1. **A classe base pode ser `sealed` em C# (ou `NotInheritable` em Visual Basic).**
    
    ❌ **Incorreto.** Uma classe marcada como `sealed` em C# ou `NotInheritable` em Visual Basic não pode ser herdada. Portanto, se você deseja que uma classe base seja herdada e seus métodos sejam substituídos, ela não pode ser `sealed` ou `NotInheritable`.
    
2. **A classe base pode ser `abstract` em C# (ou `MustInherit` em Visual Basic).**
    
    ✅ **Correto.** Uma classe base pode ser `abstract` (C#) ou `MustInherit` (Visual Basic). Isso significa que a classe não pode ser instanciada diretamente e pode conter métodos `abstract` que devem ser implementados pelas classes derivadas.
    
3. **O método da classe base pode ser `abstract` em C# (ou `MustOverride` em Visual Basic).**
    
    ✅ **Correto.** Métodos `abstract` (C#) ou `MustOverride` (Visual Basic) em uma classe base não têm implementação e devem ser obrigatoriamente substituídos nas classes derivadas. Eles servem como um contrato que as classes derivadas devem cumprir.
    
4. **O método da classe base pode ser `virtual` em C# (ou `Overridable` em Visual Basic).**
    
    ✅ **Correto.** Métodos `virtual` (C#) ou `Overridable` (Visual Basic) em uma classe base têm uma implementação padrão que pode ser substituída nas classes derivadas. Isso permite que as classes derivadas forneçam uma implementação específica do método, se desejado.
    
5. **O método da classe base não precisa ter nenhum modificador.**
    
    ❌ **Incorreto.** Para que um método da classe base seja substituído, ele precisa ter um modificador que permita a substituição, como `virtual`, `abstract`, ou `protected` (junto com `virtual` ou `abstract`). Um método sem modificador não é garantido para ser substituído e não pode ser acessado diretamente pelas classes derivadas.
    
6. **O método da classe base pode ter apenas um modificador `protected`.**
    
    ❌ **Incorreto.** Um método com apenas o modificador `protected` não pode ser substituído diretamente se não for também `virtual` ou `abstract`. `Protected` só controla o acesso ao método, mas não permite substituição sem um modificador adicional.
    
7. **O método na classe que substitui deve ter o modificador `override` (ou `Overrides` em Visual Basic).**
    
    ✅ **Correto.** Na classe derivada, para substituir um método da classe base, o método deve ser marcado com `override` (C#) ou `Overrides` (Visual Basic). Isso indica que o método está substituindo uma implementação da classe base.
    

---

## **Inteiro**

Quais afirmações são verdadeiras para o tipo de dado `int/Integer` integrado no .NET?
(Selecione todas as respostas aceitáveis.)

- Suporta operadores bitwise. ✅
- O método `ToString` pode ser usado para formatar um valor numérico. ✅
- A expressão `a/b` retornará infinito se `a` tiver valor 1 e `b` tiver valor 0. ❌
- É não assinado por padrão e não suporta valores negativos. ❌

### Explicações das Respostas

1. **Suporta operadores bitwise.**
    
    ✅ **Correto.** O tipo `int` (ou `Integer` em Visual Basic) suporta operadores bitwise como AND (`&`), OR (`|`), XOR (`^`), NOT (`~`), e shift left (`<<`) e shift right (`>>`). Estes operadores podem ser usados para manipulação direta dos bits do valor inteiro.
    
2. **O método `ToString` pode ser usado para formatar um valor numérico.**
    
    ✅ **Correto.** O tipo `int` tem o método `ToString`, que pode ser usado para converter o valor inteiro em uma string. Além disso, você pode passar parâmetros para o método `ToString` para formatar o valor numérico de acordo com suas necessidades, como usando diferentes formatos numéricos ou especificando a cultura.
    
3. **A expressão `a/b` retornará infinito se `a` tiver valor 1 e `b` tiver valor 0.**
    
    ❌ **Incorreto.** No caso de uma divisão por zero com tipos de dados inteiros, como `int`, uma exceção é lançada (por exemplo, `DivideByZeroException` em C#). Ao contrário de tipos de ponto flutuante (como `float` ou `double`), que podem retornar "Infinity" ou "NaN" para divisões por zero, os tipos inteiros não têm conceito de infinito e resultam em um erro.
    
4. **É não assinado por padrão e não suporta valores negativos.**
    
    ❌ **Incorreto.** O tipo `int` é um tipo de dado com sinal por padrão, o que significa que ele pode representar tanto valores positivos quanto negativos. O tipo `uint` (unsigned int) é o tipo não assinado que não suporta valores negativos, mas o `int` é assinado e pode representar uma 
    

---

## **Herança de Caranguejo**

Considere o seguinte código:

**C#**

```csharp
public class Crab
{
    public virtual string PinchClaws()
    {
        return "clap clap";
    }
}

public class CoconutCrab : Crab
{
    public override string PinchClaws()
    {
        return "CLAP CLAP";
    }
}
```

[**VB.NET**](http://vb.net/)

```vbnet
Public Class Crab
    Public Overridable Function PinchClaws() As String
        Return "clap clap"
    End Function
End Class

Public Class CoconutCrab
    Inherits Crab
    Public Overrides Function PinchClaws() As String
        Return "CLAP CLAP"
    End Function
End Class
```

Selecione as afirmações que são corretas.

(Selecione todas as respostas aceitáveis.)

- Chamar `PinchClaws` em uma instância de `CoconutCrab` retornará "CLAP CLAP". ✅
- Chamar `PinchClaws` em uma instância de `Crab` retornará "CLAP CLAP". ❌
- Converter uma instância de `CoconutCrab` para `Crab` e depois chamar o método `PinchClaws` retornará "clap clap". ❌
- Converter uma instância de `Crab` para `CoconutCrab` lançará uma exceção. ✅

### Explicação:

1. **Chamar `PinchClaws` em uma instância de `CoconutCrab` retornará "CLAP CLAP".**
    
    ✅ **Correto.** O método `PinchClaws` foi substituído (`override`) na classe `CoconutCrab` para retornar "CLAP CLAP". Portanto, quando o método é chamado em uma instância de `CoconutCrab`, ele executa a versão sobrecarregada da classe `CoconutCrab`, retornando "CLAP CLAP".
    
2. **Chamar `PinchClaws` em uma instância de `Crab` retornará "CLAP CLAP".**
    
    ❌ **Incorreto.** A classe base `Crab` tem uma implementação do método `PinchClaws` que retorna "clap clap". Somente a instância da classe `CoconutCrab`, que substitui o método, retornará "CLAP CLAP". Uma instância da classe `Crab` chamará o método da classe base, retornando "clap clap".
    
3. **Converter uma instância de `CoconutCrab` para `Crab` e depois chamar o método `PinchClaws` retornará "clap clap".**
    
    ❌ **Incorreto.** Quando uma instância de `CoconutCrab` é convertida para `Crab`, o método `PinchClaws` ainda se refere à implementação sobrecarregada da classe `CoconutCrab`, pois a chamada ao método é polimórfica. Portanto, a chamada ao método `PinchClaws` retornará "CLAP CLAP", não "clap clap".
    
4. **Converter uma instância de `Crab` para `CoconutCrab` lançará uma exceção.**
    
    ✅ **Correto.** Tentar converter uma instância de `Crab` para `CoconutCrab` lançará uma exceção de tempo de execução (`InvalidCastException`), a menos que a instância seja realmente de tipo `CoconutCrab`. Isso ocorre porque `Crab` não é uma instância da classe `CoconutCrab`, e a conversão de tipos não relacionados diretamente resulta em uma exceção.
    

---

## Adicionar Tabela

O Entity Framework é usado em uma aplicação que gerencia estoques. A aplicação possui o seguinte diagrama de classes para o modelo e o contexto do banco de dados:

```vbnet
**Stock**
Classe
Propriedades
Id (get; set;): int
Name (get; set;): string
```

```vbnet
**StockMarketContext**
Classe
DbContext
Propriedades
Stocks (get; set;): DbSet<Stock>
```

Usando migração code-first, precisamos atualizar os modelos mostrados no seguinte diagrama de classes:

```vbnet
**Stock**
Classe
Propriedades
Id (get; set;): int
Name (get; set;): string
Prices (get; set;): List<Price>
```

```vbnet
**Price**
Classe
Propriedades
Id (get; set;): int
PriceValue (get; set;): float
```

```vbnet
**StockMarketContext**
Classe
DbContext
Propriedades
Stocks (get; set;): DbSet<Stock>
```

O que acontecerá ao executar as migrações necessárias usando o Console do Gerenciador de Pacotes?
(Selecione todas as respostas aceitáveis.) 

- O comando Add-Migration atualizará o banco de dados para a migração code-first dada. ❌
- A propriedade Id precisa ser anotada com o atributo Key para torná-la uma chave primária.  ❌
- Uma chave estrangeira será adicionada implicitamente à tabela Prices, já que a propriedade de navegação Prices é adicionada à tabela Stocks.  ✅
- O comando All-Migrations busca todas as migrações que foram aplicadas ao banco de dados de destino.  ❌
- O parâmetro TargetMigration pode ser usado com o comando Update-Database para reverter atualizações feitas a um banco de dados usando migrações do Entity Framework. ✅

1. **O comando Add-Migration atualizará o banco de dados para a migração code-first dada.**
    
    ❌ **Incorreto.** O comando `Add-Migration` não atualiza o banco de dados. Em vez disso, ele cria uma nova migração que descreve as alterações que precisam ser aplicadas ao banco de dados. Para atualizar o banco de dados com essas alterações, você deve usar o comando `Update-Database`.
    
2. **A propriedade Id precisa ser anotada com o atributo Key para torná-la uma chave primária.**
    
    ❌ **Incorreto.** No Entity Framework, a propriedade `Id` é considerada a chave primária por convenção, desde que siga a convenção de nomenclatura padrão (por exemplo, "Id" ou "<NomeDaClasse>Id"). Portanto, não é necessário anotar explicitamente a propriedade com o atributo `[Key]` a menos que você deseje usar um nome diferente ou se a convenção não se aplicar.
    
3. **Uma chave estrangeira será adicionada implicitamente à tabela Prices, já que a propriedade de navegação Prices é adicionada à tabela Stocks.**
    
    ✅ **Correto.** Ao adicionar uma propriedade de navegação (`Prices`) na classe `Stock` e uma classe associada (`Price`), o Entity Framework cria uma chave estrangeira implícita na tabela `Prices` que faz referência à tabela `Stocks`. Isso é feito automaticamente para manter o relacionamento entre as tabelas.
    
4. **O comando All-Migrations busca todas as migrações que foram aplicadas ao banco de dados de destino.**
    
    ❌ **Incorreto.** Não existe um comando chamado `All-Migrations` no Entity Framework. O comando usado para listar todas as migrações aplicadas é `Get-Migrations`, que exibe as migrações que foram aplicadas ou estão disponíveis no projeto.
    
5. **O parâmetro TargetMigration pode ser usado com o comando Update-Database para reverter atualizações feitas a um banco de dados usando migrações do Entity Framework.**
    
    ✅ **Correto.** O parâmetro `TargetMigration` no comando `Update-Database` pode ser utilizado para reverter o banco de dados para um estado anterior, aplicando migrações até o ponto especificado. Se você deseja desfazer ou reverter migrações, pode especificar a migração de destino para a qual o banco de dados deve ser atualizado.
    

---

## **Análise de XML**

Quais afirmações são verdadeiras para as tecnologias .NET que você pode usar para processar dados XML?

(Selecione todas as respostas aceitáveis.) 

- `System.Xml.XmlReader.Create(Stream stream)` constrói um modelo interno que armazena o arquivo XML inteiro. ❌
- `System.Xml.Linq.XElement` pode ser usado para modificar o arquivo XML existente. ✅
- Usar `System.Xml.Serialization.XmlSerializer` pode ser útil quando o fluxo XML é esperado para estar em conformidade com um esquema XML conhecido. ✅
- `System.Xml.Linq.XElement.Load(Stream stream)` constrói um modelo interno que armazena o arquivo XML inteiro.  ✅
- Executar `System.Xml.Linq.XElement.Load(Stream stream)` é mais rápido do que executar `System.Xml.XmlReader.Create(Stream stream)`.  ❌

1. **`System.Xml.XmlReader.Create(Stream stream)` constrói um modelo interno que armazena o arquivo XML inteiro.**
    
    ❌ **Incorreto.** O `XmlReader` é uma classe de leitura sequencial e eficiente para XML. Ela não constrói um modelo interno que armazena o arquivo XML inteiro, mas sim lê o XML de forma forward-only e não mantém o arquivo XML inteiro na memória. É ideal para ler grandes arquivos XML sem sobrecarregar a memória.
    
2. **`System.Xml.Linq.XElement` pode ser usado para modificar o arquivo XML existente.**
    
    ✅ **Correto.** A classe `XElement` do namespace `System.Xml.Linq` faz parte da API LINQ to XML e permite manipular, modificar e consultar o XML de maneira eficiente. Você pode adicionar, remover ou alterar elementos e atributos usando essa classe.
    
3. **Usar `System.Xml.Serialization.XmlSerializer` pode ser útil quando o fluxo XML é esperado para estar em conformidade com um esquema XML conhecido.**
    
    ✅ **Correto.** `XmlSerializer` é utilizado para serializar e desserializar objetos .NET para e a partir de XML. É útil quando você sabe que o XML está em conformidade com um esquema específico, pois o `XmlSerializer` mapeia o XML para as propriedades dos objetos com base nas convenções de serialização.
    
4. **`System.Xml.Linq.XElement.Load(Stream stream)` constrói um modelo interno que armazena o arquivo XML inteiro.**
    
    ✅ **Correto.** O método `XElement.Load(Stream stream)` carrega o XML do fluxo e constrói um modelo na memória que representa o documento XML inteiro. Isso permite consultar e modificar o XML com LINQ to XML.
    
5. **Executar `System.Xml.Linq.XElement.Load(Stream stream)` é mais rápido do que executar `System.Xml.XmlReader.Create(Stream stream)`.**
    
    ❌ **Incorreto.** `XElement.Load(Stream stream)` carrega o XML inteiro em memória, o que pode ser mais lento e consumir mais memória, especialmente para grandes arquivos XML. Em contraste, `XmlReader` é mais eficiente em termos de desempenho e uso de memória porque lê o XML de forma sequencial e não armazena o arquivo inteiro na memória. Portanto, `XmlReader` tende a ser mais rápido e menos exigente em termos de recursos para leitura de XML.
    

---
