import sqlite3
import tkinter as tk
from tkinter import messagebox
from tkinter import simpledialog


# Função para criar a tabela no banco de dados se não existir
def criar_tabela(conn):
    conn.execute('''CREATE TABLE IF NOT EXISTS resultados (
                     id INTEGER PRIMARY KEY AUTOINCREMENT,
                     nome TEXT,
                     idade INTEGER,
                     sexo TEXT,
                     objetivo TEXT,
                     peso REAL,
                     altura REAL,
                     imc REAL,
                     CaloriasPorDia REAL,
                     email TEXT
                     )''')
    conn.commit()


# Função para inserir os dados da avaliação na tabela
def inserir_resultado(conn, nome, idade, sexo, objetivo, peso, altura, imc, calorias_por_dia, email):
    conn.execute('''INSERT INTO resultados (nome, idade, sexo, objetivo, peso, altura, imc, CaloriasPorDia, email)
                    VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?)''',
                 (nome, idade, sexo, objetivo, peso, altura, imc, calorias_por_dia, email))
    conn.commit()


# Função para exibir os resultados anteriores
def exibir_resultados(conn, email):
    cursor = conn.execute("SELECT * FROM resultados WHERE email = ?", (email,))
    resultados = cursor.fetchall()
    return resultados


def avaliar():
    nome = simpledialog.askstring("Avaliação Nova", "Qual é o seu nome?")
    idade = simpledialog.askinteger("Avaliação Nova", "Qual é a sua idade?")

    sexo = simpledialog.askstring("Avaliação Nova", "Qual é o seu sexo? (M/F)").strip().upper()
    objetivo = simpledialog.askstring("Avaliação Nova", "Qual é o seu objetivo? (Emagrecer/Engordar)").strip().lower()
    peso = simpledialog.askfloat("Avaliação Nova", "Qual é o seu peso atual? (kg)")
    altura = simpledialog.askfloat("Avaliação Nova", "Qual é a sua altura? (m)")
    email = simpledialog.askstring("Avaliação Nova", "Qual é o seu e-mail para enviar os resultados?")

    if peso is None or altura is None or altura <= 0:
        messagebox.showerror("Erro", "Por favor, insira valores válidos para peso e altura.")
        return

    # Cálculo do IMC
    imc = peso / (altura ** 2)

    # Verificar se o IMC foi calculado corretamente
    if imc == 0:
        messagebox.showerror("Erro", "O cálculo do IMC retornou zero. Verifique os valores inseridos.")
        return

    # Cálculo das calorias
    if sexo == "F":
        if idade <= 3:
            calorias_por_dia = (58.317 * peso) - 31.1
        elif idade <= 10:
            calorias_por_dia = (20.315 * peso) + 485.9
        elif idade <= 18:
            calorias_por_dia = (13.384 * peso) + 692.6
        elif idade <= 30:
            calorias_por_dia = (14.818 * peso) + 486.6
        elif idade <= 60:
            calorias_por_dia = (8.126 * peso) + 845.6
        else:
            calorias_por_dia = (9.082 * peso) + 658.5
    else:
        if idade <= 3:
            calorias_por_dia = (59.512 * peso) - 30.4
        elif idade <= 10:
            calorias_por_dia = (22.706 * peso) + 504.3
        elif idade <= 18:
            calorias_por_dia = (17.686 * peso) + 658.2
        elif idade <= 30:
            calorias_por_dia = (15.057 * peso) + 692.2
        elif idade <= 60:
            calorias_por_dia = (11.472 * peso) + 873.1
        else:
            calorias_por_dia = (11.711 * peso) + 587.7

    if objetivo == "emagrecer":
        calorias_por_dia -= 500
    elif objetivo == "engordar":
        calorias_por_dia += 500

    imc_formatado = f"{imc:.2f}"
    calorias_formatadas = f"{calorias_por_dia:.2f}"

    # Determinando peso ideal
    peso_ideal = 18.5 * (altura ** 2)

    if peso < peso_ideal - 2 or peso > peso_ideal + 2:
        alerta = "Seu peso está fora da faixa ideal. Recomendamos que você marque uma consulta para um acompanhamento mais detalhado."
    else:
        alerta = "Você está no peso ideal!"

    if objetivo == "engordar":
        alerta += "\nComo seu objetivo é engordar, é importante que você siga um plano alimentar específico para ganhar peso de forma saudável."

    # Mostrar resultado
    result_message = f"Seu IMC é {imc_formatado}\nA quantidade de calorias que você deve ingerir por dia é de: {calorias_formatadas} cal/dia\n\n{alerta}"
    messagebox.showinfo("Resultado da Avaliação", result_message)

    # Salvando os resultados no banco de dados
    inserir_resultado(conn, nome, idade, sexo, objetivo, peso, altura, imc, calorias_por_dia, email)

    if peso < peso_ideal - 2 or peso > peso_ideal + 2:
        resposta = messagebox.askyesno("Marcar Consulta",
                                       "Você gostaria de marcar uma consulta para um acompanhamento mais detalhado?")
        if resposta:
            marcar_consulta()


def resultados_anteriores():
    email = simpledialog.askstring("Resultados Anteriores",
                                   "Por favor, insira seu e-mail para exibir os resultados anteriores:")
    resultados = exibir_resultados(conn, email)

    if resultados:
        msg = "\n".join([
                            f"ID: {row[0]}, Nome: {row[1]}, Idade: {row[2]}, Sexo: {row[3]}, Objetivo: {row[4]}, Peso: {row[5]}, Altura: {row[6]}, IMC: {row[7]:.2f}, Calorias/Dia: {row[8]:.2f}"
                            for row in resultados])
        messagebox.showinfo("Resultados Anteriores", msg)
    else:
        messagebox.showinfo("Resultados Anteriores", "Nenhum resultado encontrado para este e-mail.")


def marcar_consulta():
    messagebox.showinfo("Marcar Consulta",
                        "Que legal!! Aguarde uns minutos enquanto te transferimos para uma atendente da clínica.")


def sair():
    resposta = messagebox.askyesno("Sair", "Deseja falar com um atendente? Se não, será encerrado.")
    if resposta:
        marcar_consulta()
    else:
        root.destroy()


# Conectar ao banco de dados (ou criar se não existir)
conn = sqlite3.connect('resultados.db')
criar_tabela(conn)

# Configuração da interface gráfica
root = tk.Tk()
root.title("Bot de Avaliação")

tk.Button(root, text="Avaliação Nova", command=avaliar).pack(pady=10)
tk.Button(root, text="Resultados Anteriores", command=resultados_anteriores).pack(pady=10)
tk.Button(root, text="Marcar Consulta", command=marcar_consulta).pack(pady=10)
tk.Button(root, text="Sair", command=sair).pack(pady=10)

root.mainloop()
