# Nexus ELECTRE — Relações de Sobreclassificação Não-Compensatórias

Este repositório é o módulo independente do ecossistema **NEXUS MCDM**, configurado para operar exclusivamente com a família de métodos **ELECTRE (Elimination Et Choix Traduisant la Realité)**.

---

## 🎨 Identidade Visual e Branding
- **Nome Oficial:** Nexus ELECTRE
- **Cores Oficiais:** Índigo (`#4F46E5`) e Violeta (`#7C3AED`)
- **Conceito Visual:** Grafo de sobreclassificação direta conectando alternativas e arcos direcionais.
- **Copyright:** Direitos Reservados © 2026 NEXUS-MCDM.

---

## 🌟 Recursos e Matemática

- **Racionalidade Não-Compensatória:** Impede a compensação de desempenhos ruins através da aplicação de veto absoluto.
- **Variantes Suportadas:**
  - **ELECTRE I:** Escolha de alternativas com limiares nítidos.
  - **ELECTRE IS:** Escolha incorporando pseudo-critérios e limiares de veto local.
  - **ELECTRE II:** Ordenação baseada em relações de sobreclassificação fortes e fracas.
  - **ELECTRE III:** Ordenação avançada usando matriz de credibilidade de sobreclassificação baseada em limiares locais de indiferença (q), preferência (p) e veto (v).
  - **ELECTRE IV:** Ordenação ordinal direta sem a necessidade de elicitar pesos de critérios.
  - **ELECTRE TRI:** Classificação das alternativas em categorias pré-definidas.
- **Relatório Completo PDF:** Visualização do Kernel e relações de preferência.

---

## 🚀 Instalação e Execução
```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python app.py
```
