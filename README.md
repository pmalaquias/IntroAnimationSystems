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
