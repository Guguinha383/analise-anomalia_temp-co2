# 🌡️ Análise Econométrica: Aquecimento Global, CO₂ e El Niño

> **Uma investigação estatística sobre os drivers da temperatura global: separando a tendência de longo prazo da variabilidade natural de curto prazo.**

## 📖 Sobre o Projeto

Este projeto nasceu de um estudo exploratório sobre anomalias de temperatura global. Inicialmente focado em uma regressão linear simples entre emissões de CO₂ e temperatura, o estudo evoluiu para uma análise de **Séries Temporais** robusta.

O objetivo principal foi investigar se a correlação entre CO₂ e temperatura era causal no curto prazo ou se tratava de uma **Regressão Espúria**. Com insights de engenheiros ambientais, o modelo foi refinado para incluir ciclos oceânicos (El Niño/La Niña), revelando a dinâmica real entre forçantes antropogênicos e naturais.

---

## 📊 Principais Descobertas

| Variável | Papel no Clima | Resultado Estatístico |
| :--- | :--- | :--- |
| **Emissões de CO₂** | Tendência de Longo Prazo (Stock) | Significativo em níveis, mas perde significância em *primeiras diferenças* ($p > 0.05$). Atua no acumulado. |
| **El Niño (ONI)** | Variabilidade de Curto Prazo (Flow) | Altamente significativo ($p < 0.01$) na explicação das flutuações anuais da temperatura. |

**Conclusão:** O aquecimento global é uma tendência de fundo impulsionada pelo CO₂, mas os "solavancos" anuais de temperatura são dominados pela dinâmica do Oceano Pacífico.

---

## 🛠️ Metodologia

A análise seguiu um rigoroso processo econométrico:

1.  **Coleta e ETL:**
    * Dados de Anomalia de Temperatura (NASA GISS).
    * Emissões Globais de CO₂ (Our World in Data).
    * Índice Oceânico Niño - ONI (NOAA).

2.  **Diagnóstico Inicial (A "Armadilha"):**
    * O modelo simples apresentou $R^2 > 0.90$, sugerindo alta correlação.
    * Contudo, o teste **Augmented Dickey-Fuller (ADF)** confirmou que as séries não eram estacionárias.
    * O teste **Durbin-Watson** indicou forte autocorrelação nos resíduos, diagnosticando uma **regressão espúria**.

3.  **Correção e Refinamento:**
    * Aplicação de **Primeiras Diferenças** (`diff`) para tornar as séries estacionárias.
    * Criação de **Defasagens (Lags)** para testar causalidade temporal.
    * Inclusão da variável de controle **ONI (El Niño)** para mitigar o viés de variável omitida.

---

## 📈 Visualizações

### 1. A Prova Visual: El Niño vs Variação da Temperatura
*Observe como os picos de aquecimento global (linha pontilhada) coincidem perfeitamente com os picos do El Niño (áreas vermelhas).*

<img width="4170" height="2070" alt="Influência dos Ciclos do El Niño (ONI) na Variabilidade da Temperatura Anual" src="https://github.com/user-attachments/assets/bcef0903-5f8b-483c-a3aa-ec31ed9988ba" />


## 💻 Stack Tecnológica

* **Linguagem:** Python
* **Manipulação de Dados:** Pandas, NumPy
* **Estatística e Econometria:** Statsmodels (OLS, ADF, Granger Causality)
* **Visualização:** Matplotlib, Seaborn, Lets-Plot

---

## 🚀 Como Rodar o Projeto

1. **Clone o repositório:**
   ```bash
   git clone [https://github.com/Guguinha383/analise-anomalia_temp-co2.git](https://github.com/Guguinha383/analise-anomalia_temp-co2.git)
