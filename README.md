# Classificação de Grãos de Café com Visão Computacional (YOLOv8)

Projeto acadêmico de detecção e classificação de grãos de café por maturidade
utilizando YOLOv8, desenvolvido na UNIFEI.

## Sobre o projeto

O modelo classifica grãos de café em 4 estágios de maturidade:

| ID | Classe |
|----|--------|
| 0 | Seco |
| 1 | Maduro |
| 2 | Semi maduro |
| 3 | Verde |

> As classes originais "Muito Maduro" e "Maduro" foram fundidas em uma única
> classe para reduzir ambiguidade e melhorar o desempenho do modelo.

## Pipeline

1. **Preparação dos dados** — descompactação e organização do dataset
2. **Análise exploratória** — visualização da distribuição original das 5 classes
3. **Fusão de classes** — mapeamento de 5 → 4 classes via `id_map`
4. **Undersampling** — remoção de 60% das imagens exclusivamente da classe "Verde"
5. **Data Augmentation offline** — geração de imagens sintéticas para balancear classes minoritárias (flip, brilho, rotação, saturação)
6. **Treinamento** — YOLOv8s com 50 épocas, early stopping, imagem 640px
7. **Avaliação** — métricas de precisão, recall e matriz de confusão

## Tecnologias

- Python
- YOLOv8 (Ultralytics)
- OpenCV
- Albumentations
- Google Colab (GPU Tesla T4)

## Como usar

1. Abra o notebook no Google Colab
2. Monte seu Google Drive e coloque o `coffee_dataset.zip` na raiz
3. Execute as células em ordem

## Resultados

O modelo foi avaliado com `model.val()` no conjunto de teste,
reportando precisão média (mP) e recall médio (mR) por classe.
