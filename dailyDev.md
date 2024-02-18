
# Adicionando manualmente o DevCard ao seu perfil do GitHub

<br>

A maneira mais fácil de adicionar seu DevCard ao seu perfil é visitando a página DevCard e gerando seu cartão. <br>
1 clique na sua imagem no lado direito <br>
2 DevCard <br>
3 Generate now <br>
4 podes escolher se queres na horizontal ou na vertical <br>
5 clique no lado direito em Embed e copie o código <br>

<br>

<img src="https://github.com/MGBrave/things-for-your-github-profile/blob/main/img/imagem1.png?raw=true"  width="400">

<br>

Vá até o arquivo README.md do seu perfil do GitHub e cole o código.
Se você salvar esse arquivo e visualizar seu perfil, deverá ver o DevCard em ação.

<br>

<img src="https://github.com/MGBrave/things-for-your-github-profile/blob/main/img/imagem2.png?raw=true"  width="400">

<br>

No entanto, há uma desvantagem nessa abordagem, ele não atualizará automaticamente. 

Isso significa que teremos que executar essa ação sempre que quisermos  obter o DevCard mais recente.

# Como usar Actions do GitHub para atualizar seu DevCard automaticamente

Clique no botão Actions no repositório do seu perfil e configure um novo fluxo de trabalho

<br>

<img src="https://github.com/MGBrave/things-for-your-github-profile/blob/main/img/imagem3.png?raw=true"  width="400">

<br>

A partir daí, ele criará um fluxo de trabalho básico que começará a modificar.

Alterar o nome do fluxo de trabalho para ‘DevCard’.

Então, queremos definir duas maneiras pelas quais nossa ação deve ser acionada, sendo a primeira se houver um empurrão no main.

O outro é um horário, que funciona como um cronjob e voltará a cada {x}.
No nosso caso, vamos executá-lo todas as noites às 00:00.

*Também observe como definimos permissões de gravação.

```permissions:
  contents: write

on:
  workflow_dispatch:
  push:
    branches:
      - main
  schedule:
    - cron: "0 0 * * *"
```
O workflow_dispatch informa a ação que pode ser executada manualmente na guia Actions.
Então, queremos criar um novo trabalho que execute a ação DevCard GitHub.
Precisamos definir uma variável para a nossa versão, que será o ID do DevCard que estamos buscando.

 ``` jobs:
  devcard:
    runs-on: ubuntu-latest
    steps:
      - name: devcard
        uses: dailydotdev/action-devcard@2.0.4
        with:
          devcard_id: ${{ secrets.DEVCARD_ID }}
```

Fazendo o arquivo total parecer com isso:

```
name: DevCard

permissions:
  contents: write

on:
  workflow_dispatch:
  push:
    branches:
      - main
  schedule:
    - cron: "0 0 * * *"

jobs:
  devcard:
    runs-on: ubuntu-latest
    steps:
      - name: devcard
        uses: dailydotdev/action-devcard@2.0.2
        with:
          devcard_id: ${{ secrets.DEVCARD_ID }}

```
A próxima coisa que precisamos fazer é buscar nosso ID DevCard e configurá-lo como um segredo neste repositório do GitHub.

Dirija-se ao Página DevCard e gere seu DevCard.

O ID que precisamos é a parte antes da parte .png.

<br>

<img src="https://github.com/MGBrave/things-for-your-github-profile/blob/main/img/imagem4.png?raw=true"  width="400">

<br>

Então, no exemplo acima, o URL é assim:

 ```
https://api.daily.dev/devcards/b2a0b896ef724e68a2364c727e8e9e6e.png?r=6mk

```
O que significa que nosso ID é b2a0b896ef724e68a2364c727e8e9e6e.

Agora podemos voltar ao GitHub e clicar na guia Configurações.
A partir daí, escolha a seção Segredo e gere um novo segredo.

<br>

<img src="https://github.com/MGBrave/things-for-your-github-profile/blob/main/img/imagem5.png?raw=true"  width="500">

 <br>
 
 Esse segredo deve ter o seguinte nome: DEVCARD_ID e o valor que acabamos de recuperar da imagem.

Agora podemos ir até a guia Ações e executar nosso fluxo de trabalho.
Depois que o fluxo de trabalho estiver concluído, você verá um ícone verde no seu fluxo de trabalho.

<br>

<img src="https://github.com/MGBrave/things-for-your-github-profile/blob/main/img/imagem6.png?raw=true"  width="500">

<br>

Volte para o seu repositório e você verá que há um novo arquivo chamado devcard.svg.

Tudo o que precisamos fazer agora é atualizar nosso arquivo README.md para usar esse arquivo gerado da seguinte maneira:

```
<a href="https://app.daily.dev/DailyDevTips"><img src="https://github.com/rebelchris/rebelchris/blob/master/devcard.svg" width="400" alt="Chris Bongers's Dev Card"/></a>

```
Onde você precisa modificar as partes href, rebelchris / rebelchris e alt para ser o nome do seu repositório.

E lá vai você! Agora você tem um DevCard atualizado automaticamente no seu perfil do GitHub.

# Mantenha sua Action do GitHub atualizada com o GitHub Dependabot
Se você optou pelo método de ação do GitHub, considere usar o Dependabot para esse repositório. Ele garantirá que você esteja sempre usando a versão mais recente de nossa Action do GitHub. Para ativar o Dependabot para este repositório, tudo o que você precisa fazer é adicionar um .github/dependabot.yml arquivo com os seguintes conteúdos.

```
version: 2
updates:
  # Maintain dependencies for GitHub Actions
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: "daily"
```

Imagens: Cris Bongers
