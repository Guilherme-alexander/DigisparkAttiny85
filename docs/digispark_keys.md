# Códigos de Teclas e Modificadores para Digispark ATtiny85

Esta tabela pode ser útil se você estiver escrevendo código que simula pressionamentos de teclas ou ações através do **Digispark ATtiny85** (como um "teclado USB").

Aqui, fornecemos uma tabela com os principais **códigos de teclas** e **modificadores** que podem ser usados no **Digispark ATtiny85** com as bibliotecas **HID-Project** ou **HID-Keyboard** para emular entradas de teclado.

## Códigos de Teclas e Modificadores para Digispark ATtiny85 (Emulação de Teclado)

| **Ação**                  | **Código da Tecla**         |
|---------------------------|-----------------------------|  
| **Tecla A**               | `KEY_A`                     |
| **Tecla B**               | `KEY_B`                     |
| **Tecla C**               | `KEY_C`                     |
| **Tecla D**               | `KEY_D`                     |
| **Tecla E**               | `KEY_E`                     |
| **Tecla F**               | `KEY_F`                     |
| **Tecla G**               | `KEY_G`                     |
| **Tecla H**               | `KEY_H`                     |
| **Tecla I**               | `KEY_I`                     |
| **Tecla J**               | `KEY_J`                     |
| **Tecla K**               | `KEY_K`                     |
| **Tecla L**               | `KEY_L`                     |
| **Tecla M**               | `KEY_M`                     |
| **Tecla N**               | `KEY_N`                     |
| **Tecla O**               | `KEY_O`                     |
| **Tecla P**               | `KEY_P`                     |
| **Tecla Q**               | `KEY_Q`                     |
| **Tecla R**               | `KEY_R`                     |
| **Tecla S**               | `KEY_S`                     |
| **Tecla T**               | `KEY_T`                     |
| **Tecla U**               | `KEY_U`                     |
| **Tecla V**               | `KEY_V`                     |
| **Tecla W**               | `KEY_W`                     |
| **Tecla X**               | `KEY_X`                     |
| **Tecla Y**               | `KEY_Y`                     |
| **Tecla Z**               | `KEY_Z`                     |
| **Tecla 0**               | `KEY_0`                     |
| **Tecla 1**               | `KEY_1`                     |
| **Tecla 2**               | `KEY_2`                     |
| **Tecla 3**               | `KEY_3`                     |
| **Tecla 4**               | `KEY_4`                     |
| **Tecla 5**               | `KEY_5`                     |
| **Tecla 6**               | `KEY_6`                     |
| **Tecla 7**               | `KEY_7`                     |
| **Tecla 8**               | `KEY_8`                     |
| **Tecla 9**               | `KEY_9`                     |
| **Enter**                 | `KEY_RETURN`                |
| **Espaço**                | `KEY_SPACE`                 |
| **Backspace**             | `KEY_BACKSPACE`             |
| **Tab**                   | `KEY_TAB`                   |
| **Escape**                | `KEY_ESC`                   |
| **Shift**                 | `MOD_SHIFT`                 |
| **Control**               | `MOD_CONTROL`               |
| **Alt**                   | `MOD_ALT`                   |
| **GUI (Windows)**         | `MOD_GUI_LEFT`              |
| **GUI (Mac)**             | `MOD_GUI_RIGHT`             |
| **Caps Lock**             | `KEY_CAPS_LOCK`             |
| **F1**                    | `KEY_F1`                    |
| **F2**                    | `KEY_F2`                    |
| **F3**                    | `KEY_F3`                    |
| **F4**                    | `KEY_F4`                    |
| **F5**                    | `KEY_F5`                    |
| **F6**                    | `KEY_F6`                    |
| **F7**                    | `KEY_F7`                    |
| **F8**                    | `KEY_F8`                    |
| **F9**                    | `KEY_F9`                    |
| **F10**                   | `KEY_F10`                   |
| **F11**                   | `KEY_F11`                   |
| **F12**                   | `KEY_F12`                   |

