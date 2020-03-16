
#Linguagem de programação utilizada: Python

print("Programa da Transferência entre usuários")

opcao = 'a'
usuarios = [] #Variável que vai armazenar os usuarios
saldos = [] #Armazena os saldos
senhas = [] #Armazana as senhas
tam_l = 0
temporaria = 'temp' # variável que vai armazenar de forma temporários os dados
origem = 0
destino = 0
transf = 0

while opcao != '0':

    print("\nMenu:") #Meno do programa
    print(" 1 - Cadastrar usuário")
    print(" 2 - Imprimir saldos")
    print(" 3 - Transferir valores")
    print(" 0 - Sair do programa")
    opcao = input("\nDigite a opção: ")

    if opcao == '1': #Cadastrar usuários
        temporaria = input("Digite o nome do usuário:")
        usuarios.append(temporaria)
        temporaria = ''
        temporaria = input("Digite uma senha")
        while(temporaria == ''):
            print("Senha invalida")
            temporaria = input("Digite uma senha")
        senhas.append(temporaria)
        saldos.append(100)
        print("Usuário cadastrado com sucesso")
        #input("Pressione ENTER para continuar")

    if opcao == '2': #Imprimir a relação de usuários
        tam_l = len(usuarios)
        if(tam_l < 1):
            print("Não existe usuários cadastrados")
        else:
            print("Item:\t Usuário:\t Saldo")
            for i in range(0, tam_l):
                print(i+1,"\t\t", usuarios[i],"\t", saldos[i])
        #input("\nPressione ENTER para continuar")

    if opcao == '3': #Realizar transferências
        tam_l = len(usuarios)
        if (tam_l < 1):
            print("Não existe usuários cadastrados")
        else:
            print("Código:\t Usuário:")
            for i in range(0, tam_l):
                print(i + 1, "\t\t", usuarios[i])

            origem = int(input("\nEscolha o código do usuário que irá ENVIAR o valor"))

            while ((origem < 1) or (origem > tam_l)):
                print("Opção inválida")
                origem = int(input("\nEscolha o código do usuário que irá ENVIAR o valor"))
            temporaria = ''
            temporaria = input("Digite a senha")
            while (temporaria != senhas[origem-1]):
                print("Senha inválida")
                temporaria = input("Digite a senha")
            print("Usuário de envio = ",usuarios[origem-1], "\t","Saldo atual = ", saldos[origem-1])
            if (saldos[origem-1] == 0):
                print("Você não possui saldo")
            else:
                print("\nRelação de destinos:")
                for i in range(0, tam_l):
                    if(i != origem-1):
                        print(i+1,"\t\t", usuarios[i])

                destino = int(input("\nEscolha o código do usuario que irá RECEBER o valor"))
                while ((destino < 1) or (destino > tam_l) or (destino == origem)):
                    print("Opção inválida")
                    destino = int(input("\nEscolha o código do usuario que irá RECEBER o valor"))

                transf = int(input("Digite o valor a transferir"))
                while (transf > saldos[origem-1]):
                    print("Saldo insuficiente")
                    transf = int(input("Digite o valor a transferir"))

                saldos[origem-1] = (saldos[origem-1] - transf)
                saldos[destino-1] = (saldos[destino-1] + transf)
                print("Valor transferido com sucesso")

    if opcao == '0':
        print("O programa será encerrado")

print("Programa encerrado com sucesso")
