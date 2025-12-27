# StatsForecast

[![CI](https://github.com/Nixtla/statsforecast/actions/workflows/ci.yaml/badge.svg?branch=main)](https://github.com/Nixtla/statsforecast/actions/workflows/ci.yaml)
[![Python](https://img.shields.io/pypi/pyversions/statsforecast)](https://pypi.org/project/statsforecast/)
[![PyPi](https://img.shields.io/pypi/v/statsforecast?color=blue)](https://pypi.org/project/statsforecast/)
[![conda-forge](https://img.shields.io/conda/vn/conda-forge/statsforecast?color=seagreen&label=conda)](https://anaconda.org/conda-forge/statsforecast)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://github.com/Nixtla/statsforecast/blob/main/LICENSE)

**StatsForecast** é uma biblioteca de previsão de extremo desempenho, otimizada para cálculos estatísticos e econométricos rápidos. Ela oferece uma suíte completa de modelos de séries temporais univariadas, incluindo `AutoARIMA`, `ETS`, `CES` e `Theta`, compilados com `numba` para agilidade máxima.

## Principais Recursos

*   **Velocidade:** Processamento ultrarrápido, ideal para grandes volumes de dados.
*   **Escalabilidade:** Capacidade de prever milhões de séries temporais com eficiência.
*   **Modelos Estatísticos:** Implementações precisas de modelos clássicos e modernos.
*   **Leveza:** Baixo consumo de memória e dependências mínimas.

## Instalação

Instale via pip:

bash
pip install statsforecast


Ou via conda:

bash
conda install -c conda-forge statsforecast


## Começo Rápido

Exemplo básico de utilização com `AutoARIMA`:

python
import pandas as pd
from statsforecast import StatsForecast
from statsforecast.models import AutoARIMA

# 1. Preparar o dataframe (unique_id, ds, y)
df = pd.DataFrame({
    'unique_id': ['A'] * 24,
    'ds': pd.date_range(start='2020-01-01', periods=24, freq='M'),
    'y': [i + (i % 5) for i in range(24)]
})

# 2. Inicializar o objeto
sf = StatsForecast(
    models=[AutoARIMA(season_length=12)],
    freq='M'
)

# 3. Treinar e Prever
sf.fit(df)
forecast_df = sf.predict(h=12, level=[95])

print(forecast_df)


## Documentação

Acesse a [Documentação Oficial](https://nixtla.github.io/statsforecast/) para guias detalhados e exemplos avançados.

## Por que escolher o StatsForecast?

Diferente de outras ferramentas que priorizam interfaces gráficas ou simplicidade excessiva ao custo de performance, o StatsForecast foi construído para a realidade industrial. Ele permite aplicar modelos estatísticos complexos em tempo real, mesmo com grandes bases de dados, sem perda de precisão.