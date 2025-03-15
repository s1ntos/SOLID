# Princípios SOLID

## 📌 Descrição
Este repositório contém explicações detalhadas e exemplos práticos dos princípios SOLID, um conjunto de diretrizes essenciais para o design de software orientado a objetos. Esses princípios ajudam a criar um código mais flexível, compreensível e fácil de manter.

## 🔍 O que é SOLID?
O SOLID é um acrônimo para cinco princípios:

1. **S**ingle Responsibility Principle (**Princípio da Responsabilidade Única**)
2. **O**pen/Closed Principle (**Princípio do Aberto/Fechado**)
3. **L**iskov Substitution Principle (**Princípio da Substituição de Liskov**)
4. **I**nterface Segregation Principle (**Princípio da Segregação de Interfaces**)
5. **D**ependency Inversion Principle (**Princípio da Inversão de Dependência**)

Cada princípio é detalhado abaixo com explicações e exemplos.

---

## 1️⃣ Single Responsibility Principle (SRP)
### 🔹 Princípio da Responsabilidade Única
**Uma classe deve ter apenas uma razão para mudar.**

### ✅ Exemplo Correto
```java
class Relatorio {
    public void gerarRelatorio() {
        // Gera o relatório
    }
}

class RelatorioExportador {
    public void exportarParaPDF(Relatorio relatorio) {
        // Exporta para PDF
    }
}
```

---

## 2️⃣ Open/Closed Principle (OCP)
### 🔹 Princípio do Aberto/Fechado
**Um módulo deve estar aberto para extensão, mas fechado para modificação.**

### ✅ Exemplo Correto
```java
interface Desconto {
    double aplicar(double preco);
}

class DescontoNatal implements Desconto {
    public double aplicar(double preco) {
        return preco * 0.9;
    }
}

class CalculadoraDePrecos {
    public double calcularPrecoComDesconto(double preco, Desconto desconto) {
        return desconto.aplicar(preco);
    }
}
```

---

## 3️⃣ Liskov Substitution Principle (LSP)
### 🔹 Princípio da Substituição de Liskov
**Uma subclasse deve ser substituível por sua classe base sem quebrar o sistema.**

### ❌ Exemplo Ruim
```java
class Pato {
    void nadar() {
        System.out.println("O pato está nadando");
    }
    
    void voar() {
        System.out.println("O pato está voando");
    }
}

class PatoDeBorracha extends Pato {
    @Override
    void voar() {
        throw new UnsupportedOperationException("Patos de borracha não voam!");
    }
}
```

---

## 4️⃣ Interface Segregation Principle (ISP)
### 🔹 Princípio da Segregação de Interfaces
**Uma classe não deve ser forçada a implementar métodos que não usa.**

### ✅ Exemplo Correto
```java
interface Trabalhador {
    void trabalhar();
    void baterPonto();
}

interface Programador {
    void programar();
}

class Caixa implements Trabalhador {
    public void trabalhar() {
        System.out.println("Atendendo clientes");
    }
    
    public void baterPonto() {
        System.out.println("Bateu ponto");
    }
}
```

---

## 5️⃣ Dependency Inversion Principle (DIP)
### 🔹 Princípio da Inversão de Dependência
**Dependa de abstrações, não de implementações concretas.**

### ✅ Exemplo Correto
```java
interface Database {
    void conectar();
}

class MySQLDatabase implements Database {
    public void conectar() {
        System.out.println("Conectando ao MySQL...");
    }
}

class Aplicacao {
    private Database banco;
    
    public Aplicacao(Database banco) {
        this.banco = banco;
    }
    
    void iniciar() {
        banco.conectar();
    }
}
```

---

## 📌 Conclusão
Os princípios SOLID ajudam a tornar o código **modular, reutilizável e fácil de manter**. Ao aplicá-los, garantimos um design de software mais robusto e flexível para futuras modificações.

📌 **Se gostou desse conteúdo, não esqueça de dar uma ⭐ no repositório!** 🚀
