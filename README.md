# DIO - Trilha Java Básico

[Visite o site da DIO](https://www.dio.me)

**Autor:** Gleyson Sampaio

---

## Controle de Fluxo - Desafio

Vamos exercitar todo o conteúdo apresentado no módulo de Controle de Fluxo codificando o seguinte cenário.

### Cenário

O sistema deverá receber dois parâmetros via terminal que representarão dois números inteiros. Com esses dois números, você deverá:

- Calcular a quantidade de interações necessárias (utilizando um laço `for`) e imprimir no console os números incrementados.
- **Exemplo:**  
  Se os números informados forem `12` e `30`, haverá `18` iterações, onde serão exibidas mensagens como:  
  - "Imprimindo o número 1"  
  - "Imprimindo o número 2"  
  - ... e assim por diante.

### Regras de Negócio

- **Validação:**  
  Se o primeiro parâmetro for **maior** que o segundo, o sistema deverá lançar uma exceção customizada chamada `ParametrosInvalidosException` com a mensagem:  
  > "O segundo parâmetro deve ser maior que o primeiro"

### Estrutura do Projeto

Crie o projeto **DesafioControleFluxo** e, dentro dele, as seguintes classes:

1. **Contador.java:**  
   Responsável por implementar a lógica do programa, ler os dados do terminal e realizar a contagem.
   
2. **ParametrosInvalidosException.java:**  
   Classe que representa a exceção de negócio a ser lançada caso a validação dos parâmetros falhe.

# Desafio concluído

### Exemplo de Código

A seguir, um trecho de código base que você poderá utilizar e ajustar conforme necessário:

```java
import java.util.Scanner;

public class Contador {
    public static void main(String[] args) {
        Scanner terminal = new Scanner(System.in);
        
        System.out.println("Digite o primeiro parâmetro");
        int parametroUm = terminal.nextInt(); // Utilize nextInt() para ler um inteiro
        
        System.out.println("Digite o segundo parâmetro");
        int parametroDois = terminal.nextInt(); // Utilize nextInt() para ler um inteiro
        
        try {
            // Chamando o método contendo a lógica de contagem
            contar(parametroUm, parametroDois);
        } catch (ParametrosInvalidosException e) { // Captura a exceção customizada
            // Exibe a mensagem de erro: "O segundo parâmetro deve ser maior que o primeiro"
            System.out.println(e.getMessage());
        }
    }
    
    static void contar(int parametroUm, int parametroDois) throws ParametrosInvalidosException {
        // Validação: se o primeiro parâmetro for maior que o segundo, lança a exceção
        if (parametroUm > parametroDois) {
            throw new ParametrosInvalidosException("O segundo parâmetro deve ser maior que o primeiro");
        }
        
        int contagem = parametroDois - parametroUm;
        
        // Realiza o laço de repetição para imprimir os números incrementados
        for (int i = 1; i <= contagem; i++) {
            System.out.println("Imprimindo o número " + i);
        }
    }
}
