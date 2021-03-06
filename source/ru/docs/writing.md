---
title: Написание
---
Чтобы создать новый пост, можно выполнить следующую команду:

``` bash
$ hexo new [layout] <title>
```

`post` — это `layout` по умолчанию, но можно установить свой собственный изменив значение `default_layout` в `_config.yml`.

### Макет

В Hexo есть три макета по умолчанию: `post`, `page` и `draft`. Каждый из них сохраняется по своему пути. Пользовательские макеты сохраняются в папке `source/_posts`.

Макет | Путь
--- | ---
`post` | `source/_posts`
`page` | `source`
`draft` | `source/_drafts`

{% note tip Disabling layout %}
If you don't want an article (post/page) to be processed with a theme, set `layout: false` in its front-matter. Refer to [this section](/ru/docs/front-matter#Макет) for more details.
{% endnote %}

### Имя файла

По умолчанию Hexo использует название поста для создания имени. Для изменения имени файла по умолчанию, можно отредактировать настройки, изменив `new_post_name` в `_config.yml`. Например, у значения `:year-:month-:day-:title.md`, будет префикс с именем файлов и датой создания поста. Можно использовать следующие подстановки:

Подстановка | Описание
--- | ---
`:title` | Заголовок поста (строчными буквами с пробелами заменёнными на дефисы)
`:year` | Год создания. Например: `2015`
`:month` | Месяц создания (с ведущим нулём). Например: `04`
`:i_month` | Месяц создания (без ведущего нуля). Например: `4`
`:day` | День создания (с ведущим нулём). Например: `07`
`:i_day` | Месяц создания (без ведущего нуля). Например: `7`

### Черновики

Ранее упоминалось о специальном макете в Hexo: `draft`. В нём сообщения при создании сохраняются в папку `source/_drafts`. Можно использовать команду `publish`, чтобы переместить черновик в папку `source/_posts`. `publish` похожа на команду `new`.

``` bash
$ hexo publish [layout] <title>
```

Черновики по умолчанию не отображаются. Можно добавить параметр `--draft` при запуске Hexo или установить значение `render_drafts: true` в `_config.yml`, чтобы включить обработку черновиков.

### Заготовки

При создании сообщения Hexo строит файлы на основе соответствующего `scaffolds` файла. Например:

``` bash
$ hexo new photo "My Gallery"
```

Когда выпонится эта команда, Hexo постарается найти `photo.md` в папке `scaffolds` и создать пост на его основе. Эти подстановочные части доступны в заготовках:

Подстановка | Описание
--- | ---
`layout` | Макет
`title` | Заголовок
`date` | Дата создания файла

### Supported Formats

Hexo support posts written in any format, as long as the corresponding renderer plugin is installed.

For example, Hexo has `hexo-renderer-marked` and `hexo-renderer-ejs` installed by default, so you can write your posts in `markdown` or in `ejs`. If you have `hexo-renderer-pug` installed, then you can even write your post in pug template language.

You can rename your posts and change to file extension from `.md` to `.ejs`, then Hexo will use `hexo-renderer-ejs` to render that file, so do the other formats.
