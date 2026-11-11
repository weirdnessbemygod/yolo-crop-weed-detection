<div align="center">

# animal vision

**Detecção de gatos e cachorros com YOLOv5**

Projeto acadêmico individual · Python · PyTorch · Visão computacional

</div>

## O projeto

Desenvolvi este estudo individual para explorar a identificação e a localização de gatos e cachorros em imagens. O trabalho reúne preparação de dados, anotação de caixas, dois treinamentos supervisionados, seleção de modelo por validação e avaliação em imagens reservadas para teste.

O nome **Animal Vision** foi adotado para a apresentação do portfólio. O cenário de monitoramento é ilustrativo.

[**Ver notebook e figuras**](notebooks/animal_detection.ipynb) · [**Abrir no Google Colab**](https://colab.research.google.com/github/weirdnessbemygod/yolo-crop-weed-detection/blob/main/notebooks/animal_detection.ipynb)

## O que fiz

- Preparei um conjunto de 80 imagens de gatos e cachorros.
- Anotei os objetos no Make Sense AI e organizei os rótulos no formato YOLO.
- Conferi a correspondência entre imagens, anotações e códigos das classes.
- Treinei YOLOv5s em experimentos independentes de 30 e 60 épocas.
- Selecionei os pesos pelo desempenho na validação e avaliei o modelo no teste.
- Analisei imagens com detecções, incluindo falhas de localização e de classe.
- Comparei de forma exploratória o detector customizado, os pesos COCO e uma CNN implementada em PyTorch.

## Dataset

| Conjunto | Gatos | Cachorros | Imagens |
| --- | ---: | ---: | ---: |
| Treino | 32 | 32 | 64 |
| Validação | 4 | 4 | 8 |
| Teste | 4 | 4 | 8 |
| **Total** | **40** | **40** | **80** |

Classes do detector customizado: **0 = gato** e **1 = cachorro**.

## Experimentos YOLOv5s

Ambos os treinamentos começaram com pesos pré-treinados, imagens de 640 pixels, batch 16 e seed 42. A execução registrada utilizou uma GPU Tesla T4.

A tabela abaixo corresponde à avaliação dos arquivos `best.pt` na validação.

| Treinamento | Precisão | Recall | mAP@0.5 | mAP@0.5:0.95 | Tempo do treino |
| --- | ---: | ---: | ---: | ---: | ---: |
| 30 épocas | 84,5% | 100% | 97,0% | 68,6% | 2,07 min |
| 60 épocas | 96,8% | 100% | 99,5% | 78,7% | 3,51 min |

O modelo de 60 épocas foi selecionado pelo mAP@0.5:0.95 na validação.

## Resultado final no teste

Avaliação do modelo selecionado em **8 imagens com 8 instâncias anotadas**.

| Classe | Precisão | Recall | mAP@0.5 | mAP@0.5:0.95 |
| --- | ---: | ---: | ---: | ---: |
| Gato | 95,5% | 75,0% | 91,2% | 59,8% |
| Cachorro | 71,7% | 100% | 99,5% | 82,1% |
| **Geral** | **83,6%** | **87,5%** | **95,3%** | **70,9%** |

mAP avalia detecção de objetos e não representa acurácia global de classificação. Os resultados foram extraídos das saídas registradas no notebook.

O painel de teste está disponível no notebook. A inspeção mostra um gato sem detecção e outro classificado como cachorro. Os exemplos tornam visíveis as limitações do modelo mesmo com um mAP elevado.

## Comparação complementar

| Abordagem | Tarefa e avaliação registrada | Resultado |
| --- | --- | --- |
| YOLOv5s customizado | Detecção com caixas, avaliada por mAP | mAP@0.5 de 95,3% |
| YOLOv5s pré-treinado no COCO | Identificação pela classe da detecção de maior confiança | 7 acertos em 8 imagens |
| CNN treinada do zero | Classificação global de imagem | 5 acertos em 8 imagens |

As avaliações têm critérios diferentes. Elas não constituem um ranking diretamente comparável. A avaliação do modelo COCO considera identificação de classe, sem medir a sobreposição das caixas.

A CNN utiliza três blocos convolucionais, camadas densas, dropout e otimizador Adam. Foi treinada por 25 épocas com as 64 imagens de treino.

## Executar

1. Abra o notebook no Colab com GPU ou em um ambiente Jupyter com PyTorch instalado.
2. Prepare a pasta `animal_vision_data` com a estrutura abaixo.
3. Execute as células em ordem. A primeira célula procura os dados no Colab, no Drive ou na pasta de execução local. Um caminho personalizado pode ser definido na variável de ambiente `ANIMAL_VISION_DATA`.
4. O notebook instala as dependências do repositório oficial do YOLOv5 e registra seu commit.
5. Ao terminar, salve os pesos, gráficos e relatórios produzidos.

| Caminho na pasta de dados | Conteúdo |
| --- | --- |
| `TREINO/` | 64 imagens |
| `VALIDAÇÃO/` | 8 imagens |
| `TESTE/` | 8 imagens |
| `rotulos_treino_corrigidos.zip` | Anotações de treino |
| `rotulos_validacao_corrigidos.zip` | Anotações de validação |
| `rotulos_teste_corrigidos.zip` | Anotações de teste |

Os arquivos de imagem e anotação devem ter nomes-base correspondentes, iniciados por `gato` ou `cachorro`, conforme a classe. Dataset e pesos devem ser fornecidos pelo usuário.

O commit do YOLOv5 registrado na execução original é `402e17ddf820996f51a191cbb798376e1144f069`. O procedimento de instalação do notebook clona o repositório oficial disponível no momento da execução, portanto uma nova instalação pode usar outra versão.

## Limitações e estado desta edição

- O teste possui apenas quatro imagens por classe. É necessário ampliar e diversificar os dados para investigar generalização.
- Os tempos foram medidos por rotinas diferentes e não constituem um benchmark controlado de latência ou FPS. A medição da CNN em GPU não usa sincronização explícita.
- As figuras e os resultados são da execução original enviada pela autora. As figuras foram compactadas para facilitar a leitura no GitHub.
- Esta edição adapta nomes, apresentação e configuração dos caminhos. O JSON e a sintaxe das células foram conferidos. O treinamento não foi reexecutado nesta revisão.

## Autoria

**Beatriz Barreto Pinto** · projeto acadêmico desenvolvido individualmente.

Esta apresentação usa identificação genérica para a atividade acadêmica e seu cenário de aplicação.
