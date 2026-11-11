<div align="center">

# crop & weed detection

**Visão computacional aplicada à agricultura**

Detecção de plantas cultivadas e plantas daninhas com YOLO e Python.

Projeto acadêmico desenvolvido no contexto do FarmTech360, na FIAP.

</div>

## O projeto

O detector identifica duas classes em imagens agrícolas, `crop` (planta cultivada) e `weed` (planta daninha). A proposta é apoiar a inspeção visual de áreas de cultivo, destacando as regiões detectadas e apresentando a quantidade de ocorrências por classe.

Este repositório apresenta minha contribuição de visão computacional ao FarmTech360, desenvolvido em equipe. O notebook reúne dois experimentos com modelos treinados separadamente e resultados de teste registrados.

[**Explorar o notebook**](notebooks/FarmTech360_YOLO.ipynb) · [**Abrir no Google Colab**](https://colab.research.google.com/github/weirdnessbemygod/yolo-crop-weed-detection/blob/main/notebooks/FarmTech360_YOLO.ipynb)

## Resultados registrados

| Experimento | Imagens de teste | Precisão | Recall | mAP@50 | mAP@50–95 |
| --- | ---: | ---: | ---: | ---: | ---: |
| Dataset inicial | 130 | 80,8% | 78,2% | **84,8%** | 55,1% |
| CornWeed | 1.054 | 82,2% | 83,3% | **83,3%** | 50,1% |

Os valores foram extraídos das saídas de teste do notebook. mAP mede a qualidade das detecções e não representa uma porcentagem geral de acerto. Os experimentos usam bases e divisões diferentes, portanto esses valores não constituem uma comparação controlada entre modelos.

## Minha contribuição

- Treinamento e avaliação de um detector YOLO com imagens agrícolas anotadas.
- Execução do treinamento no Google Colab.
- Integração do detector à interface Streamlit do FarmTech360.
- Exibição de imagens anotadas e contagem de detecções por classe.
- Organização do fluxo de trabalho em notebook e versionamento com Git e GitHub.

## Dados utilizados

O primeiro experimento utiliza **1.300 imagens**, separadas em treino, validação e teste.

| Partição | Imagens |
| --- | ---: |
| Treino | 1.040 |
| Validação | 130 |
| Teste | 130 |
| **Total** | **1.300** |

| ID | Classe | Descrição |
| --- | --- | --- |
| 0 | `crop` | Planta cultivada |
| 1 | `weed` | Planta daninha |

As anotações delimitam os objetos com caixas retangulares no formato YOLO. O conjunto de teste fica reservado para avaliar o modelo em imagens separadas do treinamento.

O segundo experimento utiliza o **CornWeed**, com 2.015 imagens de treino, 505 de validação e 1.054 de teste. Os rótulos originais foram convertidos para `0 = crop` (milho) e `1 = weed`. O notebook inclui inspeção das anotações, auditoria de duplicatas e análise de similaridade visual.

A separação do CornWeed considera sequências e datas de aquisição, mas a independência espacial não foi comprovada. Foram encontrados quatro pares visualmente semelhantes entre treino e validação pelo critério pHash utilizado. Esses limites devem acompanhar a interpretação dos resultados.

Fonte do CornWeed e acesso aos metadados de autoria e licença registrados no notebook: [Zenodo, DOI 10.5281/zenodo.7961764](https://zenodo.org/records/7961764). As imagens do dataset não estão incluídas neste repositório.

## Configuração dos experimentos

| Parâmetro | Dataset inicial | CornWeed |
| --- | --- | --- |
| Modelo inicial declarado | YOLOv8n pré-treinado | YOLOv8n pré-treinado |
| Épocas | 20 | Até 30, encerrado na 26 por early stopping |
| Tamanho de imagem | 512 | 640 |
| Batch | 8 | 8 |
| Seed | 42 | 42 |
| GPU da execução registrada | Tesla T4 | Tesla T4 |

## Tecnologias

| Ferramenta | Aplicação no projeto |
| --- | --- |
| Python | Execução do fluxo de visão computacional |
| YOLO / Ultralytics | Treinamento e detecção de objetos |
| Google Colab | Ambiente de treinamento com GPU |
| Streamlit | Interface para analisar imagens |
| Git e GitHub | Versionamento do trabalho |

## Da imagem à detecção

1. O usuário envia uma imagem agrícola ao aplicativo.
2. O modelo detecta regiões das classes `crop` e `weed`.
3. A interface apresenta a imagem com as caixas e os rótulos.
4. As contagens ajudam a localizar ocorrências para inspeção.

O desempenho depende das condições da imagem e da semelhança com os dados utilizados no treinamento.

## Conteúdo do portfólio

| Material | Situação |
| --- | --- |
| Apresentação do projeto | Disponível neste README |
| Notebook de treinamento e avaliação | [Disponível](notebooks/FarmTech360_YOLO.ipynb) |
| Exemplos de imagens com detecções | A adicionar |
| Métricas e configurações dos experimentos | Disponíveis neste README e nas saídas do notebook |
| Instruções de execução e acesso aos pesos | A adicionar |

## Como explorar e executar

1. Consulte as etapas e os resultados no [notebook](notebooks/FarmTech360_YOLO.ipynb).
2. Para executar, abra no Colab e selecione um ambiente com GPU.
3. O experimento inicial requer o `Dataset.zip` original, contendo `datasets/weed_crop_cc0`. Esse arquivo deve ser fornecido pelo usuário.
4. O experimento CornWeed pode ser iniciado em uma sessão própria a partir de sua seção de inspeção. A primeira célula dessa seção instala as dependências, e as seguintes baixam os dados e verificam o checksum.
5. Execute as células em ordem dentro do experimento escolhido e baixe os arquivos gerados antes de encerrar a sessão.

A edição publicada conserva resultados textuais selecionados da execução original. Foram removidos widgets, imagens embutidas e logs extensos para facilitar a leitura. Os caminhos com datas fixas foram substituídos por variáveis da sessão. O notebook foi verificado como JSON e teve a sintaxe Python inspecionada, mas esta edição não foi reexecutada com GPU.

## Contexto e autoria

**Beatriz Barreto Pinto** · estudante de Inteligência Artificial na FIAP.

O FarmTech360 é um projeto acadêmico em equipe. Este portfólio destaca minha participação no componente de visão computacional. A origem dos dados e as condições de uso dos arquivos serão documentadas junto aos materiais publicados.
