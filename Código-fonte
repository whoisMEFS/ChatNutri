import tkinter as tk
import random


# Função para calcular a necessidade calórica baseada nos dados do usuário
def calcular_necessidade_calorica(peso, altura, idade, nivel_atividade):
    # Cálculo do BMR usando a fórmula de Harris-Benedict
    BMR = 10 * peso + 6.25 * altura * 100 - 5 * idade + 5  # Para homens
    # BMR = 10 * peso + 6.25 * altura * 100 - 5 * idade - 161  # Para mulheres

    # Fator de atividade física
    if nivel_atividade == "Sedentário":
        fator_atividade = 1.2
    elif nivel_atividade == "Levemente Ativo":
        fator_atividade = 1.375
    elif nivel_atividade == "Moderadamente Ativo":
        fator_atividade = 1.55
    elif nivel_atividade == "Muito Ativo":
        fator_atividade = 1.725

    # Cálculo do TDEE
    necessidade_calorica_total = BMR * fator_atividade
    return necessidade_calorica_total


# Função para criar um plano de refeições equilibrado com base nas necessidades calóricas e preferências alimentares
def criar_plano_refeicoes(necessidade_calorica, preferencias_alimentares):
    # Dicionário de exemplo com refeições para cada período do dia
    refeicoes = {
        "Café da Manhã": ["Iogurte natural com granola", "Mingau de aveia com frutas", "Omelete de legumes"],
        "Almoço": ["Macarrão integral com molho de tomate e legumes",
                   "Arroz integral, feijão, frango grelhado e salada", "Peixe assado com batata-doce e brócolis"],
        "Jantar": ["Wrap de frango com vegetais", "Salada de quinoa com legumes grelhados", "Sopa de legumes"]
    }

    # Calcular número aproximado de calorias por refeição
    calorias_por_refeicao = necessidade_calorica / 3

    # Criar plano de refeições baseado nas preferências alimentares
    plano_refeicoes = {}
    for periodo, opcoes_refeicao in refeicoes.items():
        # Selecionar aleatoriamente uma refeição da lista de opções
        refeicao_selecionada = random.choice(opcoes_refeicao)
        # Adicionar a refeição ao plano de refeições
        plano_refeicoes[periodo] = {"Refeição": refeicao_selecionada, "Calorias": calorias_por_refeicao}

    return plano_refeicoes


# Função para criar um programa de treinamento periodizado com base nas metas de condicionamento físico e nível de experiência
def criar_programa_treinamento(meta, nivel_experiencia):
    # Lista de exercícios de cardio e de força
    exercicios_cardio = ["Corrida", "Ciclismo", "Pular corda"]
    exercicios_forca = ["Flexões", "Agachamentos", "Levantamento de peso"]

    # Definir o número de dias de treino por semana e o número de exercícios por dia
    dias_semana = 3
    exercicios_por_dia = 2

    # Criar o programa de treinamento
    programa_treinamento = {}
    for dia in range(1, dias_semana + 1):
        exercicios_do_dia = []
        for _ in range(exercicios_por_dia):
            # Selecionar aleatoriamente um exercício de cardio e um de força
            exercicio_cardio = random.choice(exercicios_cardio)
            exercicio_forca = random.choice(exercicios_forca)
            exercicios_do_dia.append(exercicio_cardio)
            exercicios_do_dia.append(exercicio_forca)
        programa_treinamento[f"Dia {dia}"] = exercicios_do_dia

    return programa_treinamento


# Função para processar os dados inseridos pelo usuário e exibir resultados
def processar_dados():
    try:
        peso = float(entry_peso.get())
        altura = float(entry_altura.get())
        idade = int(entry_idade.get())
        nivel_atividade = nivel_atividade_var.get()
        preferencias_alimentares = entry_preferencias.get()
        meta = entry_meta.get()
        nivel_experiencia = nivel_experiencia_var.get()

        # Calcular necessidade calórica
        necessidade_calorica = calcular_necessidade_calorica(peso, altura, idade, nivel_atividade)

        # Criar plano de refeições
        plano_refeicoes = criar_plano_refeicoes(necessidade_calorica, preferencias_alimentares)

        # Criar programa de treinamento
        programa_treinamento = criar_programa_treinamento(meta, nivel_experiencia)

        # Limpar o conteúdo atual da caixa de texto de resultados
        text_resultados.delete(1.0, tk.END)

        # Adicionar resultados na caixa de texto de resultados
        text_resultados.insert(tk.END, "Plano de Refeições:\n")
        for periodo, refeicao_info in plano_refeicoes.items():
            text_resultados.insert(tk.END,
                                   f"{periodo}: {refeicao_info['Refeição']} - {refeicao_info['Calorias']:.2f} calorias\n")
        text_resultados.insert(tk.END, "\nPrograma de Treinamento:\n")
        for dia, exercicios in programa_treinamento.items():
            text_resultados.insert(tk.END, f"{dia}:\n")
            for exercicio in exercicios:
                text_resultados.insert(tk.END, f"- {exercicio}\n")
            text_resultados.insert(tk.END, "\n")
    except ValueError:
        text_resultados.delete(1.0, tk.END)
        text_resultados.insert(tk.END, "Por favor, insira valores válidos para todos os campos.")


# Interface gráfica
root = tk.Tk()
root.title("Sistema de Dieta e Treino")

# Labels e entry fields para entrada de dados do usuário
tk.Label(root, text="Peso (kg):").grid(row=0, column=0)
entry_peso = tk.Entry(root)
entry_peso.grid(row=0, column=1)

tk.Label(root, text="Altura (m):").grid(row=1, column=0)
entry_altura = tk.Entry(root)
entry_altura.grid(row=1, column=1)

tk.Label(root, text="Idade:").grid(row=2, column=0)
entry_idade = tk.Entry(root)
entry_idade.grid(row=2, column=1)

tk.Label(root, text="Nível de Atividade:").grid(row=3, column=0)
nivel_atividade_var = tk.StringVar(value="Sedentário")
nivel_atividade_options = ["Sedentário", "Levemente Ativo", "Moderadamente Ativo", "Muito Ativo"]
nivel_atividade_dropdown = tk.OptionMenu(root, nivel_atividade_var, *nivel_atividade_options)
nivel_atividade_dropdown.grid(row=3, column=1)

tk.Label(root, text="Preferências Alimentares:").grid(row=4, column=0)
entry_preferencias = tk.Entry(root)
entry_preferencias.grid(row=4, column=1)

tk.Label(root, text="Meta de Treino:").grid(row=5, column=0)
entry_meta = tk.Entry(root)
entry_meta.grid(row=5, column=1)

tk.Label(root, text="Nível de Experiência:").grid(row=6, column=0)
nivel_experiencia_var = tk.StringVar(value="Iniciante")
nivel_experiencia_options = ["Iniciante", "Intermediário", "Avançado"]
nivel_experiencia_dropdown = tk.OptionMenu(root, nivel_experiencia_var, *nivel_experiencia_options)
nivel_experiencia_dropdown.grid(row=6, column=1)

# Botão para processar os dados
tk.Button(root, text="Processar", command=processar_dados).grid(row=7, columnspan=2)

# Caixa de texto para exibir os resultados
text_resultados = tk.Text(root, height=20, width=50)
text_resultados.grid(row=8, columnspan=2)

root.mainloop()
