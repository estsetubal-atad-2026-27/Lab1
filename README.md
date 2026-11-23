# ATAD 2026/27 · Laboratório 1 — Do enunciado ao programa em Java

| | |
|---|---|
| **Unidade curricular** | Algoritmos e Tipos Abstratos de Dados |
| **Semana** | 2 |
| **Duração** | 1 h 45 min |
| **Meio** | IntelliJ IDEA, JDK 21 (ou o disponível na sala) |
| **Conteúdo de suporte** | Tópicos 1–4 (semana 1): algoritmo, representação, tradução para Java, corretude informal |
| **Trabalho** | Individual ou em grupo de 2 (à escolha dos estudantes) |

---

## 1. Objetivos

No final deste laboratório deves ser capaz de:

1. Criar e executar um projeto Java no IntelliJ IDEA;
2. Fixar as ambiguidades de um enunciado em linguagem natural, escrevendo a **pré-condição** e a **pós-condição**;
3. Escrever **pseudo-código** com `input`, `output` e passos elementares;
4. Traduzir pseudo-código para **métodos Java**, preservando a estrutura;
5. **Verificar** um método com tabela de traço e casos de teste, registando o resultado esperado e o obtido.

---

## 2. O que é fornecido

**Nada.** Este laboratório não tem código inicial: o projeto é criado de raiz.

>  [!NOTE] 
> A verificação é feita por **casos de teste escritos por ti** e executados a partir do `main` — é exatamente o que fizemos na aula teórica.

---

## 3. Plano da sessão

| Parte | Tarefa                                                                         | Tempo  |
| :---: | ------------------------------------------------------------------------------ | :----: |
|   1   | Criar o projeto no IntelliJ e executar um `main` vazio                         | 10 min |
|   2   | Formalizar o primeiro problema: ambiguidades, pré/pós-condição e pseudo-código | 20 min |
|   3   | Traduzir três algoritmos para Java                                             | 40 min |
|   4   | Verificar: tabela de traço e casos de teste                                    | 25 min |
|   5   | Fecho: checklist e extensão                                                    | 10 min |

---

## 4. Parte 1 — Criar o projeto (10 min)

1. `File` → `New` → `Project…`;
2. Escolhe `Java` no lado direito do *wizard*.
3. Configurações (segue esta ordem):
  - **Location**: (cria/escolhe uma pasta para os projetos de ATAD) 
  - **Name**: `atad-lab1`
  - **Build System**: `Maven`
  - **JDK**: Qualquer existente `>= 21`;
  - `Add sample code` desabilitado -> Sem código inicial.  
  - Advanced Settings:
    - **Group**: `pt.unips.atad`
    - **Artifact Id**: `atad-lab1`
4. Cria a classe `Main` em `src/main/java` e substitui o conteúdo por:

```java
public class Main {

    public static void main(String[] args) {
        System.out.println("Projeto criado.");
    }
}
```

5. Executa com o triângulo verde ao lado de `main` e confirma que aparece `Projeto criado.` na consola.


---

## 5. Parte 2 — Do enunciado ao pseudo-código (20 min)

### 5.1. O enunciado

> «Escreve um programa que calcule a soma de todos os números inteiros entre dois valores introduzidos pelo utilizador.»

Este enunciado é **ambíguo**. Antes de escrever código, cria na raiz do projeto um ficheiro `notas.md` e resolve as ambiguidades.

### 5.2. Fixar o problema

Preenche a tabela com as decisões que tomaste:

| Questão                                                     | Decisão |
| ----------------------------------------------------------- | ------- |
| «Entre» inclui os extremos?                                 |         |
| O que fazer se o primeiro valor for maior do que o segundo? |         |
| Os valores podem ser negativos?                             |         |
| O que é escrito no ecrã?                                    |         |
| E se os dois valores forem iguais?                          |         |

### 5.3. Pré e pós-condição

Escreve, em `notas.md`:

- **Pré-condição:** o que tem de ser verdade sobre os dados à entrada;
- **Pós-condição:** o que se promete sobre o resultado.

Para este problema, a pré-condição depende da decisão que tomaste sobre a ordem dos valores. Se decidires que o algoritmo só é chamado com `a <= b`, a pré-condição fica `a <= b`; se decidires aceitar qualquer ordem, o algoritmo tem de tratar o caso `a > b`.

### 5.4. Pseudo-código

Escreve o algoritmo em `notas.md`, com `input`, `output` e `BEGIN`/`END`, usando o dialeto da aula.

```pascal
Algorithm somarIntervalo
    input:  a - integer
            b - integer
    output: s - integer

BEGIN
    <as tuas instruções>

    RETURN s
END
```

---

## 6. Parte 3 — Traduzir para Java (40 min)

