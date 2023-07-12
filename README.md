# Desafio-Redes-Neurais-Infinity
Desafio proposto pela aula de Redes Neurais na Instituição Infinity School!

### > Treinando um modelo de rede neural, para reconhecimento de imagem (Cachorro e Gato).

### > Foram utilizadas as bibliotecas: tensorflow, keras, ImageDataGenerator, VGG16, Model, Dense e GlobalAveragePooling2D do módulo tensorflow.keras.

### > Definimos as configurações para o treinamento do modelo, incluindo a largura e altura das imagens (img_width e img_height), o tamanho do lote (batch_size), os diretórios de treinamento e validação (train_data_dir e validation_data_dir) e o número de épocas (epochs).

### > O VGG16 é um modelo de rede neural convolucional (CNN) muito conhecido e eficaz, amplamente utilizado para tarefas de classificação de imagens. Nesta linha de código, estamos criando uma instância do modelo VGG16 como base para o nosso modelo de classificação de cachorros e gatos.

### > Weights='imagenet': Especificamos o conjunto de pesos a serem usados pelo modelo. O valor 'imagenet' indica que queremos carregar os pesos pré-treinados do modelo VGG16 treinado no conjunto de dados ImageNet. Esses pesos foram treinados em um conjunto enorme e diversificado de imagens e podem capturar características gerais úteis para tarefas de classificação de imagens.

### > include_top=False: Isso indica que não queremos incluir as camadas finais de classificação do VGG16, que são responsáveis por mapear as características aprendidas para as classes do conjunto de dados ImageNet original. Ao definir include_top=False, excluímos essas camadas finais e teremos a flexibilidade de adicionar nossas próprias camadas personalizadas para nossa tarefa de classificação de cachorros e gatos.

### > input_shape=(img_width, img_height, 3): Especificamos a forma das imagens de entrada que o modelo VGG16 espera receber. As dimensões (img_width, img_height) indicam o tamanho desejado para as imagens de entrada (150x150 pixels neste caso), e 3 representa os três canais de cor (vermelho, verde e azul - RGB). É importante fornecer imagens de entrada com a mesma forma definida aqui para garantir que o modelo funcione corretamente.

### > Congelamos as camadas do modelo pré-treinado definindo layer.trainable = False para cada camada no modelo.

### > Adicionamos novas camadas no topo do modelo. Primeiro, aplicamos um GlobalAveragePooling2D para reduzir as dimensões da saída. Em seguida, adicionamos uma camada Dense com 512 unidades e função de ativação ReLU. Por fim, adicionamos uma camada de saída Dense com 2 unidades (uma para cada classe - cachorro e gato) e função de ativação softmax para obter as probabilidades de cada classe.

### > Criamos o modelo final, especificando as entradas (inputs=base_model.input) e as saídas (outputs=predictions).

### > Compilamos o modelo usando o otimizador 'adam', a função de perda 'categorical_crossentropy' e a métrica 'accuracy' para avaliar o desempenho do modelo durante o treinamento.

### > Criamos geradores de dados para o treinamento e a validação usando ImageDataGenerator. Esses geradores aplicam várias transformações nas imagens, como redimensionamento, rotação, zoom e espelhamento horizontal, para enriquecer o conjunto de dados de treinamento e evitar overfitting.

### > O gerador de treinamento train_generator é criado a partir do diretório de treinamento, especificando o tamanho das imagens alvo, o tamanho do lote e o modo 'categorical' para tratar as classes como variáveis categóricas.

### > O gerador de validação validation_generator é criado de forma semelhante, mas a partir do diretório de validação.

### > Realizamos o ajuste fino do modelo chamando model.fit(), passando o gerador de treinamento, o número de épocas e o gerador de validação. Durante o treinamento, o modelo será ajustado para melhor se adequar ao conjunto de dados.

### > Após o treinamento, salvamos o modelo treinado em um arquivo chamado 'cachorro_gato_modelo_treinado.h5' usando model.save().

> **Esse código cria e treina um modelo baseado no VGG16 com camadas personalizadas para classificação de imagens de cachorro e gato. O ajuste fino é realizado para adaptar o modelo pré-treinado ao seu problema específico. Os geradores de dados são usados para fornecer lotes de imagens durante o treinamento, aplicando transformações para melhorar a diversidade dos dados.**





**Observações Finais** : O modelo criado teve um accuracy bem positiva, mas ele ainda não deve ser usado como o modelo ideal para reconhecimento dessas imagens. O motivo é que ele foi treinado em cima de uma base de dados pequena, e com certeza ao passar outras imagens pelo modelo, pode não reconhecer corretamente, pela falta de treinamento efetivo.

O intuito do desafio era apenas melhorar o código dado anteriormente pelo professor, então foram feitas modificações na base de dados para o treinamento, incluindo mais imagens na internet e mudando a biblioteca de Perceptron para Tensorflow.
