Programação Orientada a Objetos (POO)
Antes de termos essa imersão com POO, precisamos entender como a Programação Orientada a Objetos facilita nossa vida. Mas afinal, o que é POO?

De forma bastante resumida, POO surgiu como uma alternativa à programação estruturada para nos ajudar a lidar com sistemas complexos. Hoje utilizamos POO em tudo no nosso dia a dia como programadores, seja no frontend, backend, ciência de dados, tudo mesmo no geral.

O grande trunfo da POO é a Abstração: a capacidade de isolar apenas as características e comportamentos essenciais de um objeto para o nosso sistema. Além disso, ela nos permite proteger esses dados através do Encapsulamento, controlando como as informações são acessadas e alteradas (geralmente através de construtores, getters e setters), garantindo muito mais segurança e organização ao projeto.

Viu que ali em cima citamos Construtores, Getters e Setters? Precisamos entender o que são eles também através de uma analogia simples: A Casa e seus Móveis.

Construtores: Geralmente é por ele que teremos acesso à nova classe. Imagine que o construtor é o momento de "construir" e entregar a casa. Observe o exemplo:

Java
public class Casa {
    private String moveis;

    public Casa(String moveis) {
        // O construtor define quais móveis a casa terá ao ser criada
        this.moveis = moveis;
    }
}
Os moveis seriam a nossa variável (o conteúdo), porém só com eles soltos não conseguimos ter organização ou proteção. Precisamos da Casa (a classe) para guardá-los e do Construtor para colocar tudo no lugar assim que entramos; esses são os construtores.

E o que são os Getters e Setters?

Getters: Servem para conseguirmos buscar essa variável na memória. Na lógica da casa: os móveis estão lá dentro, mas você não os vê da rua. Você precisa pedir a chave para entrar e buscar/ver o que tem lá dentro.

Setters: Servem para conseguirmos setar (definir ou alterar) dados. Usando a lógica da casa: você usa a chave para entrar e trocar um móvel antigo por um novo.

Java
public class Casa {
    private String moveis;

    public Casa(String moveis) {
        this.moveis = moveis;
    }

    public String getMoveis() {
        return this.moveis; // Getter: pegando a informação
    }

    public void setCasa(String novosMoveis) {
        this.moveis = novosMoveis; // Setter: alterando a informação
    }
}
Encapsulamento
O Encapsulamento serve, resumidamente, como uma blindagem para não expor nossos dados vindo do banco na aplicação. Se você expõe suas entidades (seus atributos) diretamente, qualquer parte do código pode chegar lá e alterar o valor de uma forma que quebre a lógica do seu sistema, ou seja, não teríamos uma aplicação segura.

Exemplo de encapsulamento: private String moveis;

Bom, com esses dados protegidos, não seria qualquer um que teria acesso. Precisaríamos dos getters, setters e construtores para que consigamos ter acesso, alterar os dados e pegar os dados. Ficaria mais ou menos assim:

Java
public class Cidade {
    // 1. O Atributo Privado (A "blindagem" ou Encapsulamento)
    private String casa;

    // 2. O Construtor (A "porta de entrada" para criar o objeto)
    public Cidade(String casa) {
        this.casa = casa;
    }

    // 3. O Getter (A "chave" para ler o valor)
    public String getCasa() {
        return this.casa;
    }

    // 4. O Setter (A "permissão" para alterar o valor)
    public void setCasa(String novaCasa) {
        // Aqui você poderia validar, ex: if (novaCasa != null)
        this.casa = novaCasa;
    }
}
Herança (Reutilização)
A Herança é o mecanismo que permite que uma classe (filha) herde todos os atributos e métodos de outra classe (pai). O principal objetivo aqui é o reuso de código. Imagine que você está construindo o sistema da sua Cidade. Você tem uma Casa e um Apartamento. Ambos têm: Endereço, Cor, Valor e Dono.

Em vez de escrever esse código duas vezes, você cria uma classe "mãe" chamada Imovel e faz a Casa e o Apartamento herdarem dela.

Java
public class Imovel {
    public String endereco;
    public double valor;

    public void exibirDetalhes() {
        System.out.println("Endereço: " + endereco);
    }
}

// Casa "é um" Imovel, então ela herda tudo dele
public class Casa extends Imovel {
    private boolean temQuintal; 
}
Polimorfismo
O Polimorfismo é o que nos permite tratar uma Casa, um Apartamento ou uma Mansão simplesmente como um Imóvel. Imagine que você tem uma lista de pagamentos de IPTU. Você não precisa saber se é casa ou prédio; você só precisa chamar o método calcularImposto() que existe em todos eles.

Polimorfismo no Spring Boot
No dia a dia com Java Spring, vemos o polimorfismo brilhar no @ExceptionHandler:

Java
@RestControllerAdvice
public class GerenciadorDeErros {
    @ExceptionHandler(Exception.class) // Captura QUALQUER erro que herde de Exception
    public ResponseEntity tratarErroGenerico(Exception e) {
        return ResponseEntity.status(500).body("Erro interno: " + e.getMessage());
    }
}
Abstração (Classes Abstratas e Interfaces)
1. Classes Abstratas: Faz sentido existir um Imóvel "puro" que não é nem casa nem apartamento? Provavelmente não. O Imóvel é apenas um conceito. Ao usar public abstract class Imovel, você impede que alguém instancie um imóvel genérico (new Imovel()), obrigando a criação de algo específico.

2. Interfaces (O Contrato): A interface é o que você mais utiliza no Java Spring. Ela é um contrato: quem assina o contrato (implementa a interface) é obrigado a cumprir o que está escrito. Se a Herança diz que um objeto É alguma coisa, a Interface diz que um objeto FAZ alguma coisa. O seu UserRepository é uma interface; ela define o que deve ser feito (salvar, deletar), mas o Spring é quem resolve o "como".

Conclusão: Entender POO é entender as engrenagens por trás do Java e do Spring. Quando você domina Encapsulamento, Herança, Polimorfismo e Abstração, você para de apenas 'escrever código' e passa a 'desenhar soluções'. Isso é o que torna seu sistema escalável e fácil de manter, seja em um projeto de faculdade ou em uma aplicação robusta de nível empresarial.