Implementa **três** métodos na classe `Main`. Mantém o `main` como ponto de entrada e chama os métodos a partir dele.

> [!IMPORTANT]
> Documenta cada método traduzido com *Javadoc*, incluindo as respetivas pré/pós-condições — vê as **convenções na secção 11** e o exemplo fornecido.

### 6.1. `somarIntervalo`

Traduz **o teu** pseudo-código da Parte 2.

```java
/*
 * ...
 */
static long somarIntervalo(int inicio, int fim) {
    // a completar
}
```

### 6.2. `contarDigitos`

Traduz o pseudo-código seguinte. O caso `n = 0` está tratado à parte — pensa porquê antes de traduzir.

```pascal
Algorithm contarDigitos
    input:  n - integer (n >= 0)
    output: d - natural

BEGIN
    IF n = 0 THEN
        RETURN 1
    END IF

    x <- n
    d <- 0
    WHILE x > 0 DO
        x <- x / 10
        d <- d + 1
    END WHILE
    RETURN d
END
```

```java
/*
 * ...
 */
public static int contarDigitos(int n) {
    // a completar
}
```

<small>

:warning: `x / 10` em Java, com `x` inteiro, é **divisão inteira**. É isso que queremos aqui: descartar o último dígito.

</small>

### 6.3. `maiorDiferenca`

Traduz o pseudo-código seguinte. Repara nas **duas** variáveis acumuladoras e na forma como são inicializadas.

```pascal
Algorithm maiorDiferenca
    input:  a - array of integers
            n - natural (n > 0)
    output: d - integer

BEGIN
    maior <- a[0]
    menor <- a[0]
    i <- 1
    WHILE i < n DO
        IF a[i] > maior THEN
            maior <- a[i]
        END IF
        IF a[i] < menor THEN
            menor <- a[i]
        END IF
        i <- i + 1
    END WHILE
    RETURN maior - menor
END
```

```java
/*
 * ...
 */
public static int maiorDiferenca(int[] a) {
    // a completar
}
```

---

## 7. Parte 4 — Verificar (25 min)

### 7.1. Tabela de traço

Traça `contarDigitos(407)` em `notas.md`. Cada linha representa o estado **no início de uma verificação** do ciclo:

|  `x`  | `x > 0` |  `d`  |
| :---: | :-----: | :---: |
|  407  | verdade |   0   |
|   ?   |    ?    |   ?   |
|   ?   |    ?    |   ?   |
|   ?   |    ?    |   ?   |

### 7.2. Casos de teste

Calcula **à mão** o resultado esperado de cada chamada e só depois executa. Preenche a coluna «Obtido» com o que o programa imprimiu.

|   #   | Chamada                                 | Esperado | Obtido | Passa? |
| :---: | --------------------------------------- | :------: | :----: | :----: |
|   1   | `somarIntervalo(3, 6)`                  |          |        |        |
|   2   | `somarIntervalo(4, 4)`                  |          |        |        |
|   3   | `somarIntervalo(-2, 2)`                 |          |        |        |
|   4   | `contarDigitos(0)`                      |          |        |        |
|   5   | `contarDigitos(407)`                    |          |        |        |
|   6   | `contarDigitos(1000)`                   |          |        |        |
|   7   | `maiorDiferenca(new int[]{3, 9, 2})`    |          |        |        |
|   8   | `maiorDiferenca(new int[]{5})`          |          |        |        |
|   9   | `maiorDiferenca(new int[]{-5, -2, -9})` |          |        |        |

Usa chamadas deste tipo no `main`, para que o resultado esperado fique visível na consola:

```java
System.out.println("1) " + somarIntervalo(3, 6) + " (esperado: ??)");
```

<small>

:bulb: Os casos 4, 8 e 9 são **fronteira**: zero, um elemento e todos negativos. Se um deles falhar, o erro está provavelmente na inicialização de uma variável — e não no ciclo.

</small>

O caso 3 pressupõe que a tua pré-condição admite valores negativos. Se decidiste o contrário na Parte 2, substitui-o por outro caso **dentro do teu domínio** e regista a justificação. Um caso de teste que viola a pré-condição não testa nada.

**Se algum caso falhar:** não alteres o valor esperado. Localiza a instrução errada no pseudo-código primeiro e só depois corrige o Java.

---

## 8. Parte 5 — Fecho (10 min)

Antes de saíres, confirma:

- [ ] O projeto compila **sem erros** (`Build` → `Build Project`);
- [ ] Os nove casos de teste foram executados e estão registados em `notas.md`;
- [ ] Nenhum caso falha, ou a falha está identificada e justificada;
- [ ] O `notas.md` contém a tabela de decisões, a pré/pós-condição e o pseudo-código.

