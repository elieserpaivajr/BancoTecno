#Linguagem de programa��o utilizada: Python

print("Programa da Transfer�ncia entre usu�rios")

opcao = 'a'
usuarios = [] #Vari�vel que vai armazenar os usuarios
saldos = [] #Armazena os saldos
senhas = [] #Armazana as senhas
tam_l = 0
temporaria = 'temp' # vari�vel que vai armazenar de forma tempor�rios os dados
origem = 0
destino = 0
transf = 0

while opcao != '0':

    print("\nMenu:") #Meno do programa
    print(" 1 - Cadastrar usu�rio")
    print(" 2 - Imprimir saldos")
    print(" 3 - Transferir valores")
    print(" 0 - Sair do programa")
    opcao = input("\nDigite a op��o: ")

    if opcao == '1': #Cadastrar usu�rios
        temporaria = input("Digite o nome do usu�rio:")
        usuarios.append(temporaria)
        temporaria = ''
        temporaria = input("Digite uma senha")
        while(temporaria == ''):
            print("Senha invalida")
            temporaria = input("Digite uma senha")
        senhas.append(temporaria)
        saldos.append(100)
        print("Usu�rio cadastrado com sucesso")
        #input("Pressione ENTER para continuar")

    if opcao == '2': #Imprimir a rela��o de usu�rios
        tam_l = len(usuarios)
        if(tam_l < 1):
            print("N�o existe usu�rios cadastrados")
        else:
            print("Item:\t Usu�rio:\t Saldo")
            for i in range(0, tam_l):
                print(i+1,"\t\t", usuarios[i],"\t", saldos[i])
        #input("\nPressione ENTER para continuar")

    if opcao == '3': #Realizar transfer�ncias
        tam_l = len(usuarios)
        if (tam_l < 1):
            print("N�o existe usu�rios cadastrados")
        else:
            print("C�digo:\t Usu�rio:")
            for i in range(0, tam_l):
                print(i + 1, "\t\t", usuarios[i])

            origem = int(input("\nEscolha o c�digo do usu�rio que ir� ENVIAR o valor"))

            while ((origem < 1) or (origem > tam_l)):
                print("Op��o inv�lida")
                origem = int(input("\nEscolha o c�digo do usu�rio que ir� ENVIAR o valor"))
            temporaria = ''
            temporaria = input("Digite a senha")
            while (temporaria != senhas[origem-1]):
                print("Senha inv�lida")
                temporaria = input("Digite a senha")
            print("Usu�rio de envio = ",usuarios[origem-1], "\t","Saldo atual = ", saldos[origem-1])
            if (saldos[origem-1] == 0):
                print("Voc� n�o possui saldo")
            else:
                print("\nRela��o de destinos:")
                for i in range(0, tam_l):
                    if(i != origem-1):
                        print(i+1,"\t\t", usuarios[i])

                destino = int(input("\nEscolha o c�digo do usuario que ir� RECEBER o valor"))
                while ((destino < 1) or (destino > tam_l) or (destino == origem)):
                    print("Op��o inv�lida")
                    destino = int(input("\nEscolha o c�digo do usuario que ir� RECEBER o valor"))

                transf = int(input("Digite o valor a transferir"))
                while (transf > saldos[origem-1]):
                    print("Saldo insuficiente")
                    transf = int(input("Digite o valor a transferir"))

                saldos[origem-1] = (saldos[origem-1] - transf)
                saldos[destino-1] = (saldos[destino-1] + transf)
                print("Valor transferido com sucesso")

    if opcao == '0':
        print("O programa ser� encerrado")

print("Programa encerrado com sucesso")