### Modificadores Combinados

- **Shift + A**:  
  ```cpp
  Keyboard.press(MOD_SHIFT);
  Keyboard.press(KEY_A);
  Keyboard.releaseAll();
  ```
- **Ctrl + C**:  
  ```cpp
  Keyboard.press(MOD_CONTROL);
  Keyboard.press(KEY_C);
  Keyboard.releaseAll();
  ```
- **Alt + Tab**:  
  ```cpp
  Keyboard.press(MOD_ALT);
  Keyboard.press(KEY_TAB);
  Keyboard.releaseAll();
  ```
- **Shift + Enter**:  
  ```cpp
  Keyboard.press(MOD_SHIFT);
  Keyboard.press(KEY_RETURN);
  Keyboard.releaseAll();
  ```

### Observações:
- **MOD_SHIFT**, **MOD_CONTROL**, **MOD_ALT**, **MOD_GUI_LEFT**, **MOD_GUI_RIGHT** são **modificadores** que alteram o comportamento das teclas.
- A biblioteca **HID-Project** ou **HID-Keyboard** deve estar instalada na IDE para usar essas teclas.
- Esta tabela é usada principalmente para simular entrada de teclado no Digispark, sendo útil para projetos como automação de pressionamentos de teclas.

# Teclas Especiais para Digispark ATtiny85 (Emulação de Teclado)

Estas são as teclas de controle especiais que você pode emular usando o **Digispark ATtiny85** com as bibliotecas **HID-Project** ou **HID-Keyboard**. Estas teclas fornecem funcionalidades avançadas além das teclas alfanuméricas padrão.

### Teclas de Navegação

| **Ação**               | **Código da Tecla**         |
|--------------------------|-----------------------------|
| **Seta para Cima**       | `KEY_UP_ARROW`              |
| **Seta para Baixo**      | `KEY_DOWN_ARROW`            |
| **Seta para Esquerda**   | `KEY_LEFT_ARROW`            |
| **Seta para Direita**    | `KEY_RIGHT_ARROW`           |

### Teclas de Função Avançadas

| **Ação**               | **Código da Tecla**         |
|--------------------------|-----------------------------|
| **Break**                 | `KEY_BREAK`                 |
| **Pause**                 | `KEY_PAUSE`                 |
| **Print Screen**          | `KEY_PRINTSCREEN`           |
| **Scroll Lock**           | `KEY_SCROLL_LOCK`           |
| **Num Lock**              | `KEY_NUM_LOCK`              |

### Teclas de Controle do Sistema

| **Ação**               | **Código da Tecla**         |
|--------------------------|-----------------------------|
| **Caps Lock**             | `KEY_CAPS_LOCK`             |
| **Insert**                | `KEY_INSERT`                |
| **Home**                  | `KEY_HOME`                  |
| **End**                   | `KEY_END`                   |
| **Page Up**               | `KEY_PAGE_UP`               |
| **Page Down**             | `KEY_PAGE_DOWN`             |

### Exemplo de Uso

Você pode usar estas teclas especiais em seu código conforme mostrado nos exemplos abaixo:

#### Exemplo: Pressionando a tecla **Caps Lock**:
```cpp
Keyboard.press(KEY_CAPS_LOCK);
Keyboard.releaseAll();
```

# Funções do Mouse
Se você quiser usar o Digispark como um mouse USB (em vez de um teclado), você pode emular cliques e movimentos do mouse com as bibliotecas HID-Project ou HID-Mouse.

```cpp
#include <HID-Project.h>

void setup() {
  Mouse.begin();
}

void loop() {
  Mouse.move(10, 10);  // Move o mouse 10 pixels para a direita e 10 pixels para baixo
  delay(1000);
}
```

Exemplo: Movendo o cursor do mouse

```cpp
#include <HID-Project.h>

void setup() {
  Mouse.begin();
}

void loop() {
  Mouse.click(MOUSE_LEFT);  // Clica com o botão esquerdo do mouse
  delay(1000);
}
```
