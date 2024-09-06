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
