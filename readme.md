# Работа с GitHub Actions

1. Создать репозиторий в GitHub
2. Склонировать репозиторий на локальный компьютер
3. Установить [Hugo](https://gohugo.io)
4. Создать скелет нового сайта: `hugo new site --force .`
5. Добавить тему оформления:
   ```
   git submodule add --depth 1 https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
   ```
6. Задать тему в конфигурационной файл `hugo.toml` добавить `theme = 'ananke'`
7. Создать страницу `hugo new content posts/my-first-post.md`
8. Проверить работу сайта локально `hugo server`
9. Добавить файл описания workflow для GitHub Actions `.github/workflows/deploy.yml`

   ```yaml
   on: push
   jobs:
     deploy:
       runs-on: ubuntu-latest
       steps:
         - uses: action/checkout@v4
         - run:
           apt-get update
           apt-get install -y hugo
           hugo
        - uses: uses: JamesIves/github-pages-deploy-action@v4
          with:
            folder: public
   ```

   Документация: https://github.com/marketplace/actions/deploy-to-github-pages

10. Закоммитить и запушить в GitHub
11. Проследить работу GitHub Actions
12. Перейти в настройки репозитория и в разделе GitHub Pages указать публикацию из ветки.
