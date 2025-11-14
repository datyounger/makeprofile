name: Generate Snake

on:
  schedule:
    - cron: "0 */12 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: windows-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Generate GitHub Contribution Snake
        uses: Platane/snk@v3
        with:
          github_user_name: datyounger
          outputs: |
            dist/snake-dark.svg?palette=github-dark&color_snake=#ffffff

      - name: Upload artifacts
        uses: actions/upload-artifact@v4
        with:
          name: snake
          path: dist
