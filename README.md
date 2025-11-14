name: Generate Snake

on:
  schedule:
    - cron: "0 */12 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Generate GitHub Contribution Snake
        uses: Platane/snk@v3
        with:
          github_user_name: ${{ github.repository_owner }}

          # list of files to generate
          outputs: |
            dist/github-snake.svg?palette=github&color_snake=#40c463&color_dots=#ebedf0,#c6e48b,#7bc96f,#239a3b,#196127
            dist/github-snake-dark.svg?palette=github-dark
            dist/github-snake-light.svg?palette=github-light

      - name: Upload artifacts
        uses: actions/upload-artifact@v4
        with:
          name: snake
          path: dist
