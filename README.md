# Padrão Proxy

## Conceito
O padrão Proxy fornece um substituto ou marcador para controlar o acesso a outro objeto. Ele é usado para adicionar uma camada de controle entre o cliente e o recurso.

## Problema que Resolve
- Reduz o custo de acessar objetos caros, como imagens ou conexões de rede.
- Protege recursos sensíveis de acessos não autorizados.
- Permite realizar operações adicionais antes ou depois do acesso ao recurso.

## Quando Usar
- Quando o custo de criação ou inicialização do objeto é alto.
- Para controlar o acesso a recursos sensíveis.
- Para encapsular operações adicionais relacionadas ao acesso do cliente ao objeto.

## Diagrama UML
![proxy-diagram](https://github.com/user-attachments/assets/bc840ccd-a441-4c73-a44b-2579a1d607d3)


## Exemplo de Código
from abc import ABC, abstractmethod

# Interface Comum: Define os métodos que o Proxy e o Objeto Real devem implementar.
class Image(ABC):
    @abstractmethod
    def display(self):
        pass

# Objeto Real: Contém a lógica principal, como carregar e exibir a imagem.
class RealImage(Image):
    def __init__(self, filename):
        self.filename = filename
        self.load_from_disk()  # Simula o carregamento do recurso.

    def load_from_disk(self):
        print(f"Carregando imagem {self.filename} do disco...")

    def display(self):
        print(f"Exibindo imagem {self.filename}")

# Proxy: Controla o acesso ao Objeto Real, carregando-o somente quando necessário.
class ImageProxy(Image):
    def __init__(self, filename):
        self.filename = filename
        self.real_image = None  # O objeto real só será inicializado sob demanda.

    def display(self):
        # Lazy loading: O Objeto Real só é criado no primeiro uso.
        if self.real_image is None:
            print(f"Inicializando o proxy para carregar a imagem {self.filename}.")
            self.real_image = RealImage(self.filename)
        self.real_image.display()

# Uso do padrão Proxy
if __name__ == "__main__":
    # Criando o proxy, mas sem carregar a imagem do disco.
    image = ImageProxy("foto.jpg")
    print("Imagem criada, mas ainda não carregada do disco.")

    # A imagem será carregada e exibida na primeira chamada ao método display.
    image.display()

    # Na segunda chamada, a imagem já está carregada, então o proxy apenas delega.
    image.display()


## Vantagens
- Reduz o uso de recursos desnecessários.
- Fornece controle adicional sobre o acesso aos objetos.
- Promove a separação de responsabilidades.

## Desvantagens
- Pode adicionar complexidade ao sistema.
- Introduz uma camada adicional de indireção.


