# mooc-optimization

## Sobre o problema

Dado um orçamento limitado de intervenções por semana, este projeto busca selecionar
dinamicamente em quais alunos intervir e qual intervenção aplicar para maximizar a
retenção ao longo de um MOOC.

O problema é formulado como **Programação Inteira Binária Multi-período (PIBM)**
e resolvido com métodos exatos (Branch-and-Bound via PuLP/CBC) e heurísticos
(Guloso, Simulated Annealing, GRASP).

## Dataset

KDD Cup 2015 — predição de dropout em MOOCs da plataforma XuetangX.

Disponível em: [https://www.kaggle.com/datasets/sst2023/kdd-cup-2015](https://www.kaggle.com/datasets/sst2023/kdd-cup-2015)

## Pipeline de Execução

Execute os notebooks na seguinte ordem:

1. `pipeline.ipynb` — preparação dos dados, extração de features e modelo LightGBM
2. `optimization.ipynb` — métodos exatos e heurísticos
3. `results.ipynb` — comparação e gráficos

## Instalação

```bash
pip install -r requirements.txt
```

## Estrutura do Projeto

```
mooc-optimization/
├── pipeline.ipynb         # preparação + features + LightGBM/gain[i,t,r]
├── optimization.ipynb     # Exato, Guloso, SA, GRASP
├── results.ipynb          # comparação e figuras
├── requirements.txt
└── data/                  # gerado automaticamente (não versionado)
    ├── logs_amostra.csv
    ├── enroll_amostra.csv
    ├── labels_amostra.csv
    ├── features.csv
    ├── gains.csv
    ├── gains.pkl
    └── resultados.pkl
```

## Tipos de Intervenção


| Código | Descrição                | Custo | Efetividade |
| ------ | ------------------------ | ----- | ----------- |
| R1     | Email de lembrete        | 1     | 0,15        |
| R2     | Contato com tutor        | 5     | 0,45        |
| R3     | Atividade de recuperação | 2     | 0,25        |


## Parâmetros do Problema

- Orçamento semanal (B): 20
- Máximo de intervenções por aluno (M): 3
- Horizonte (T): 10 semanas
- Instância exata: 50 alunos | Heurísticas: 300 alunos

## Autores

- Juliana Karla de C. Melo Baracho
- Márcio Henrique Vieira de Oliveira

UFAL / Instituto de Computação — PPGI