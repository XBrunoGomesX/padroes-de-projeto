# padroes-de-projeto 

## Conceito do Adapter 
O principal objetivo de um adapter é atuar como uma ponte ou intermediário para conectar sistemas, dispositivos ou conceitos que não são compatíveis diretamente

### Código exemplo
```
// Digamos que você tenha duas classes com interfaces
// compatíveis: RoundHole (Buraco Redondo) e RoundPeg (Pino
// Redondo).
class RoundHole is
    constructor RoundHole(radius) { ... }

    method getRadius() is
        // Retorna o raio do buraco.

    method fits(peg: RoundPeg) is
        return this.getRadius() >= peg.getRadius()

class RoundPeg is
    constructor RoundPeg(radius) { ... }

    method getRadius() is
        // Retorna o raio do pino.


// Mas tem uma classe incompatível: SquarePeg (Pino Quadrado).
class SquarePeg is
    constructor SquarePeg(width) { ... }

    method getWidth() is
        // Retorna a largura do pino quadrado.


// Uma classe adaptadora permite que você encaixe pinos
// quadrados em buracos redondos. Ela estende a classe RoundPeg
// para permitir que objetos do adaptador ajam como pinos
// redondos.
class SquarePegAdapter extends RoundPeg is
    // Na verdade, o adaptador contém uma instância da classe
    // SquarePeg.
    private field peg: SquarePeg

    constructor SquarePegAdapter(peg: SquarePeg) is
        this.peg = peg

    method getRadius() is
        // O adaptador finge que é um pino redondo com um raio
        // que encaixaria o pino quadrado que o adaptador está
        // envolvendo.
        return peg.getWidth() * Math.sqrt(2) / 2
```

## Problema que ele resolve
1 - **Incompatibilidade de interfaces**

O adapter permite que duas partes com interfaces diferentes (métodos, conectores ou formatos) possam interagir sem que nenhuma delas precise ser alterada.

2 - **Reutilização de código ou componentes**

Ao invés de reescrever ou modificar sistemas existentes, o adapter adapta a interface ou funcionalidade de um componente para torná-lo compatível com novos requisitos.

3 - **Redução de dependências diretas**

Sem o adapter, seria necessário alterar as classes ou dispositivos diretamente, criando dependências rígidas. Isso tornaria o sistema menos flexível e mais difícil de manter.

## Quando deve ser usado?

Deve ser usado quando você precisa resolver problemas de incompatibilidade entre diferentes interfaces, formatos ou sistemas, e deseja fazê-lo de forma não intrusiva e reutilizável.

## Diagrama UML

![Diagrama UML:](https://github.com/user-attachments/assets/3f97469a-b4aa-4cb4-90a1-7de2d70c638f)

## Vantagens e Desvantagens

### Vantagens
- Princípio de responsabilidade única. Você pode separar a conversão de interface ou de dados da lógica primária do negócio do programa.
- Princípio aberto/fechado. Você pode introduzir novos tipos de adaptadores no programa sem quebrar o código cliente existente, desde que eles trabalhem com os adaptadores através da interface cliente.
- Aumenta a flexibilidade: È possível alterar ou substituir componentes no futuro com impacto mínimo, já que o código principal permanece desacoplado de implementações específicas.

### Desvantagens
- A complexidade geral do código aumenta porque você precisa introduzir um conjunto de novas interfaces e classes. Algumas vezes é mais simples mudar a classe serviço para que ela se adeque com o resto do seu código.
- Overhead de desempenho: O processo de adaptação pode introduzir algum overhead de tempo de execução, principalmente em cenários de alta frequência de chamadas.
- Manutenção adicional: O adapter se torna um ponto de falha ou complexidade adicional, exigindo manutenção sempre que a interface original ou o sistema adaptado for alterado.
