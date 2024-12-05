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
