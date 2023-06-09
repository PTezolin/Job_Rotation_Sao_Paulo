# Job Rotation - São Paulo

# 2) Dado a sequência de Fibonacci
Onde se inicia por 0 e 1 e o próximo valor sempre será a soma dos 2 valores anteriores (exemplo: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34...), escreva um programa na linguagem que desejar onde, informado um número, ele calcule a sequência de Fibonacci e retorne uma mensagem avisando se o número informado pertence ou não a sequência.

IMPORTANTE: Esse número pode ser informado através de qualquer entrada de sua preferência ou pode ser previamente definido no código;

    print("-----------------------------------------------------------------")
    print("      Verificador de pertencimento à sequência de Fibonacci      ")
    print("-----------------------------------------------------------------")

    while True:
        num_str = input("Informe o número que você deseja verificar ou digite 0 para sair: ")

        if num_str == "0":
            print("Programa encerrado!\n")
            break

        try:
            num_float = float(num_str)
            num_int = int(num_float)
            if num_int != num_float:
                print("Valor inválido. O número deve ser um inteiro.\n")
                continue
        except ValueError:
            print("Valor inválido. O número deve ser um inteiro.\n")
            continue

        if num_int <= 0:
            print("Valor inválido. O número deve ser maior que zero.\n")
            continue

        fib1, fib2 = 0, 1
        while fib2 < num_int:
            fib1, fib2 = fib2, fib1 + fib2

        if fib2 == num_int:
            print(num_int, "pertence à sequência de Fibonacci\n")
        else:
            print(num_int, "não pertence à sequência de Fibonacci\n")

# 3) Faturamento diário de uma distribuidora 
Dado um vetor que guarda o valor de faturamento diário de uma distribuidora, faça um programa, na linguagem que desejar, que calcule e retorne:
• O menor valor de faturamento ocorrido em um dia do mês;
• O maior valor de faturamento ocorrido em um dia do mês;
• Número de dias no mês em que o valor de faturamento diário foi superior à média mensal.

IMPORTANTE:
a) Usar o json ou xml disponível como fonte dos dados do faturamento mensal;
b) Podem existir dias sem faturamento, como nos finais de semana e feriados. Estes dias devem ser ignorados no cálculo da média;

    import json

    # Ler arquivo JSON
    with open('dados.json', 'r') as f:
        dados = json.load(f)

    # Iterar sobre a lista de dicionários e imprimir o conteúdo
    print("-----------------------------------------------")
    print("    Leitura dos dados do faturamento mensal    ")
    print("-----------------------------------------------")

    for d in dados:
        print(f"- Dia {d['dia']} e valor de faturamento R$ {d['valor']}")

    print("-----------------------------------------------\n")

    # Extrair a lista faturamento_diario, ignorando os dias sem faturamento
    faturamento_diario = [dado['valor'] for dado in dados if dado['valor'] != 0]

    # Encontrar valores mínimos e máximos e seus respectivos dias
    min_dado = min(dados, key=lambda x: x['valor'] if x['valor'] != 0 else float('inf'))
    max_dado = max(dados, key=lambda x: x['valor'] if x['valor'] != 0 else float('-inf'))

    # Print do resultado dos dias com maior e menor faturamento
    print("- O menor valor de faturamento: R$ {:.2f} foi no dia {}".format(min_dado['valor'], min_dado['dia']))
    print("- O maior valor de faturamento: R$ {:.2f} foi no dia {}".format(max_dado['valor'], max_dado['dia']))

    # Calcular valor médio (dias sem faturamento, devem ser ignorados no cálculo da média)
    media = sum(faturamento_diario) / len(faturamento_diario)
    print("- Média de faturamento diário: R$ {:.2f}".format(media))

    # Encontrar número de dias com faturamento maior que a média
    dias_acima_media = len([valor for valor in faturamento_diario if valor > media])

    # Print dos dias do mês em que o valor de faturamento diário foi superior à média mensal
    print("- Dias com faturamento acima da média mensal: {}".format(dias_acima_media))
    print("")
    
# 4) Dado o valor de faturamento mensal de uma distribuidora, detalhado por estado:
 
SP – R$67.836,43
RJ – R$36.678,66
MG – R$29.229,88
ES – R$27.165,48
Outros – R$19.849,53

Escreva um programa na linguagem que desejar onde calcule o percentual de representação que cada estado teve dentro do valor total mensal da distribuidora.

    # Define o faturamento mensal de cada estado
    faturamento = {
        'SP': 67836.43,
        'RJ': 36678.66,
        'MG': 29229.88,
        'ES': 27165.48,
        'Outros': 19849.53
    }

    # Calcula o faturamento total mensal da distribuidora
    faturamento_total = sum(faturamento.values())
    print("- O faturamento total mensal da distribuidora é R$", faturamento_total)
    # Calcula o percentual de representação de cada estado
    percentuais = {estado: (valor / faturamento_total) * 100 for estado, valor in faturamento.items()}

    print("\nPercentual de representação que cada estado teve dentro do valor total mensal da distribuidora:")
    # Imprime o resultado para cada estado
    for estado, percentual in percentuais.items():
        print(f"- {estado} tem um percentual de {percentual:.2f}%")

# 5) Escreva um programa que inverta os caracteres de um string.
 
IMPORTANTE:
a) Essa string pode ser informada através de qualquer entrada de sua preferência ou pode ser previamente definida no código;
b) Evite usar funções prontas, como, por exemplo, reverse;

    print("--------------------------------------------")
    string = input("-  Informe uma string: ")
    print("--------------------------------------------")

    string_invertido = ""
    for i in range(len(string)-1, -1, -1):
        string_invertido += string[i]

    print("A string invertida é:", string_invertido)
    print()
