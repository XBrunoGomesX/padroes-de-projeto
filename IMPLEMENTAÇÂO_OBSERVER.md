# Padrão de Design: Observer

## O Observer é um padrão de design comportamental que define um mecanismo de assinatura, 
## permitindo que múltiplos objetos sejam notificados sobre eventos ocorridos em um objeto observado.
## Quando o estado do objeto observado muda, todos os objetos que se inscreveram (observadores) são atualizados automaticamente.


interface Observer {
  update(data: any): void;
}

class Subject {
  private observers: Observer[] = [];

  subscribe(observer: Observer) {
    this.observers.push(observer);
  }

  unsubscribe(observer: Observer) {
    this.observers = this.observers.filter(obs => obs !== observer);
  }

  notify(data: any) {
    this.observers.forEach(observer => observer.update(data));
  }
}

// Concretizando os Observers
class ConcreteObserverA implements Observer {
  update(data: any) {
    console.log('Observer A recebeu:', data);
  }
}

class ConcreteObserverB implements Observer {
  update(data: any) {
    console.log('Observer B recebeu:', data);
  }
}

// Usando o Observer
const subject = new Subject();

const observerA = new ConcreteObserverA();
const observerB = new ConcreteObserverB();

subject.subscribe(observerA);
subject.subscribe(observerB);

subject.notify('Nova notificação!');

# Este código implementa o padrão de design Observer, que resolve os seguintes problemas:

## Comunicação desacoplada entre objetos:
  O padrão Observer resolve o problema da dependência direta entre o objeto que gera dados (chamado de Subject) e os objetos que consomem ou reagem a esses dados (os Observers). Sem o padrão, o Subject precisaria manter referências explícitas e depender diretamente dos observadores, o que tornaria o sistema mais rígido e difícil de manter. Com o Observer, o Subject mantém um conjunto de observers e pode notificá-los sem precisar saber detalhes sobre cada um.

## Notificação automática de mudanças para múltiplos objetos:
  O padrão permite que o Subject notifique automaticamente todos os seus observers sempre que houver uma mudança de estado. Isso é útil quando há múltiplos componentes do sistema que precisam ser atualizados com os mesmos dados sem a necessidade de fazer chamadas diretas entre eles. No código fornecido, os observers (como ConcreteObserverA e ConcreteObserverB) são atualizados automaticamente com o método notify() sempre que há uma mudança de dados.

## Flexibilidade para adicionar ou remover observers:
  O código resolve o problema de adicionar ou remover observadores de forma dinâmica, sem afetar a lógica central do Subject. Através dos métodos subscribe() e unsubscribe(), é possível adicionar ou remover observers conforme necessário, sem necessidade de modificar o código do Subject. Isso permite maior flexibilidade e modularidade no sistema.

## Facilidade de extensão:
  O padrão facilita a extensão do sistema com novos tipos de observers, sem precisar alterar o código do Subject. Novos observers podem ser adicionados com a simples implementação da interface Observer e a definição do comportamento no método update(). Isso torna o código mais fácil de manter e escalar conforme o sistema cresce.
