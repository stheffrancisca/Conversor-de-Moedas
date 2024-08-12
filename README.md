# Conversor-de-Moedas
Conversor de Moedas

- Parte 1: Crie um conversor de moedas que pergunte para o usuário qual moeda ele quer converter e para qual moeda destino ele quer converter. Caso alguma das moedas não estejam na lista de conversão, o usuário deve ser informado que essa conversão não é possível. Sendo possível a conversão, o seu conversor de moedas deve em seguida pedir o valor da moeda de origem que ele quer converter para a moeda de destino, fazer a conversão e exibir para o usuário o valor convertido.
- Parte 2: Adapte o seu código (crie uma cópia para manter os 2 códigos prontos) para o usuário não precisar dizer qual a moeda original, mas que permita inserir um valor para fazer a conversão com o indicativo da moeda, ex: R$50, US$20 e o sistema fazer a conversão automaticamente.

- dic_conversoes = {
    "R$-US$": 0.194,
    "US$-R$": 5.15,
    "R$-BTC":  0.000002857,
    "BTC-R$": 350000,
    "BTC-US$": 67961.16,
    "US$-BTC": 0.000014714

}  


# Parte 1
moedas = []
for par_moeda in dic_conversoes.keys():
    moeda_origem, moeda_destino = par_moeda.split("-")
    if moeda_origem not in moedas:
        moedas.append(moeda_origem)
texto_moedas = ",".join(moedas)
moeda_origem_usuario = input(f"Qual a moeda de origem para a conversão? ({texto_moedas})")

if moeda_origem_usuario in moedas:
    moeda_destino_usuario = input(f"Qual a moeda destino para a conversão? ({texto_moedas})")
    if moeda_destino_usuario not in moedas:
        print("Moeda inválida")
    else:
        if moeda_destino_usuario == moeda_origem_usuario:
            conversao = 1
        else:
            chave_dic = f"{moeda_origem_usuario}-{moeda_destino_usuario}"
            conversao = dic_conversoes[chave_dic]
        print(f"Conversão: {moeda_origem_usuario}1 = {moeda_destino_usuario}{conversao}")
else:
    print("Moeda inválida")

    # Parte 2
moedas = []
for par_moeda in dic_conversoes.keys():
    moeda_origem, moeda_destino = par_moeda.split("-")
    if moeda_origem not in moedas:
        moedas.append(moeda_origem)
texto_moedas = ",".join(moedas)

valor_original = input("Insira o valor a converter")

moeda_origem_usuario = ""
for moeda in moedas:
    if moeda in valor_original:
        moeda_origem_usuario = moeda
        valor = float(valor_original.replace(moeda, ""))

if moeda_origem_usuario != "":
    moeda_destino_usuario = input(f"Qual a moeda destino para a conversão? ({texto_moedas})")
    if moeda_destino_usuario not in moedas:
        print("Moeda inválida")
    else:
        if moeda_destino_usuario == moeda_origem_usuario:
            conversao = 1
        else:
            chave_dic = f"{moeda_origem_usuario}-{moeda_destino_usuario}"
            conversao = dic_conversoes[chave_dic]
        valor_convertido = valor * conversao
        print(f"Conversão: {moeda_origem_usuario}{valor} = {moeda_destino_usuario}{valor_convertido}")
else:
    print("Moeda inválida")
