# Digispark ATtiny85 - Guia de Funcionalidade do Mouse

Este guia fornece instruções sobre como usar o **Digispark ATtiny85** para emular funcionalidades de mouse através da biblioteca **HID-Project**. Você aprenderá como simular várias ações do mouse como mover o cursor, clicar, rolar, arrastar e muito mais. Seja para construir scripts de automação, criar dispositivos de entrada personalizados ou apenas experimentar com dispositivos HID, este guia irá ajudá-lo a começar.

<br/>

## Pré-requisitos

Para usar a biblioteca **HID-Project** para emulação de mouse com o **Digispark ATtiny85**, você precisará instalar a biblioteca na sua IDE Arduino:

1. Abra a **IDE Arduino**.
2. Vá em **Sketch > Incluir Biblioteca > Gerenciar Bibliotecas...**.
3. Pesquise por "**HID-Project**" e clique em **Instalar**.

Após instalar a biblioteca, você estará pronto para começar a usar o Digispark ATtiny85 para emulação de mouse!

<br/>

## Operações Básicas do Mouse

A biblioteca **HID-Project** fornece várias funções para emular ações do mouse. Abaixo estão as funcionalidades principais que você pode usar com seu **Digispark ATtiny85**.

### 1. Movendo o Mouse

Você pode mover o cursor do mouse na tela usando a função `Mouse.move()`.

#### Sintaxe:
```cpp
Mouse.move(x, y, wheel);
```

- `x`: Movimento horizontal (positivo para direita, negativo para esquerda).
- `y`: Movimento vertical (positivo para baixo, negativo para cima).
- `wheel`: Movimento da roda de rolagem (positivo para cima, negativo para baixo).

#### Exemplo: Mover o Mouse 10 Pixels para a Direita e 10 Pixels para Baixo
```cpp
Mouse.move(10, 10, 0);  // Move o mouse na diagonal
```

<br/>

### 2. Simulando Cliques do Mouse

Você pode simular cliques do mouse com as funções `Mouse.click()`, `Mouse.press()` e `Mouse.release()`.

#### Sintaxe:
```cpp
Mouse.click(botao);
Mouse.press(botao);
Mouse.release(botao);
```

- `botao`: O botão que você deseja clicar. Valores possíveis:
  - `MOUSE_LEFT` (botão esquerdo)
  - `MOUSE_RIGHT` (botão direito)
  - `MOUSE_MIDDLE` (botão do meio)

#### Exemplo: Simular Clique com Botão Esquerdo do Mouse
```cpp
Mouse.click(MOUSE_LEFT);
```

#### Exemplo: Pressionar e Segurar o Botão Esquerdo do Mouse
```cpp
Mouse.press(MOUSE_LEFT);
delay(1000);  // Segura o botão por 1 segundo
Mouse.release(MOUSE_LEFT);
```

<br/>

### 3. Rolagem com o Mouse

Simule a rolagem da roda do mouse com a função `Mouse.scroll()`.

#### Sintaxe:
```cpp
Mouse.scroll(roda);
```

- `roda`: O número de unidades de rolagem (positivo para rolar para cima, negativo para rolar para baixo).

#### Exemplo: Rolar para Baixo
```cpp
Mouse.scroll(-1);  // Rola para baixo uma vez
```

#### Exemplo: Rolar para Cima
```cpp
Mouse.scroll(1);   // Rola para cima uma vez
```

<br/>

### 4. Movimento Rápido do Mouse

Você pode mover o mouse rapidamente usando valores maiores para `x` e `y`. O mouse se moverá suavemente com base na entrada fornecida.

#### Exemplo: Mover o Mouse 100 Pixels para a Direita e 50 Pixels para Baixo
```cpp
Mouse.move(100, 50, 0);  // Movimento rápido para a direita e baixo
```

<br/>

### 5. Arrastando com o Mouse

Para arrastar um item, você pressiona e segura um botão do mouse, move o mouse e depois solta o botão.

