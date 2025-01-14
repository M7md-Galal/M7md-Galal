<h1 align="center">Hi , I'm Mohamed Galal <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="35"></h1>
<p align="center">
  <a href="https://github.com/DenverCoder1/readme-typing-svg"><img src="https://readme-typing-svg.herokuapp.com?font=Time+New+Roman&color=%23C8BE25&size=25&center=true&vCenter=true&width=600&height=100&lines=Software+Engineer;Computer+Science+Student;Always+learning+new+things"></a>
</p>


<br>
	
## <picture><img src = "https://github.com/7oSkaaa/7oSkaaa/blob/main/Images/about_me.gif?raw=true" width = 50px></picture> About me

<picture> <img align="right" src="https://github.com/7oSkaaa/7oSkaaa/blob/main/Images/Right_Side.gif?raw=true" width = 250px></picture>

<br><br>

- :school: I am a `Student` at [Faculty of Computers & Informatics Science](http://www.fci.zu.edu.eg/faculty/default) at [Zagazig University](https://www.zu.edu.eg/).
- :technologist: I love using Software as a solution for every `Problem`.
- :computer: I am a Problem Solver at `Codeforces`, `Leetcode`.
- :student: I’m currently learning `Computer Science` and `Software Engineering`.
- :nerd_face: Always `learning new things`.
- :thinking: I’m currently open for a new `job opportunity`, this is [MY RESUME]().
<br>


## <picture> <img src="https://github.com/7oSkaaa/7oSkaaa/blob/main/Images/competitive_programming_profile.png?raw=true" width=40> </picture> My Problem Solving Profiles

<p align="center">
  <a href="https://codeforces.com/profile/M7md-Galal"><img src="https://img.icons8.com/external-tal-revivo-shadow-tal-revivo/50/000000/external-codeforces-programming-competitions-and-contests-programming-community-logo-shadow-tal-revivo.png" alt="Code Forces"/></a>
  <a href="https://leetcode.com/u/mohamed-galal/"><img src="https://img.icons8.com/external-tal-revivo-shadow-tal-revivo/50/000000/external-level-up-your-coding-skills-and-quickly-land-a-job-logo-shadow-tal-revivo.png" alt="LeetCode"/></a>
</p>

## <picture> <img src="https://github.com/7oSkaaa/7oSkaaa/blob/main/Images/Connect-with-me.gif?raw=true" width="100px"> </picture> Connect with me
<p align="center">
	<a href="mailto:mohamed754f@gmail.com"><img img src="https://img.shields.io/badge/gmail-%23EA4335.svg?style=plastic&logo=gmail&logoColor=white" alt="Gmail"/></a>
	<a href="https://github.com/M7md-Galal"><img src="https://img.shields.io/badge/github-%23181717.svg?style=plastic&logo=github&logoColor=white" alt="GitHub"/></a>
	<a href="https://wa.me/0201094651438"><img src="https://img.shields.io/badge/whatsapp-%2325D366.svg?style=plastic&logo=whatsapp&logoColor=white" alt="Whatsapp"/></a>
	<a href="https://www.linkedin.com/in/mohamed-galal74"><img src="https://img.shields.io/badge/linkedin-%230A66C2.svg?style=plastic&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
	<a href="https://www.facebook.com/profile.php?id=100039845973021&mibextid=ZbWKwL"><img src="https://img.shields.io/badge/facebook-%231877F2.svg?style=plastic&logo=facebook&logoColor=white" alt="Facebook"/></a>
	<a href="https://www.instagram.com/m.o.h.med_/"><img src="https://img.shields.io/badge/instagram-%23E4405F.svg?style=plastic&logo=instagram&logoColor=white" alt="Instagram"/></a>
</p>

name: GitHub Snake Game

on:
  # Schedule the workflow to run daily at midnight UTC
  schedule:
    - cron: "0 0 * * *"
  # Allow manual triggering of the workflow
  workflow_dispatch:
  # Trigger the workflow on pushes to the main branch
  push:
    branches:
      - main
jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      # Step 1: Checkout the repository
      - name: Checkout Repository
        uses: actions/checkout@v3
      # Step 2: Generate the snake animations
      - name: Generate GitHub Contributions Snake Animations
        uses: Platane/snk@v3
        with:
          # GitHub username to generate the animation for
          github_user_name: ${{ github.repository_owner }}
          # Define the output files and their configurations
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark
            dist/ocean.gif?color_snake=orange&color_dots=#bfd6f6,#8dbdff,#64a1f4,#4b91f1,#3c7dd9
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      # Step 3: Deploy the generated files to the 'output' branch
      - name: Deploy to Output Branch
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
          publish_branch: output
          # Optionally, you can set a custom commit message
          commit_message: "Update snake animation [skip ci]"