**Regras de implementação**

- Resolveste os problemas com **estruturas de controlo** (`if`, `while`, `for`), como nas aulas;
- Não usaste métodos que já resolvem o problema no seu lugar: `Math.max`, `Math.min`, `Math.abs`, `Integer.toString(...).length()`, etc.;
- Pensaste bem sobre as coisas e bloqueaste antes de "delegar" o teu raciocínio a GenAI.

---

## 9. Extensão (se terminares antes)

**a) Programa interativo.** Acrescenta um método `mainInterativo` (chamado a partir do `main`) que leia os dois valores com `Scanner` e imprima o resultado — ou substitui o corpo do `main` por esta versão:

```java
import java.util.Scanner;

// dentro de um método:
Scanner sc = new Scanner(System.in);
int a = sc.nextInt();
int b = sc.nextInt();
System.out.println(somarIntervalo(a, b));
```

Testa com valores válidos e com valores que **violam** a pré-condição. O que acontece?

**b) `ePrimo`.** Formaliza e implementa:

> «Escreve um método que diga se um número inteiro é primo.»

Antes de escrever código, responde em `notas.md`: qual é a pré-condição? Qual é o caso fronteira mais pequeno? É possível terminar o ciclo antes do fim? Como?

---

## 10. Erros comuns

| Erro | Onde aparece | Como detetar |
| --- | --- | --- |
| `=` em vez de `==` na condição | `if (a = b)` não compila | o compilador ajuda; lê a mensagem |
| `i <= n` em vez de `i < n` | ciclos sobre arrays | `ArrayIndexOutOfBoundsException` |
| Acumulador inicializado a `0` sem pensar | `maiorDiferenca` | caso 9 (todos negativos) |
| Divisão inteira inesperada | `contarDigitos` | caso 5 vs. caso 6 |
| `%` em vez de `/` para descartar o dígito | `contarDigitos` | ciclo infinito ou resultado absurdo |
| Alterar o valor esperado para «passar» | tabela de testes | o teste deixa de testar |

---

## 11. Convenções para Javadoc

O Javadoc padrão não possui etiquetas (*tags*) nativas como `@pre` ou `@post`, mas existem convenções bem estabelecidas na comunidade Java (incluindo as diretrizes oficiais da Oracle) sobre onde e como documentá-las:

### 11.1 Pré-condições

Devem ser distribuídas consoante a sua natureza:

* **Na tag `@param`:** Sempre que a pré-condição disser respeito a um parâmetro específico (ex.: limites numéricos, não ser nulo, ordem dos argumentos).
* **Na tag `@throws` (ou `@exception`):** Para indicar o que acontece caso uma pré-condição seja violada (ex.: `IllegalArgumentException`, `NullPointerException`).
* **Na descrição principal (corpo do comentário):** Quando a pré-condição envolve o estado interno do objeto (ex.: *"O ficheiro deve estar aberto antes de invocar este método"*) ou uma relação entre múltiplos parâmetros.

### 11.2 Pós-condições

* **Na tag `@return`:** Quando a pós-condição descreve exatamente o valor devolvido (ex.: *"a soma de todos os inteiros no intervalo $[a, b]$, inclusive"*).
* **Na descrição principal (corpo do comentário):** Quando o algoritmo tem **efeitos colaterais** (*side effects*), altera o estado do objeto, modifica uma estrutura passada por referência (como ordenar um *array*) ou escreve num ficheiro/consola.

### 11.3 Exemplo Prático

```java
/**
 * Calcula a soma de todos os números inteiros no intervalo fechado [inicio, fim].
 * 
 * <p><b>Pré-condição:</b> O intervalo deve ser válido, ou seja, {@code inicio <= fim}.
 * 
 * <p><b>Pós-condição:</b> O resultado corresponde à progressão aritmética exata entre os dois limites.</p>
 *
 * @param inicio o limite inferior do intervalo (inclusive); deve ser menor ou igual a {@code fim}
 * @param fim    o limite superior do intervalo (inclusive); deve ser maior ou igual a {@code inicio}
 * @return       a soma de todos os inteiros entre {@code inicio} e {@code fim}
 * @throws IllegalArgumentException se {@code inicio > fim}
 * @throws ArithmeticException      se o resultado ultrapassar a capacidade de {@code long}
 */
public long somarIntervalo(int inicio, int fim) {
    // ...
}

```

## 12. Referências

- Slides do bloco 1 (semana 1) — disponíveis no Moodle;
- Exercícios de aula da semana 1 — disponíveis no Moodle;
- Documentação Java: <https://docs.oracle.com/en/java/>;
- IntelliJ IDEA: <https://www.jetbrains.com/help/idea/getting-started.html>.
  

