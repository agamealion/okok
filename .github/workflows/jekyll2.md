name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main  # 修改为您的主分支名称

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v2

      - name: Set up Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: 2.7

      - name: Install dependencies
        run: bundle install

      - name: Build
        run: bundle exec jekyll build

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token : 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
          publish_dir: ./_site