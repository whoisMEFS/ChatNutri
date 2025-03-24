# Sistema de Dieta e Treino

## Visão Geral

Este projeto é um Sistema de Dieta e Treino desenvolvido em Python usando a biblioteca Tkinter para a interface gráfica. O sistema permite que o usuário insira seus dados pessoais, como peso, altura, idade, nível de atividade física, preferências alimentares, meta de treino e nível de experiência. Com base nesses dados, o sistema calcula a necessidade calórica do usuário, gera um plano de refeições equilibrado e cria um programa de treinamento periodizado.

## Funcionalidades

1. **Calcular Necessidade Calórica:**
   - Baseado na fórmula de Harris-Benedict, calcula a Taxa Metabólica Basal (BMR) e a Necessidade Calórica Total (TDEE) do usuário.

2. **Criar Plano de Refeições:**
   - Gera um plano de refeições equilibrado com base nas necessidades calóricas e preferências alimentares do usuário.
   
3. **Criar Programa de Treinamento:**
   - Desenvolve um programa de treinamento periodizado com base nas metas de condicionamento físico e nível de experiência do usuário.

## Como Usar

1. Clone este repositório para o seu ambiente local:
   ```bash
   git clone <URL_DO_REPOSITÓRIO>
   ```

2. Navegue até o diretório do projeto:
   ```bash
   cd <NOME_DO_DIRETÓRIO>
   ```

3. Certifique-se de ter o Python instalado em sua máquina. Este projeto foi desenvolvido usando Python 3.8+.

4. Execute o script Python para iniciar a aplicação:
   ```bash
   python sistema_dieta_treino.py
   ```

5. Insira seus dados nos campos apropriados:
   - Peso (kg)
   - Altura (m)
   - Idade
   - Nível de Atividade (Sedentário, Levemente Ativo, Moderadamente Ativo, Muito Ativo)
   - Preferências Alimentares
   - Meta de Treino
   - Nível de Experiência (Iniciante, Intermediário, Avançado)

6. Clique no botão "Processar" para gerar o plano de refeições e o programa de treinamento.

7. Os resultados serão exibidos na caixa de texto na interface gráfica.

## Estrutura do Código

- **calcular_necessidade_calorica(peso, altura, idade, nivel_atividade):** Calcula a necessidade calórica total baseada nos dados do usuário.
- **criar_plano_refeicoes(necessidade_calorica, preferencias_alimentares):** Gera um plano de refeições equilibrado.
- **criar_programa_treinamento(meta, nivel_experiencia):** Cria um programa de treinamento periodizado.
- **processar_dados():** Processa os dados inseridos pelo usuário e exibe os resultados.
- **Interface Gráfica:** Utiliza a biblioteca Tkinter para criar a interface gráfica do usuário (GUI).

## Dependências

- Python 3.8+
- Tkinter (incluído na biblioteca padrão do Python)

## Contribuição

1. Faça um fork deste repositório.
2. Crie um branch para sua feature (`git checkout -b feature/AmazingFeature`).
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`).
4. Faça o push para o branch (`git push origin feature/AmazingFeature`).
5. Abra um Pull Request.

## Licença

Este projeto é licenciado sob a [Licença MIT](LICENSE).

---

Qualquer dúvida ou sugestão, sinta-se à vontade para entrar em contato. Aproveite o sistema e bons treinos!
