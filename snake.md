
## Github Snake

<br>
<br>
  
![Snake animation](https://github.com/martageraldo/martageraldo/blob/output/github-contribution-grid-snake.svg)

<br>

![Snake animation](https://raw.githubusercontent.com/Envoy-VC/Envoy-VC/output/github-contribution-grid-snake-dark.svg)

<br>
<br>
  
  
 | Nome |                    URL                          |
 |------|-------------------------------------------------| 
 |White Snake Animation|```![Snake animation](https://github.com/martageraldo/martageraldo/blob/output/github-contribution-grid-snake.svg) ```| 
 |Black Snake Animation|```![Snake animation](https://raw.githubusercontent.com/Envoy-VC/Envoy-VC/output/github-contribution-grid-snake-dark.svg) ```| 

Você poderá fazer o seu:

Para implementar ela, primeiro coloque o seguinte código no seu arquivo README.md:
<br>

```
![Snake animation](https://github.com/seu-usuário-aqui/seu-usuário-aqui/blob/output/github-contribution-grid-snake.svg)
```

Tome cuidado para colocar o seu nome de usuário do GitHub  correto onde diz `seu-usuario-aqui` seu para que seja demonstrado seu grid de contribuições, caso contrário, poderá dar erro.

Em seguida, vá em Actions e selecione set up a workflow yourself →

imagem1

E cole o seguinte código no editor de texto que irá abrir:
<!--

```
name: Generate Datas

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"
  workflow_dispatch:

jobs:
  build:
    name: Jobs to update datas
    runs-on: ubuntu-latest
    steps:
      # Snake Animation
      - uses: Platane/snk@master
        id: snake-gif
        with:
          github_user_name: seu-usuário-aqui
          svg_out_path: dist/github-contribution-grid-snake.svg

      - uses: crazy-max/ghaction-github-pages@v2.1.3
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }} 
          
          ```
-->
         
         
 Aqui, novamente tome cuidado para  colocar o seu nome de usuário do GitHub  correto onde diz `seu-usuario-aqui` seu para que seja demonstrado seu grid de contribuições, caso contrário, poderá dar erro.

E clique em **Start commit** e **Commit new file**:
 <br>
imagem
 <br>
 
 Concluído! A cada 12 horas a animação será atualizada, mas você pode rodar selecionando o arquivo yml e em seguida, **View runs**:
imagem

<br>
E rodar com **Run workflow**

imagem

<br>



