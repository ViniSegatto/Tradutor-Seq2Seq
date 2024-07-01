# Tradutor Seq2Seq com Mecanismo de Atenção

## Visão Geral

Este projeto tem como objetivo desenvolver um modelo de tradução automática do português para o inglês usando uma rede neural Seq2Seq aprimorada com um mecanismo de atenção. A rede Seq2Seq, também conhecida como rede codificadora-decodificadora, é uma arquitetura poderosa para lidar com tarefas de sequência, como tradução automática, onde a ordem das palavras é importante. O mecanismo de atenção permite que o modelo se concentre em partes específicas da entrada durante o processo de tradução, resultando em resultados mais precisos e fluentes.

## Introdução
Este projeto envolve a construção de um modelo de tradução automática que traduz sentenças do português para o inglês. O modelo utiliza uma arquitetura de rede neural Seq2Seq com um mecanismo de atenção, implementado usando PyTorch.

## Dados
O conjunto de dados utilizado neste projeto consiste em pares de sentenças em português e inglês, obtidos de tatoeba.org. Cada par de sentenças está alinhado, e o conjunto de dados foi pré-processado para facilitar o treinamento e a avaliação do modelo.

## Informações do Conjunto de Dados
* Número de Entradas: 193.632
* Colunas:
   * Go.: Sentenças em inglês.
   * Vai.: Sentenças em português.
   * Fonte: Atribuição da fonte das sentenças.

 ## Dicionário de Dados
 	
| Coluna  | Descrição |
| ------------- | ------------- |
| Go.  | Sentenças em inglês  |
| Vai.  | Sentenças em português  |
| Fonte  | Atribuição da fonte das traduções  |

## Arquitetura do Modelo
O modelo consiste em duas partes principais:

1. Codificador (Encoder): Uma RNN que processa a sentença de entrada e gera uma representação do estado oculto.
2. Decodificador com Atenção (Attention Decoder): Uma RNN que usa o estado oculto do codificador e um mecanismo de atenção para gerar a sentença traduzida.
   
## Codificador
O codificador usa uma camada de embedding seguida por uma GRU (Gated Recurrent Unit) para processar a sentença de entrada.

## Decodificador com Atenção
O decodificador também usa uma camada de embedding e uma GRU, mas inclui um mecanismo de atenção que ajuda a focar em partes relevantes da sentença de entrada durante a tradução.

## Treinamento
O processo de treinamento envolve os seguintes passos:

1. Preparação dos Dados: Carregar e pré-processar o conjunto de dados.
2. Laço de Treinamento: Treinar iterativamente o modelo usando lotes de pares de sentenças.
3. Cálculo da Perda: Usar a perda de log-verossimilhança negativa para medir o desempenho do modelo.
4. Otimização: Atualizar os parâmetros do modelo usando o otimizador Adam.

Parâmetros de Treinamento
* Tamanho Oculto: 128
* Tamanho do Lote: 32
* Número de Épocas: 80
* Taxa de Aprendizado: 0,001

## Avaliação

A avaliação é semelhante ao treinamento, mas sem usar as saídas alvo. As previsões do modelo são alimentadas de volta para ele mesmo a cada passo. As saídas de atenção do modelo também são armazenadas para visualização posterior.

## Uso
Para usar o modelo para tradução, você pode inserir uma sentença em português, e o modelo fornecerá a tradução em inglês juntamente com as visualizações de atenção.

## Exemplo 

'''python

evaluateAndShowAttention('ele nao e tao alto quanto seu pai')
evaluateAndShowAttention('Eu estou muito feliz')

'''

## Resultados
O modelo alcança uma qualidade de tradução razoável após aproximadamente 40 minutos de treinamento em uma CPU. Abaixo estão alguns exemplos de traduções:

| Sentença em Português  | Tradução em Inglês |
| ------------- | ------------- |
| ele nao e tao alto quanto seu pai  | he is not as tall as his father  |
| eu estou muito feliz  | I am very happy  |


