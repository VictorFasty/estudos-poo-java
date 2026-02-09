### Programação Orientada a Objetos (POO): Do Conceito ao Spring Boot

Antes de mergulharmos no código, precisamos entender como a Programação Orientada a Objetos facilita a nossa vida. Mas, afinal, o que é POO?

De forma resumida, a POO surgiu como uma alternativa à programação estruturada para nos ajudar a lidar com sistemas complexos. Hoje, utilizamos POO em praticamente tudo: no Frontend, Backend, Ciência de Dados e muito mais.

O grande trunfo da POO é a **Abstração**: a capacidade de isolar apenas as características e comportamentos essenciais de um objeto para o nosso sistema. Além disso, ela nos permite proteger esses dados através do **Encapsulamento**, controlando como as informações são acessadas e alteradas, garantindo segurança e organização.

### Construtores, Getters e Setters

Para manipular esses objetos, usamos ferramentas específicas:

- **Construtores:** São a "porta de entrada" da classe. É por eles que criamos uma nova instância e definimos os dados iniciais.

```java
public class Condominio {
    private String casa;

    // Construtor: A "Porta de Entrada"
    public Condominio(String nomeDaCasa) {
        this.casa = nomeDaCasa; 
    }
}
```

- **Getters:** Servem para buscar uma variável na memória. É como pedir a chave de um condomínio para acessar sua casa; você acessa o dado, mas não o expõe diretamente.
- **Setters:** Servem para alterar (setar) dados, permitindo incluir validações antes de modificar a variável.

```java
public class Condominio {
    private String casa;

    public Condominio(String casa) {
        this.casa = casa;
    }

    // Getter: Pedindo a chave para buscar o valor
    public String getCasa() {
        return this.casa;
    }

    // Setter: Permissão para entrar e trocar o valor
    public void setCasa(String novaCasa) {
        this.casa = novaCasa;
    }
}
```

### Herança: Reutilização de Código

A Herança permite que uma classe "filha" herde atributos e métodos de uma classe "pai". O objetivo é o reuso. Imagine um sistema de imóveis: em vez de repetir "endereço" e "valor" em todas as classes, criamos uma classe mãe `Imovel`.

```java
public class Imovel {
    public String endereco;
    public double valor;
}

public class Casa extends Imovel {
    private boolean temQuintal; 
    // Casa já possui endereço e valor automaticamente via herança!
}
```

*Dica:* A classe filha só herda o que é `public` ou `protected`. Atributos `private` não são acessados diretamente pela subclasse.

### Polimorfismo: Muitas Formas

O Polimorfismo permite tratar objetos diferentes (Casa, Apartamento, Mansão) como um tipo comum (`Imovel`). Se todos possuem o método `calcularImposto()`, você pode disparar esse comando para uma lista mista de imóveis e cada um responderá com sua própria lógica.

Isso gera **Desacoplamento**: seu sistema de IPTU não precisa conhecer os detalhes de uma Casa, apenas que ela é um `Imovel`. No **Spring Boot**, vemos isso o tempo todo em Exceptions:

```java
catch (Exception e) { 
    // Captura qualquer erro (NullPointer, SQL, etc) pois todos são "formas" de Exception.
    System.out.println(e.getMessage()); 
}
```

### Abstração: Classes Abstratas e Interfaces

Para organizar essa hierarquia, usamos:

1. **Classes Abstratas:** Você não mora em um "Imóvel genérico". Assim, usamos `abstract class Imovel` para impedir que alguém crie um objeto `Imovel` puro, obrigando a criação de algo específico como uma `Casa`.
2. **Interfaces (Contratos):** Define o que um objeto **faz**. No Spring, o `UserRepository` é uma interface. Ela define que o sistema deve "Salvar" ou "Deletar", e o Spring assina esse contrato criando a implementação por baixo dos panos.

```java
public interface Financiavel {
    void processarFinanciamento(); // O contrato: "o que fazer"
}
```

### Conclusão

Entender POO é entender as engrenagens por trás do Java e do Spring. Quando você domina esses pilares, você para de apenas "escrever código" e passa a "desenhar soluções". Isso torna seu sistema escalável e fácil de manter, seja em um projeto acadêmico na faculdade ou em uma aplicação robusta de nível empresarial.
