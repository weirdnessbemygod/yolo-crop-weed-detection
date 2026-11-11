<div align="center">

# crop & weed detection

**Visão computacional aplicada à agricultura**

Detecção de plantas cultivadas e plantas daninhas com YOLO e Python.

Projeto acadêmico desenvolvido no contexto do FarmTech360, na FIAP.

</div>

## O projeto

O detector identifica duas classes em imagens agrícolas, `crop` (planta cultivada) e `weed` (planta daninha). A proposta é apoiar a inspeção visual de áreas de cultivo, destacando as regiões detectadas e apresentando a quantidade de ocorrências por classe.

Este repositório apresenta minha contribuição de visão computacional ao FarmTech360, desenvolvido em equipe. A organização dos arquivos para este portfólio está em andamento.

## Minha contribuição

- Treinamento e avaliação de um detector YOLO com imagens agrícolas anotadas.
- Execução do treinamento no Google Colab.
- Integração do detector à interface Streamlit do FarmTech360.
- Exibição de imagens anotadas e contagem de detecções por classe.
- Organização do fluxo de trabalho em notebook e versionamento com Git e GitHub.

## Dados utilizados

O conjunto utilizado no projeto reúne **1.300 imagens**, separadas em treino, validação e teste.

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
| Notebook de treinamento e avaliação | A adicionar |
| Exemplos de imagens com detecções | A adicionar |
| Métricas do modelo e configuração do teste | A adicionar |
| Instruções de execução e acesso aos pesos | A adicionar |

## Contexto e autoria

**Beatriz Barreto Pinto** · estudante de Inteligência Artificial na FIAP.

O FarmTech360 é um projeto acadêmico em equipe. Este portfólio destaca minha participação no componente de visão computacional. A origem dos dados e as condições de uso dos arquivos serão documentadas junto aos materiais publicados.
