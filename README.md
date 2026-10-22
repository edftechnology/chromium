# Como instalar/configurar/usar o `Chromium` no `Linux Ubuntu`

## Resumo

Guia para instalar e iniciar o navegador `Chromium` no `Linux Ubuntu` pelo `Terminal Emulator`, usando o pacote `chromium-browser` dos repositórios oficiais do `Ubuntu`. Nas versões atuais, esse pacote `apt` é de transição e instala o `Chromium` como `Snap`.

## _Abstract_

_A guide to install and launch the `Chromium` browser on `Linux Ubuntu` through the `Terminal Emulator`, using Ubuntu's official `chromium-browser` package. On current releases, this `apt` package is transitional and installs `Chromium` as a `Snap`._

## Descrição

### `Chromium`

O `Chromium` é um navegador de código aberto que serve de base para diversos navegadores. No `Ubuntu`, o pacote `chromium-browser` dos repositórios oficiais é um pacote de transição para o `Snap`; portanto, instalar com `apt` não significa instalar um navegador empacotado integralmente como `.deb`.

## Pré-requisitos

- Permissão para usar `sudo`
- Repositórios oficiais do `Ubuntu` habilitados, incluindo `universe`
- Conexão com a internet
- `apt` funcional para instalar o pacote de transição `chromium-browser`
- Serviço `snapd` ativo para instalar e executar o navegador


## 1. Abrir o `Terminal Emulator`

1. Abrir o `Terminal Emulator`. Você pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```


2. Certifique-se de que seu sistema esteja limpo e atualizado.

    2.1 Limpar o `cache` do gerenciador de pacotes `apt`. Especificamente, ele remove todos os arquivos de pacotes (`.deb`) baixados pelo `apt` e armazenados em `/var/cache/apt/archives/`. Digite o seguinte comando:

    ```bash
    sudo apt clean
    ```

    2.2 Remover pacotes `.deb` antigos ou duplicados do `cache` local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando:

    ```bash
    sudo apt autoclean
    ```

    2.3 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando:

    ```bash
    sudo apt autoremove -y
    ```

    2.4 Buscar as atualizações disponíveis para os pacotes que estão instalados em seu sistema. Digite o seguinte comando e pressione `Enter`:

    ```bash
    sudo apt update
    ```

    2.5 **Corrigir pacotes quebrados**: Isso atualizará a lista de pacotes disponíveis e tentará corrigir pacotes quebrados ou com dependências ausentes:

    ```bash
    sudo apt --fix-broken install
    ```

    2.6 Limpar o `cache` do gerenciador de pacotes `apt` novamente:

    ```bash
    sudo apt clean
    ```

    2.7 Para ver a lista de pacotes a serem atualizados, digite o seguinte comando e pressione `Enter`:

    ```bash
    sudo apt list --upgradable
    ```

    2.8 Realmente atualizar os pacotes instalados para as suas versões mais recentes, com base na última vez que você executou `sudo apt update`. Digite o seguinte comando e pressione `Enter`:

    ```bash
    sudo apt full-upgrade -y
    ```


## 3. Instalar o `Chromium` via `apt`

No `Ubuntu 22.04` e em versões atuais, `chromium-browser` é um pacote de transição: o navegador propriamente dito é instalado como `Snap`.

1. Habilitar `universe` e atualizar a lista de pacotes:

    ```bash
    sudo add-apt-repository universe
    sudo apt update
    ```

2. Instalar o pacote de transição pelo `apt`:

    ```bash
    sudo apt install chromium-browser
    ```

3. Instalar o navegador pelo `Snap`. O comando `snap install` não aceita a opção `-y`:

    ```bash
    sudo snap install chromium
    ```

4. Confirmar a instalação:

    ```bash
    snap list chromium
    chromium --version
    ```

A instalação pode levar alguns minutos para baixar e configurar o pacote.


## 4. Executar o `Chromium`

1. Iniciar o navegador pelo comando:

    ```bash
    chromium
    ```

2. Também é possível abrir o `Chromium` pelo menu de aplicativos do `Ubuntu`.

3. Para conferir a versão instalada:

    ```bash
    chromium --version
    snap list chromium
    ```


## 5. Atualizar ou remover o `Chromium`

O `Snap` atualiza os aplicativos automaticamente. Para solicitar a atualização manualmente:

    ```bash
    sudo snap refresh chromium
    ```

Para remover o navegador:

    ```bash
    sudo snap remove chromium
    ```

O pacote `chromium-browser` do `apt` é apenas a ponte de transição; a remoção do aplicativo é feita pelo `snap`.

## 6. Solução de problemas

1. Se `sudo apt update` falhar com erros indicando que não consegue abrir arquivos ou renomear arquivos em `/var/lib/apt/lists/partial`, recrie o diretório de índices temporários com as permissões esperadas e tente atualizar novamente:

    ```bash
    sudo install -d -o _apt -g root -m 700 /var/lib/apt/lists/partial
    sudo apt update
    ```

2. Se a instalação via `apt` falhar porque não há candidato para `chromium-browser`, confirme que `universe` está habilitado e repita a atualização dos índices:

    ```bash
    sudo add-apt-repository universe
    sudo apt update
    apt policy chromium-browser
    ```

3. Se o `Snap` não instalar ou o comando não responder, confirme que `snapd` está ativo e consulte o estado da instalação:

    ```bash
    systemctl status snapd
    snap changes
    sudo systemctl start snapd
    ```


## Compatibilidade

- O procedimento se aplica às versões do `Ubuntu` cujos repositórios disponibilizam `chromium-browser`.
- Em versões atuais, o pacote `apt` é transitório e entrega o navegador como `Snap`; requer `snapd`.
- A disponibilidade e a versão podem variar conforme a versão do `Ubuntu` e a arquitetura. Consulte o catálogo oficial de pacotes antes de instalar.

## Licença

Este repositório contém um tutorial de instalação; consulte `LICENSE.txt` para os termos aplicáveis ao conteúdo.

## Contato e suporte

Para dúvidas sobre o navegador, consulte o projeto oficial do `Chromium` e a documentação da sua versão do `Linux Ubuntu`.

## Referências

[1] OPENAI.
**Instalar o `chromium` no `linux ubuntu` pelo `terminal emulator`**.
Disponível em: <https://chatgpt.com/g/g-p-6980caf949648191ad6acfcdbe590f9e-instalar/c/6ad96d91-b0e8-83e8-ac88-6f29067d663e>.
ChatGPT.
Acessado em: 21/10/2026.

[2] UBUNTU DEVELOPERS.
**Pacote `chromium-browser` no `Ubuntu`**.
Disponível em: <https://packages.ubuntu.com/chromium-browser>.
Ubuntu Packages.
Acessado em: 21/10/2026.

[3] UBUNTU.
**Transição do `Chromium` no `Ubuntu` de `deb` para `Snap`**.
Disponível em: <https://ubuntu.com/blog/chromium-in-ubuntu-deb-to-snap-transition>.
Ubuntu.
Acessado em: 21/10/2026.

[4] THE CHROMIUM PROJECT.
**Projeto `Chromium`**.
Disponível em: <https://www.chromium.org/>.
Chromium Project.
Acessado em: 21/10/2026.
