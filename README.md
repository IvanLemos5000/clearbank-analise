# ClearBank — Análise Financeira com Python

Desafio final do módulo de Python para Análise de Dados.

O projeto lê o arquivo `transacoes.csv`, valida cada registro, agrupa as transações
por mês, calcula métricas financeiras, sinaliza transações suspeitas e exporta o
resultado em `relatorio.json`.

---

## 📂 Estrutura do repositório

clearbank-analise/
├── desafio-final.ipynb   # Notebook principal (com saídas salvas)  [obrigatório]
├── transacoes.csv        # Base de entrada (16 válidas + 6 inválidas)
├── relatorio.json        # Gerado automaticamente ao rodar o notebook
├── analise_pandas.py     # (opcional) versão alternativa com pandas
├── grafico.png           # (opcional) gráfico matplotlib
└── README.md             # Este arquivo                            [obrigatório]

---

## ▶️ Como executar

### Google Colab (recomendado)
1. Faça upload do arquivo `transacoes.csv` (ícone de pasta no painel lateral).
2. Abra `desafio-final.ipynb` no Colab.
3. Menu Ambiente de execução → Executar tudo.
4. Aguarde — o relatório será impresso no terminal e `relatorio.json` será gerado.

### Jupyter Notebook local
    # (opcional) dependências extras
    pip install pandas matplotlib

    jupyter notebook desafio-final.ipynb

### Execução via linha de comando
    jupyter nbconvert --to notebook --execute desafio-final.ipynb

---

## 🧠 Requisitos atendidos

| Requisito                                          | Status |
|----------------------------------------------------|--------|
| Leitura com csv.DictReader (módulo nativo)         | OK     |
| Validação de id, cliente_id, data, tipo, valor     | OK     |
| Mínimo 4 funções com responsabilidades separadas   | OK (9) |
| Conversão de datas com datetime.strptime           | OK     |
| Agrupamento mensal + saldo + média + maior/menor   | OK     |
| Constante LIMITE_SUSPEITO = 10000.00               | OK     |
| Exportação de relatorio.json                       | OK     |
| try/except em 3+ situações distintas               | OK (4) |
| Relatório formatado no terminal com separadores    | OK     |
| (Opcional) Análise alternativa com pandas          | OK     |
| (Opcional) Visualização com matplotlib             | OK     |

---

## 📊 Métricas calculadas por mês

Para cada mês (AAAA-MM) presente nos dados:

- Quantidade de transações
- Total de crédito
- Total de débito
- Saldo (crédito − débito)
- Média por transação
- Maior valor no mês
- Menor valor no mês

Também é calculado o número de dias entre a transação mais antiga e a mais recente.

---

## 🚨 Regra de suspeita

Qualquer transação com valor > LIMITE_SUSPEITO (padrão R$ 10.000,00) é listada ao
final do relatório com id, cliente_id, data e valor.

Se não houver nenhuma, é exibida a mensagem:
> Nenhuma transação suspeita encontrada.

---

## 📄 Estrutura do relatorio.json

    {
      "gerado_em": "2026-05-14",
      "total_transacoes_validas": 16,
      "total_transacoes_invalidas": 6,
      "periodo": {
        "inicio": "2026-01-05",
        "fim": "2026-03-25",
        "dias": 79
      },
      "resumo_mensal": {
        "2026-01": {
          "quantidade": 5,
          "total_credito": 7700.00,
          "total_debito": 505.80,
          "saldo": 7194.20,
          "media": 1641.16,
          "maior_valor": 4200.00,
          "menor_valor": 75.30
        }
      },
      "transacoes_suspeitas": [
        {
          "id": 5,
          "cliente_id": "CLI003",
          "data": "2026-02-14",
          "valor": 15000.00
        },
        {
          "id": 15,
          "cliente_id": "CLI005",
          "data": "2026-03-20",
          "valor": 12000.00
        }
      ]
    }

---

## 🧪 Dataset de teste (transacoes.csv)

O arquivo contém:

- 16 registros válidos distribuídos em 3 meses (jan, fev, mar/2026)
- 6 registros inválidos para exercitar a validação:
  - id não numérico
  - cliente_id vazio
  - data mal formatada
  - tipo diferente de credito/debito
  - valor negativo
  - valor igual a zero
- 2 transações acima de R$ 10.000,00 para acionar a regra de suspeita

---

## ✅ Checklist de entrega

- [x] Célula principal roda do início ao fim sem erros
- [x] Código organizado em 9 funções com responsabilidades separadas
- [x] try/except presente em pelo menos 3 situações distintas
- [x] relatorio.json gerado corretamente
- [x] Relatório formatado exibido no terminal
- [x] Notebook com saídas salvas
- [x] README.md básico
- [x] (Opcional) analise_pandas.py
- [x] (Opcional) grafico.png

---

## 👤 Autor

Seu Nome — @ivanlemos5000

Desafio final do módulo Análise Financeira com Python.
