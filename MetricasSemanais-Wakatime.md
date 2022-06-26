# <img src="https://cdn-icons-png.flaticon.com/512/1340/1340003.png"  width="35"/> Wakatime Weekly Metrics

           
          

WakaTime dá uma ideia do tempo que você efetivamente codificou.

Para configurar as Dev Metrics no nosso perfil do GitHub devemos seguir as etapas seguintes:

* Entre no seu README, clique em  actions na parte superior,  depois em New Workflow que fica a esquerda, em seguida em Set up a workflow yourself, 

*  Exclua todo o conteúdo de ação padrão e copie/cole o código a seguir em seu workflow:

  <br> 

 ```
name: Waka Readme 

on:
  workflow_dispatch:
  schedule:
    # Runs at 12am UTC
    - cron: "0 0 * * *"

jobs:
  update-readme:<br>
    name: Update this repo's README
    runs-on: ubuntu-latest
    steps:
      - uses: athul/waka-readme@master
        with:
          WAKATIME_API_KEY: ${{ secrets.WAKATIME_API_KEY }}
   ```       
  <br>   
          
* Go to your `Settings => Secrets => New Repository Secret` e crie um novo Secret no menu a esquerda,  com o  Nome: ```WAKATIME_API_KEY```   e Value: ```Wakatime API Key```.  Se você não sabe ou não tem uma chave ``WakaTime API Key``, vá para o site <a href="https://wakatime.com/settings/account" target="_blank">Wakatime</a>  crie uma conta e gere uma chave. Posteriormente clique em Start commit.
<br>

* Entre no seu README.md adicione o comentário abaixo, clique em actions, clique no nome do seu README wakatime que você criou e que aparece a esquerda da tela, e em seguida click ``Run workflow:``

<br>

```
<!--START_SECTION:waka-->
<!--END_SECTION:waka--> 

```
<br>

No final ele ficará semelhante a imagem abaixo. <br>

![Wakatime](https://github.com/martageraldo/awesome-badges/blob/main/img/wakatimeimg.jpg?raw=true)

<br>


Referência:
<a href="https://github.com/Gapur" target="_blank" >Gapur</a>
