# ChatNutri — Assistente Virtual de Nutrição com IA ✨

![image](https://github.com/user-attachments/assets/a403e7ad-740a-4557-a992-88cd51a8f634)


## 🌟 Visão Geral

Projeto desenvolvido como parte da avaliação semestral do primeiro período do curso de Ciência da Computação da Universidade Nove de Julho (Uninove). 

**Tecnologias utilizadas:**
- 🐍 Python 3.8+
- 🖼️ Tkinter (Interface Gráfica)
- 🧠 Lógica de IA para recomendações personalizadas

**Objetivo:**  
Fornecer uma plataforma inteligente para gerenciamento de dietas e treinos, ajudando usuários a atingirem suas metas de saúde e fitness com planos 100% personalizados.

---

## 🚀 Funcionalidades Principais

### 🔍 Cálculo de Necessidade Calórica
- Fórmula de Harris-Benedict
- Cálculo de Taxa Metabólica Basal (BMR)
- Necessidade Calórica Total (TDEE) personalizada

### 🍏 Plano de Refeições Inteligente
- Geração de cardápios equilibrados
- Adaptação às preferências alimentares
- Distribuição ideal de macronutrientes

### 💪 Programa de Treinamento Personalizado
- Periodização adaptada ao nível do usuário
- Foco na meta específica (emagrecimento, hipertrofia, etc.)
- Evolução progressiva dos exercícios

---

## 📥 Como Usar

### 1. Instalação

```bash
git clone https://github.com/seu-usuario/ChatNutri.git
cd ChatNutri
````

### 2. Execução

```bash
python sistema_dieta_treino.py
```

### 3. Fluxo de Uso

* Preencha seus dados pessoais
* Defina suas preferências e metas
* Receba planos alimentares e de treino
* Acompanhe sua evolução

---

## 🧩 Estrutura do Código

```python
# Cálculos Nutricionais
def calcular_necessidade_calorica(peso, altura, idade, nivel_atividade):
    """Calcula TDEE com fórmula Harris-Benedict"""
    ...

# Gerador de Dietas
def criar_plano_refeicoes(necessidade_calorica, preferencias):
    """Gera plano alimentar personalizado"""
    ...

# Gerador de Treinos
def criar_programa_treinamento(meta, nivel):
    """Cria periodização de exercícios"""
    ...
```

---

## 📦 Dependências

| Pacote  | Versão |
| ------- | ------ |
| Python  | 3.8+   |
| Tkinter | Padrão |

---

## 🤝 Como Contribuir

1. Faça um fork do projeto
2. Crie sua feature branch:

   ```bash
   git checkout -b feature/nova-feature
   ```
3. Commit suas mudanças:

   ```bash
   git commit -m 'Adiciona nova feature'
   ```
4. Push para a branch:

   ```bash
   git push origin feature/nova-feature
   ```
5. Abra um Pull Request

---

## 📜 Licença

Este projeto está licenciado sob a Licença MIT - consulte o arquivo `LICENSE.md` para mais detalhes.

---

## 💡 Dúvidas ou sugestões?

Abra uma issue ou entre em contato com nossa equipe!

📆 **Última atualização:** Junho/2024

```

