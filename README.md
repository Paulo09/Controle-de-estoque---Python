Para criar um controle de estoque simples, você pode usar um dicionário em Python para armazenar os itens e suas quantidades. Vou mostrar um exemplo de como implementar isso.

python
Copiar código
def controle_estoque():
    estoque = {}

    while True:
        comando = input("Digite um comando (adicionar/remover) ou 'sair' para encerrar: ").strip().lower()
        
        if comando == 'sair':
            break
        
        # Dividir o comando para obter a ação, o item e a quantidade
        partes = comando.split()
        if len(partes) < 3:
            print("Comando inválido. Use 'adicionar [item] [quantidade]' ou 'remover [item] [quantidade]'.")
            continue
        
        acao = partes[0]
        item = partes[1]
        try:
            quantidade = int(partes[2])
        except ValueError:
            print("Quantidade deve ser um número inteiro.")
            continue
        
        if acao == 'adicionar':
            if item in estoque:
                estoque[item] += quantidade
            else:
                estoque[item] = quantidade
            print(f"Adicionado {quantidade} de {item}. Estoque atual: {estoque[item]}.")

        elif acao == 'remover':
            if item in estoque:
                if estoque[item] >= quantidade:
                    estoque[item] -= quantidade
                    print(f"Removido {quantidade} de {item}. Estoque atual: {estoque[item]}.")
                else:
                    print(f"Quantidade a remover maior que a disponível. Estoque atual: {estoque[item]}.")
            else:
                print(f"Item {item} não encontrado no estoque.")
        else:
            print("Ação inválida. Use 'adicionar' ou 'remover'.")

    print("Controle de estoque finalizado.")
    print("Estoque final:", estoque)

# Executar o controle de estoque
controle_estoque()
Explicação do Código:
Dicionário estoque: Armazena os itens e suas quantidades.
Loop Infinito: Permite que o usuário continue inserindo comandos até digitar "sair".
Entrada de Comando: O usuário insere um comando que é dividido em partes para obter a ação (adicionar/remover), o nome do item e a quantidade.
Adição e Remoção: A quantidade é ajustada conforme o comando. Se o item não existe ou a quantidade a ser removida é maior do que a disponível, mensagens apropriadas são exibidas.
Finalização: Ao sair, o estoque final é exibido.