#### Exemplo: Arrastar um Item do Canto Superior Esquerdo para o Canto Inferior Direito
```cpp
Mouse.press(MOUSE_LEFT);     // Pressiona o botão esquerdo do mouse
Mouse.move(50, 50, 0);       // Move na diagonal
delay(500);                  // Aguarda 0.5 segundos
Mouse.move(100, 100, 0);     // Move mais na diagonal
Mouse.release(MOUSE_LEFT);   // Solta o botão esquerdo do mouse
```

<br/>

### 6. Simulando Movimento Diagonal

Simule movimentos diagonais ajustando ambas as coordenadas `x` e `y`.

#### Exemplo: Mover o Mouse na Diagonal (Direita e Baixo)
```cpp
Mouse.move(10, 10, 0);  // Move 10 pixels para a direita e para baixo
```

<br/>

### 7. Movimento Contínuo do Mouse

Crie movimentos contínuos ou repetitivos do mouse com um loop.

#### Exemplo: Mover o Mouse Continuamente para a Direita
```cpp
void loop() {
  Mouse.move(5, 0, 0);   // Move 5 pixels para a direita
  delay(100);             // Aguarda 100ms antes de mover novamente
}
```

<br/>

### 8. Controlando a Interface do Sistema com o Mouse

Use o mouse para automatizar ações da interface como clicar em ícones ou navegar em menus.

#### Exemplo: Clicar em uma Localização Específica da Tela
```cpp
Mouse.move(500, 300, 0);  // Move para a posição (500, 300) na tela
Mouse.click(MOUSE_LEFT);   // Clica o mouse nessa posição
```

<br/>

## Exemplo de Código - Combinando Mouse e Teclado

Este exemplo mostra como usar a emulação de mouse e teclado juntas, ideal para criar fluxos de trabalho automatizados.

```cpp
#include <HID-Project.h>

void setup() {
  Mouse.begin();     // Inicia a emulação do mouse
  Keyboard.begin();  // Inicia a emulação do teclado
  
  // Simula rolagem do mouse
  Mouse.scroll(1);   // Rola para cima
  
  delay(500);         // Aguarda meio segundo
  
  // Move o mouse para a direita
  Mouse.move(50, 0, 0);
  
  delay(500);         // Aguarda meio segundo
  
  // Simula clique com botão esquerdo do mouse
  Mouse.click(MOUSE_LEFT);
  
  delay(500);         // Aguarda meio segundo
  
  // Digita uma mensagem
  Keyboard.print("Olá, Digispark!");
  Keyboard.press(KEY_RETURN);
  Keyboard.releaseAll();
  
  Mouse.end();        // Finaliza a emulação do mouse
  Keyboard.end();     // Finaliza a emulação do teclado
}

void loop() {
  // Loop vazio, todas as ações estão no setup()
}
```

<br/>

## Observações e Dicas

- **Movimento Suave**: O movimento do mouse é geralmente suave e baseado nos valores de pixel que você fornece. Se você deseja movimentos muito rápidos ou grandes, ajuste os parâmetros `x`, `y` e `roda` conforme necessário.
  
- **Usando Delays**: É uma boa prática usar `delay()` entre as ações, especialmente quando você está simulando múltiplas entradas, para garantir que as ações sejam registradas corretamente.
  
- **Combinando Entradas**: Você pode combinar ações do teclado e do mouse para criar scripts de automação poderosos ou dispositivos de entrada personalizados. Por exemplo, você pode simular uma ação de arrastar e soltar, ou um atalho de teclado seguido por um clique do mouse.

<br/>

## Conclusão

Com o **Digispark ATtiny85** e a biblioteca **HID-Project**, você pode emular uma ampla gama de ações do mouse para seus projetos. Seja para automatizar tarefas de desktop, criar dispositivos de controle personalizados ou experimentar com entrada do mouse, estas funções lhe dão controle total sobre o mouse.

Explore e modifique os exemplos acima para atender às suas necessidades, e deixe sua criatividade fluir com as capacidades de emulação de mouse do Digispark ATtiny85!

Feliz programação! 🎮
