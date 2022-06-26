Wakatime Weekly Metrics

WakaTime dá uma ideia do tempo que você realmente codificou. .

Vamos configurar Dev Metrics para nosso perfil do GitHub em 4 etapas:

1. Vá para seu repositório actions username/username/actions -> New Workflow -> Set up this workflow;

2. Delete all default action content and copy/paste the following code to your workflow:

´´´
name: Waka Readme

on:
  workflow_dispatch:
  schedule:
    # Runs at 12am UTC
    - cron: "0 0 * * *"

jobs:
  update-readme:
    name: Update this repo's README
    runs-on: ubuntu-latest
    steps:
      - uses: athul/waka-readme@master
        with:
          WAKATIME_API_KEY: ${{ secrets.WAKATIME_API_KEY }}
          
          ´´´
          
3. Go to your Settings -> Secrets -> New Repository Secret e crie a new Secret com Name: WAKATIME_API_KEY and Value: Wakatime API Key. 
If you don’t know your WakaTime API Key, please go to Account Settings in WakaTime;

4. Add a comment to your README.md like this and click Run workflow:

´´´
<!--START_SECTION:waka-->
<!--END_SECTION:waka--> 
´´´
