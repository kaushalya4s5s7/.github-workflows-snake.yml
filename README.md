name: Generate Snake Animation

on:
  schedule:
    - cron: "0 0 * * *"  # Runs every midnight
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v3
      - name: Generate Snake Animation
        uses: Platane/snk@v2
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          output: dist/github-contribution-grid-snake.svg
      - name: Push Snake Animation
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
