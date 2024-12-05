Conceito:
O Factory Method é um padrão de projeto criacional que fornece uma interface para criar objetos em uma classe base, mas permite que subclasses alterem o tipo de objetos que serão criados.
_____________________________________________________________________________________________________________________________

Problemas que resolve:
Imagine um sistema que precisa criar diferentes tipos de objetos, mas você não quer que o código do cliente dependa de classes concretas para evitar alto acoplamento.

_____________________________________________________________________________________________________________________________

Quando usar o padrão:
- Quando o código principal depende de muitos tipos concretos de objetos.
- Quando o tipo exato do objeto a ser criado não é conhecido até o momento da execução.
- Quando você deseja isolar o código que cria objetos de sua lógica de negócios.

_____________________________________________________________________________________________________________________________

UML:
Creator: Define o método abstrato factory() que as subclasses implementam.
ConcreteCreator: Subclasses concretas que os tipos de produtos.
Product: Interface ou classe base para os produtos criados.
ConcreteProduct: Implementações específicas da interface Product.

_____________________________________________________________________________________________________________________________

Código com comentários:

from _future_ import annotations
from abc import ABC, abstractmethod

_____________________________________________________________________________________________________________________________

class Creator(ABC):

    """
    Essa classe é responsável por definir a interface que contém um método concreto some_operation, 
    que utiliza o produto retornado pelo método abstrato factory.
    """
    
    def factory(self):
        """
        Será usado para criar objetos do tipo 'Product'.
        """
        pass

    def some_operation(self) -> str:
        """
        Método que demonstra o uso do produto retornado pelo método 'factory'.
        """

        # Cria o produto chamando o factory
        product = self.factory()

        # Usa o Produto.
        result = f"Criador: O mesmo código do criador acabou de funcionar com {product.operation()}"

        return result

class ConcreteCreator1(Creator):
    """
    Subclasse concreta de Creator.
    Implementa o método 'factory' para criar um produto específico ('ConcreteProduct1').
    """

    def factory(self) -> Product:
        return ConcreteProduct1()


class ConcreteCreator2(Creator):  
    """
    Mesma função da última class, criar um porduto específico.
    """

    def factory(self) -> Product:
        return ConcreteProduct2()


class Product(ABC):
    """
    Interface base para os produtos.
    """

    def operation(self) -> str:
        pass


class ConcreteProduct1(Product):
    """
    Implementação concreta de Product.
    Define o comportamento específico para o produto 1.
    """ 

    def operation(self) -> str:
        return

class ConcreteProduct2(Product):
    """
    Implementação concreta de Product.
    Define o comportamento específico para o produto 2.
    """ 

    def operation(self) -> str:
        return


def client_code(creator: Creator) -> None:
    """
    A função cliente utiliza o criador abstrato para realizar operações sem saber qual criador concreto está sendo utilizado.
    """

    print(f"Cliente: Não estou ciente da classe do criador, mas ainda funciona.\n"
          f"{creator.some_operation()}", end="")


if _name_ == "_main_":
    print("App: começa com ConcreteCreator1.")
    client_code(ConcreteCreator1())
    print("\n")

    print("App: começa com ConcreteCreator2.")
    client_code(ConcreteCreator2())

______________________________________________________________________________________________________________________________

Vantagens e Desvantagens:

Vantagens: 
- Você evita acoplamentos firmes entre o criador e os produtos concretos.
- Você pode introduzir novos tipos de produtos no programa sem quebrar o código cliente existente.

Desvantagens:
- O código pode se tornar mais complicado, pois você precisa introduzir muitas subclasses novas para implementar o padrão. 
