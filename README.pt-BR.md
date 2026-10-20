# N64 USB Launcher (webOS)

Português · [English](README.md)

Aplicativo para TVs LG com webOS que procura ROMs de Nintendo 64 (`.z64`, `.n64`, `.v64`) e Game Boy Advance (`.gba`) em um pendrive ou na memória da TV e abre o [RetroArch](https://www.retroarch.com/) já carregando a ROM escolhida. Sem pendrive, ele também baixa a sua própria ROM por link (Dropbox, Google Drive ou link https direto).

> **Status: experimental.** Ainda não foi validado em todos os modelos de TV nem em todas as versões do webOS. Use por sua conta e risco.

## Aviso sobre ROMs

**Este projeto não inclui, distribui, hospeda nem indica onde baixar ROMs, BIOS, jogos ou qualquer material protegido por direitos autorais.**

- Use apenas ROMs que você obteve legalmente, por exemplo extraídas de cartuchos que você possui.
- Não peça ROMs nas issues e não envie links para elas. Esses pedidos serão ignorados ou removidos.
- As leis sobre cópias de segurança de jogos variam de país para país. Cabe a você conhecer e cumprir a lei local.

## O que ele faz

1. Procura arquivos de ROM de N64 no pendrive (`/tmp/usb`) e em `/media/internal`.
2. Mostra uma lista que você navega com o controle remoto da TV.
3. Ao escolher uma, executa o RetroArch com um core de N64 e a ROM selecionada.

O app **não é um emulador**. Ele é só um atalho: o emulador é o RetroArch, com um core libretro de N64, como o Mupen64Plus-Next.

## Requisitos

- TV LG com webOS **com acesso root** e o [Homebrew Channel](https://www.webosbrew.org/) instalado. Sem root, só o botão "abrir RetroArch" funciona.
- RetroArch para webOS instalado (id `com.retroarch.webos`).
- Um core de N64 compilado para ARM/webOS. Este projeto **não** distribui cores.
- Um pendrive com as suas ROMs (FAT32 ou exFAT é o mais seguro).

## Instalação

1. Na TV, abra o Homebrew Channel.
2. Vá em **Settings → Add repository**.
3. Digite: `https://ruubr337.github.io/n64-webos-repo/api/apps.json`
4. Procure **N64 USB Launcher** na lista e instale.

## Uso

Plugue o pendrive, abra o app, escolha a ROM e aperte OK.

| Tecla do controle remoto | Ação |
|---|---|
| Setas cima / baixo | Escolher a ROM |
| OK | Jogar |
| Vermelho | Procurar ROMs de novo |
| Verde | Abrir o RetroArch sem ROM |
| Amarelo | Liga/desliga o auto-iniciar: na próxima vez, abre a última ROM em 3 segundos (qualquer tecla cancela) |
| Azul | Baixar uma ROM por link |
| Voltar | Sair |

### Baixar uma ROM por link

Sem pendrive? Aperte **Azul**, digite o link público da **sua própria** ROM e aperte OK.

- **Dropbox:** compartilhe o arquivo ("qualquer pessoa com o link") e use esse link. O app troca para download direto sozinho.
- **Google Drive:** deixe o arquivo como "qualquer pessoa com o link" e use o link de compartilhamento.
- **Arquivos .zip:** são descompactados e a ROM de dentro é mantida (precisa do `unzip` na TV).
- **Digitar na TV é lento.** Encurte o link antes, com um encurtador como o tinyurl, e digite o link curto. Links curtos são seguidos automaticamente.
- Os arquivos ficam em `/media/developer/roms` e aparecem na lista. O app confere o conteúdo do arquivo para distinguir ROMs de N64 e GBA e recusa qualquer outra coisa (inclusive páginas web devolvidas por links privados).

O link precisa começar com `https://`. Baixe apenas arquivos que você tem direito de usar.

## Se algo falhar

- **Core não encontrado:** instale o core pelo RetroArch (Load Core → Download a Core) ou defina `CORE_PATH_N64` / `CORE_PATH_GBA` em `n64launcher.conf`, na pasta do app.
- **Download falha ou diz "página web":** o link não é público. Deixe o compartilhamento como "qualquer pessoa com o link".
- **Nenhuma ROM aparece:** confira o formato do pendrive e a extensão da ROM.
- O log do RetroArch fica em `/tmp/n64-usb-launcher.log` (via SSH).

## Riscos do root e afiliação

Obter root pode anular a garantia da TV, e atualizações podem remover o acesso. Este é um projeto independente, **sem afiliação** com Nintendo, LG, libretro/RetroArch ou webOS Homebrew Project.

## Licença

Copyright (c) 2026 ruubr337. Todos os direitos reservados.

Você pode instalar e usar o app para fins pessoais e não comerciais. Não é permitido redistribuir, modificar ou vender sem autorização por escrito. O software é fornecido "como está", sem garantias.

Este não é um software de código aberto. O RetroArch e os cores são projetos separados, com licenças próprias, e não fazem parte deste repositório.
