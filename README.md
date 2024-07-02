# Editor de Texto Simples em C#

Este é um projeto de um editor de texto simples desenvolvido em C#. Ele permite ao usuário criar, editar, abrir e salvar arquivos de texto no formato `.txt`.

## Funcionalidades

- Abrir um arquivo existente
- Criar um novo arquivo de texto
- Editar e salvar o conteúdo do arquivo
- Sair do editor

## Como usar

1. Clone este repositório:
    ```bash
    git clone https://github.com/DFGTX360/TextEditor.git
    ```
2. Abra o projeto em seu IDE de C# preferido (como Visual Studio ou Visual Studio Code).
3. Compile e execute o projeto.
4. Siga as instruções no console para abrir um arquivo existente, criar um novo arquivo, editar e salvar o conteúdo do arquivo.

## Estrutura do Código

O código está estruturado em métodos que permitem ao usuário interagir com o editor de texto, incluindo funções para abrir, editar e salvar arquivos.

### Funcionalidades Implementadas

- `Menu`: Exibe um menu com opções para abrir arquivo, criar novo arquivo ou sair do editor.
- `Abrir`: Permite ao usuário inserir o caminho de um arquivo existente e exibe seu conteúdo no console.
- `Editar`: Permite ao usuário digitar texto para editar e salvar em um arquivo.
- `Salvar`: Salva o texto editado em um arquivo especificado


Depois de selecionar uma opção, o programa guiará o usuário através do processo correspondente, permitindo abrir um arquivo existente, criar um novo arquivo, editar o texto e salvar as alterações.

## Código

Aqui está o código principal do projeto:

```csharp
internal class Program
{
    private static void Main(string[] args)
    {
        Menu();
    }

    static void Menu()
    {
        Console.Clear();
        Console.WriteLine("O que voce deseja fazer?");
        Console.WriteLine("1 - Abrir arquivo");
        Console.WriteLine("2 - Criar novo arquivo");
        Console.WriteLine("0 - Sair");
        short option = short.Parse(Console.ReadLine());

        switch (option)
        {
            case 0: Environment.Exit(0); break;
            case 1: Abrir(); break;
            case 2: Editar(); break;
            default: Menu(); break;
        }
    }

    static void Abrir()
    {
        Console.Clear();
        Console.WriteLine("Qual caminho do arquivo?");
        string path = Console.ReadLine();

        using (var file = new StreamReader(path))
        {
            string text = file.ReadToEnd();
            Console.WriteLine(text);
        }

        Console.WriteLine("");
        Console.ReadLine();
        Menu();
    }

    static void Editar()
    {
        Console.Clear();
        Console.WriteLine("Digite seu texto abaixo (ESC para sair)");
        Console.WriteLine("----------------");
        string text = "";

        do
        {
            text += Console.ReadLine();
            text += Environment.NewLine;
        } while (Console.ReadKey().Key != ConsoleKey.Escape);

        Salvar(text);
    }

    static void Salvar(string text)
    {
        Console.Clear();
        Console.WriteLine("Qual caminho para salvar o arquivo?");
        var path = Console.ReadLine();
        using (var file = new StreamWriter(path))
        {
            file.Write(text);
        }

        Console.WriteLine($"Arquivo {path} salvo com sucesso!");
        Console.ReadLine();
        Menu();
    }
}
Depois de selecionar uma opção, o programa guiará o usuário através do processo correspondente, permitindo abrir um arquivo existente, criar um novo arquivo, editar o texto e salvar as alterações.

Certifique-se de substituir `https://github.com/DFGTX360/TextEditor.git` pelo URL correto do seu repositório no GitHub. Isso fornecerá uma documentação completa e clara para os usuários que visitarem seu projeto no GitHub.
