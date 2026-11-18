
# Meu projeto: Organizador de Conversas
# Desenvolvido em Python

# Primeiro vou criar algumas mensagens de exemplo
# para testar o funcionamento do organizador.

mensagens = [
    "Ola, gostaria de saber o preco do produto",
    "Estou enviando meu curriculo para a vaga",
    "Preciso confirmar o pagamento da cobranca",
    "Gostaria de informacoes sobre atendimento",
    "Segue meu curriculo atualizado",
    "O pagamento foi realizado hoje",
    "Tenho interesse em conhecer os servicos",
    "Bom dia, tudo bem?"
]


# Aqui vou separar as palavras que identificam
# cada tipo de mensagem.

categorias = {
    "Clientes": ["preco", "produto", "servicos"],
    "Curriculos": ["curriculo", "vaga", "emprego"],
    "Financeiro": ["pagamento", "cobranca", "boleto"],
    "Atendimento": ["atendimento", "informacoes"]
}


# Esta funcao vai analisar cada mensagem
# e descobrir em qual categoria ela se encaixa.

def organizar_mensagens(lista_de_mensagens):

    organizadas = {
        categoria: [] for categoria in categorias
    }

    # Se a mensagem nao se encaixar em nenhuma categoria,
    # ela sera colocada em Outros.

    organizadas["Outros"] = []

    for mensagem in lista_de_mensagens:

        mensagem_classificada = False

        # Vou verificar as palavras de cada categoria.

        for categoria, palavras in categorias.items():

            for palavra in palavras:

                if palavra in mensagem.lower():

                    organizadas[categoria].append(mensagem)

                    mensagem_classificada = True
                    break

            if mensagem_classificada:
                break

        # Se nenhuma palavra for encontrada,
        # a mensagem vai para a categoria Outros.

        if not mensagem_classificada:
            organizadas["Outros"].append(mensagem)

    return organizadas


# Agora vou executar o organizador.

resultado = organizar_mensagens(mensagens)


# Aqui vou mostrar tudo que foi encontrado.

print("=" * 40)
print("       ORGANIZADOR DE CONVERSAS")
print("=" * 40)

for categoria, mensagens_encontradas in resultado.items():

    print(f"\nCategoria: {categoria}")

    if mensagens_encontradas:

        for mensagem in mensagens_encontradas:
            print(f" - {mensagem}")

    else:
        print(" Nenhuma mensagem encontrada.")


print("\n" + "=" * 40)
print("Organizacao concluida com sucesso!")
print("=" * 40)
