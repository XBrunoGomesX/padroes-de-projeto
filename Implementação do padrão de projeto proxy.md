# Conceito do Padrão Proxy
- O padrão Proxy fornece um substituto ou controlador para outro objeto, permitindo que intercepte chamadas ao objeto real e, se necessário, modifique ou restrinja o acesso a ele.

# Problemas que ele resolve:
O padrão Proxy resolve problemas relacionados ao **controle, otimização ou abstração** do acesso a um objeto. Em geral, ele é útil quando o acesso direto ao objeto real não é adequado ou desejável.

### **Exemplo 1:**
- Você precisa limitar ou regular o acesso a um objeto, por exemplo, para aplicar restrições de segurança.

### **Solução**
- Um Proxy de Proteção pode verificar permissões de um usuário antes de permitir o acesso ao objeto real.

### **Exemplo 2**
- O objeto real é "pesado" de criar ou carregar, e nem sempre é necessário durante toda a execução do programa.

### **Solução**
- Um Proxy Virtual pode atrasar a criação ou carregamento do objeto real até que ele seja realmente necessário. Isso economiza recursos, como memória e tempo de processamento.


