# Nexus ELECTRE — Relações de Sobreclassificação Não-Compensatórias

Este repositório é o módulo independente do ecossistema **NEXUS MCDM**, configurado para operar exclusivamente com a família de métodos **ELECTRE**.

---

## 🎨 Identidade Visual e Branding
- **Nome Oficial:** Nexus ELECTRE
- **Cores Oficiais:** Índigo (`#4F46E5`) e Violeta (`#7C3AED`)
- **Conceito Visual:** Grafo de sobreclassificação direta conectando alternativas e arcos direcionais.
- **Copyright:** Direitos Reservados © 2026 NEXUS-MCDM. Todos os direitos reservados.

---

## 🧠 Formulação Matemática e Funcionamento

A família de métodos **ELECTRE** adota o conceito de relações de sobreclassificação ($a S b$ - a alternativa $a$ é pelo menos tão boa quanto a alternativa $b$). Diferente dos métodos clássicos, o ELECTRE não permite compensação através da aplicação de restrições de veto.

### 1. Limiares e Pseudo-critérios
Para modelar a subjetividade e a imperfeição dos dados, cada critério possui limiares:
* **Limiar de Indiferença ($q$):** A menor diferença física onde o decisor é indiferente.
* **Limiar de Preferência ($p$):** A diferença física a partir da qual existe preferência clara.
* **Limiar de Veto ($v$):** A diferença máxima aceitável no critério. Se a desvantagem física de uma alternativa sobre a outra exceder o veto $v_j$, impede-se a afirmação de sobreclassificação, independentemente das notas nos demais critérios.

### 2. Concordância e Discordância (ELECTRE III)
* **Índice de Concordância Local ($c_j(a, b)$):**
  $$c_j(a, b) = \begin{cases} 
  1 & \text{se } g_j(a) \ge g_j(b) - q_j \\ 
  0 & \text{se } g_j(a) < g_j(b) - p_j \\ 
  \frac{p_j - (g_j(b) - g_j(a))}{p_j - q_j} & \text{caso contrário} 
  \end{cases}$$
* **Índice de Concordância Global ($C(a, b)$):**
  $$C(a, b) = \sum_{j=1}^n w_j \cdot c_j(a, b)$$
* **Índice de Discordância Local ($d_j(a, b)$):**
  $$d_j(a, b) = \begin{cases} 
  0 & \text{se } g_j(a) \ge g_j(b) - p_j \\ 
  1 & \text{se } g_j(a) < g_j(b) - v_j \\ 
  \frac{(g_j(b) - g_j(a)) - p_j}{v_j - p_j} & \text{caso contrário} 
  \end{cases}$$

### 3. Matriz de Credibilidade ($\sigma(a, b)$)
A força da hipótese "a sobreclassifica b" é expressa pelo grau de credibilidade:
$$\sigma(a, b) = C(a, b) \prod_{j \in F} \frac{1 - d_j(a, b)}{1 - C(a, b)}$$
Onde $F$ é o conjunto de critérios para os quais a discordância local é maior do que a concordância global: $F = \{j \mid d_j(a, b) > C(a, b)\}$.

### 4. Algoritmo de Destilação
Para ordenar as alternativas, o resolvedor do ELECTRE realiza duas destilações direcionais (ascendente e descendente) com base em cortes de credibilidade sucessivos ($\lambda$). A ordenação final é gerada pela interseção dessas duas destilações.

---

## 🚀 Instalação e Execução
```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python app.py
```
Acesse: `http://127.0.0.1:5000`
