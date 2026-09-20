# cadastro_de_produtos_com_menu.py

# menu dos produtos
menu = """
=== Menu ===
1- Cadastrar produtos
2- Listar produtos
3- Ver situação do estoque
4- Sair
"""

produtos = []  # lista que guarda as tuplas (nome, preco, quantidade)

while True:  # repete o menu até o usuário escolher sair
    print(menu)
    opcao = input("Escolha uma opção: ")  # pergunta a opção UMA vez só

    if opcao == '1':
        qtd_novos = int(input("Quantos produtos você irá cadastrar? "))

        for i in range(qtd_novos):
            print(f'\n--- Produto {i + 1} ---')
            nome = input('Nome: ')
            preco = float(input('Preço: '))
            quantidade = int(input('Quantidade em estoque: '))

            produtos.append((nome, preco, quantidade))

    elif opcao == '2':
        print(f"\nVocê tem {len(produtos)} produto(s) cadastrado(s):\n")
        for produto in produtos:
            nome = produto[0]
            preco = produto[1]
            quantidade = produto[2]
            print(f'{nome} - Preço: R${preco:.2f} - Quantidade: {quantidade}')

    elif opcao == '3':
        print("\n--- Situação do estoque ---\n")
        for produto in produtos:
            nome = produto[0]
            preco = produto[1]
            quantidade = produto[2]

            if quantidade == 0:
                situacao = "Sem estoque"
            elif quantidade > 0 and quantidade <= 10:
                situacao = 'Estoque baixo'
            elif quantidade > 10 and preco > 100:
                situacao = 'Estoque alto - produto caro'
            else:
                situacao = 'Estoque normal'

            print(f'{nome} - Situação: {situacao}')

    elif opcao == '4':
        print("Saindo...")
        break  # só o break termina o while

    else:
        print("Opção inválida! Tente novamente.")

