# Como Contribuir

1 - **Faça um fork do repositório:**

Clique no botão "Fork" no canto superior direito da página do repositório.

2 - **Clone o repositório para sua máquina:**
```
   git clone https://github.com/seu-usuario/nome-do-projeto.git
```
3 - **Crie uma branch para suas alterações**: _Nomeie a branch de forma que esteja associada com a issue_
```
  git checkout -b minha-nova-funcionalidade
```
4 - **Faça suas alterações**:
- Certifique-se de seguir o guia de estilo de código.
- Adicione comentários ao código, quando necessário.

5 - **Adicione e commite suas alterações**: 
```
git add .
git commit -m "Descrição clara das alterações"
```
6 - **Envie suas alterações**:
```
git push origin minha-nova-funcionalidade
```
7 - **Abra um Pull Request**:
- Acesse o repositório original.
- Clique em "Pull Request".
- Preencha as informações do PR com uma descrição clara do que foi feito.

# Abrir Issue
- Verifique primeiro se a issue já existe.
- Forneça o máximo de detalhes por exemplo:
  - Qual é o problema ou sugestão?
  - Passos para reproduzir (se aplicável).
  - Logs, mensagens de erro ou capturas de tela relevantes.

# Requisitos para Pull Requests
- Teste suas alterações antes de enviar o PR.
- O nome do PR deve ser o que ele quer implementar por exemplo: "Implementação do padrão de projeto X"
- Certifique-se de que suas alterações não quebram funcionalidades existentes.
- Inclua testes para novas funcionalidades, se aplicável.

# Padrões de Estilo de Código
Siga estas convenções para manter o código consistente:
- O código sera em **Python**.
- Sempre use nomes de variáveis e funções em **inglês** e que faça sentido com o que ele faz por exemplo:

  _Obs: Comentarios podem ser em português_
  ```
   def calculate_sum():
    # Asks the user for two numbers, calculates their sum, and displays the result.
    # Ask the user for two numbers
    number1 = float(input("Enter the first number: "))
    number2 = float(input("Enter the second number: "))

    # Calculate the sum
    total = number1 + number2

    # Display the result
    print(f"The sum of {number1} and {number2} is {total}.")

  ```
  


   
