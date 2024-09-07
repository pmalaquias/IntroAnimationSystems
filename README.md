# Intro Animation System

## Introduction

## Concepts

- **AnimationClip**: Dados de animação são armazenados como um ativo chamado Animation Clip . Um Animation Clip pode armazenar qualquer animação GameObject. Isso pode ser algo relativamente simples, como um salto de personagem ou uma luz piscando, bem como animações mais complexas, como uma animação de cutscene em um jogo.

- **Values (Valores)**: Os valores de um Animation Clip são geralmente, mas nem sempre, representados por Animation Curves. Animation Curves contêm informações sobre a maneira como o GameObject que você está animando muda. Animation Curves geralmente são um valor float (um valor que pode ser um inteiro ou um decimal) que pode mudar ao longo do tempo.

- **Binding (Ligaçoes)**: As ligações de um Animation Clip são uma maneira de conectar os valores a um campo específico de um GameObject ou componente. As ligações são compostas de duas coisas:
  
  1. O caminho através da Hierarquia para o componente Transform do GameObject
  2. O caminho desse componente Transform para um campo específico

- **Curves (Curvas)**: Curvas são a maneira como os valores de um Animation Clip são armazenados. Uma Animation Curve é um conjunto de Keyframes que representam a mudança de um valor ao longo do tempo. Por exemplo, uma Animation Curve pode ser usada para representar a mudança de posição de um GameObject ao longo do tempo.

- **Keyframes**: Keyframes são pontos de dados em uma Animation Curve. Eles são usados para definir o valor de um Animation Curve em um determinado ponto no tempo. Keyframes são compostos de um tempo e um valor.

- **Animation Blending**: A mistura de animações é o processo de combinar duas ou mais animações para criar uma nova animação. Isso é feito ajustando os pesos das animações individuais para que elas se misturem suavemente. A mistura de animações é usado para criar transições suaves entre diferentes animações.

- **Animator Controller**: O Animator Controller é um ativo que controla a lógica de animação de um GameObject. Ele contém uma série de estados e transições que definem como o GameObject deve se comportar em diferentes situações. O Animator Controller é usado para controlar a reprodução de Animation Clips e para definir como as animações devem ser misturadas.

- **Modo Dopesheet**: é uma visualização condensada onde apenas os quadros-chave em si são mostrados. Essa visualização é útil quando você quer ver como os quadros-chave são dispostos, ou quando os quadros-chave representam referências de objeto em vez de valores flutuantes. Isso é comum em animação 2D, quando diferentes sprites são trocados com cada quadro-chave

- **Modo Curvas**: é uma visualização detalhada que mostra todas as curvas de animação em um Animation Clip. Isso é útil quando você deseja ajustar os valores de uma curva de animação ou ver como as curvas de animação se comparam umas às outras.

- **Configurações predefinidas de um keyframe**: Há uma série de predefinições no Unity que tornam um pouco mais fácil obter a Curva de Animação que você deseja.
  - **Clamped Auto**: Isso significa que a Curva de Animação não ultrapassará o valor do quadro-chave e se aproximará dele suavemente.
  - **Auto**:  Esta é uma configuração legada. A menos que você esteja lidando com Animation Clips criados no Unity 3.x, use Clamped Auto em vez disso.
  - **Free Smooth**: esta configuração é a melhor maneira de obter uma curva suave.
    - **Flat**: Esta é uma variação do Free Smooth onde as tangentes são exatamente horizontais.
  - **Broken**: Isso significa que as tangentes esquerda e direita não são paralelas e apontam em direções independentes.
    - **Free**: Esta é a opção usual para tangentes quebradas.
    - **Linear**: Esta é uma variação de Broken que significa que as tangentes tentarão criar uma linha reta conforme a Animation Curve se aproxima do keyframe. Se as tangentes vizinhas forem ambas lineares, a Animation Curve será uma linha reta entre os keyframes.
    - **Constant**: Esta é uma variação de Quebrado, onde a Curva de Animação tem um valor igual ao quadro-chave anterior até o próximo quadro-chave, momento em que assume o valor desse quadro-chave.
  - **Weighted**: Você pode aplicar esta configuração além de qualquer outra configuração. Ela permite que o comprimento das tangentes seja ajustado, dando a você mais controle sobre as Curvas de Animação.

- **Baking animations**:  Isso determina se as animações importadas como cinemática inversa (IK) ou dados de simulação devem ser convertidas em cinemática direta (FK) por meio de um processo chamado baking .
Os clipes de animação armazenam seus dados em um formato FK, o que significa que os modelos importados com dados IK devem ser preparados para converter os dados de IK para FK.

- **Resampling Animation Curves**: Esta configuração determina se as animações importadas com ângulos de Euler para suas rotações devem ter esses ângulos convertidos para ângulos de quaternion.
Como regra geral, você deve reamostrar todas as animações que são importadas com ângulos de euler. A única exceção é se você estiver tendo problemas com a conversão, por exemplo, se uma animação fizer uma rotação maior que 180 graus entre os quadros.  

- **Rigs**: Rigs são uma maneira de definir a estrutura do modelo que está sendo importado e são usados ​​para definir como as animações são reproduzidas. Neste tutorial, você aprenderá sobre Tipos de Animação e criará e configurará um ativo Avatar para um Rig Genérico.

## Fundamentos da animação de modelos

Os modelos podem conter muitos triângulos para que cada um deles seja movido individualmente. Quanto maior a definição de um modelo, maior o número de triângulos. Em vez de mover cada triângulo individualmente durante a animação, os modelos são **skinned** antes de serem animados.

Skinning dá a cada um dos vértices que compõem os triângulos uma dependência de um **'bone'**. Este bone é então movido usando dados de animação e os vértices associados descobrem onde eles devem estar com base na posição e rotação do bone.

### Cinemática para direta e inversa

Transforms têm uma estrutura hierárquica. Isso significa que Transforms filhos se movem em relação aos pais. O mesmo vale para bones.
Por exemplo, a posição de um osso da mão dependeria da posição de um osso do antebraço. Isso, por sua vez, dependeria da posição de um osso do braço, e assim por diante.
Essa dependência é conhecida como **forward kinematics** (FK) e é comumente usada para animação, pois você pode definir as propriedades de posição e rotação como desejar, para obter a animação geral desejada.

Outra técnica para animação é chamada de **cinemática inversa** (IK). É onde o final de uma cadeia de ossos tem sua posição ou rotação definida, e então as posições e rotações dos ossos mais acima na cadeia são definidas por meio de um algoritmo para acomodar a posição e a rotação do osso final.
A cinemática inversa pode ser usada para criar animações no software DCC, que podem então ser importadas para o Unity. Ela também pode ser usada para animação em tempo de execução no Unity.

## Otimizando o tamanho da animação

A configuração **Animation Compression** se refere a como o tamanho da animação, tanto no disco quanto na memória, pode ser reduzido fazendo aproximações do arquivo importado original. Você pode selecionar entre as seguintes opções:

- **Off**: exibe a animação exatamente como foi criada, sem aproximações.

- **Keyframe Reduction**: Alguns Keyframes com valores similares serão removidos para reduzir a quantidade de memória que o Animation Clip ocupa no tempo de execução. Isso também afetará a animação resultante. Se você selecionar essa configuração, obterá opções adicionais para a quantidade de erro permitida na redução.

- **Optimal**: Isso fará com que o tamanho da animação seja o menor possível, dadas as configurações escolhidas para erro.
