name: generate animation

on:
  # run automatically every 24 hours
  schedule:
    - cron: "0 */24 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master
    
  

jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
          
          
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

#
[![E-mail](https://img.shields.io/badge/-Email-000?style=for-the-badge&logo=microsoft-outlook&logoColor=FF00F6&color:FFF)](mailto:fabioantoniosa03@gmail.com)
[![LinkedIn](https://img.shields.io/badge/-LinkedIn-000?style=for-the-badge&logo=linkedin&logoColor=FF00F6&color:FFF)]([https://www.linkedin.com/in/f%C3%A1bio-ant%C3%B4nio/)
#

<div style="text-align: center;" align="center">
  <h3>* GitHub Stats *</h3>
  <br>
  <img src="https://github-readme-stats-git-masterrstaa-rickstaa.vercel.app/api?username=mari4souza&hide_title=true&show_icons=true&include_all_commits=false&count_private=true&line_height=25&hide=issues&bg_color=000&title_color=FF00F6&text_color=FFF&border_radius=3&border_color=36123c&icon_color=FF00F6&theme=jolly" alt="GitHub stats">

  <a href="https://github.com/mari4souza/github-readme-stats">
    <img src="https://github-readme-stats-git-masterrstaa-rickstaa.vercel.app/api/top-langs/?username=mari4souza&line_height=10&card_width=290&layout=compact&hide_title=false&count_private=true&langs_count=4&show_icons=true&title_color=FF00F6&hide=html,css&bg_color=000&text_color=8B8B8B&border_radius=3&border_color=561760&count_private=true" alt="Most Used Languages">
  </a>
</div>


#

<picture align="center">
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/mari4souza/mari4souza/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/mari4souza/mari4souza/output/github-contribution-grid-snake-dark.svg">
  <img align="center" alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/mari4souza/mari4souza/output/github-contribution-grid-snake.svg">
</picture>
