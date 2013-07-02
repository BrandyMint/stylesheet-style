# Правила по оформлению стилей:


1. В `application.css` никаких стилей, только `require` и `import`,
   каждый описывается в комментарии (что инклюдим, какой базовый класс
   определяется).

2. Каждая страница начинается блоком-контейнером, описывающим ее.
   Например `login-page`, `profile-page`

3. Каждый блок должен носить осмысленное имя. Нужно придерживаться
   следующих правил:

   * если блок отображает набор элементов, то он должен носить их
     название во множественном числе (`posts`, `companies` и т.д.);
   * если блок отображает один элемент, то он должен носить его название
     (`post`, `company`);
   * если блок отображает элемент UI, то он должен носить его название
     (`menu`, `tag-page`, `toolbar-item`), причем это название можно дополнить
     логическим названием этого элемента UI (`top-menu`, `filter-list`,
     `company-type-select`);
   * блоки могут быть вложены друг в друга.

4. Стили всех страниц, относящихся к одному контроллеру, должны быть
   определены в одном, имеющем название контроллера (например `posts.css.sass`).
   
5. Для стилей используем только классы, никаких id.
   В крайнем случае допустимы селекторы.

6. Классы-свойства и классы-модификаторы применяются к элементам
   отдельно и определяеются вместе с элементом, которые они
   модифицируют.

   Пример:
        # posts.html.haml
        .posts.highlighted
          .post.top
            = render 'post'

        // posts.css.scss
        .posts
          .post .top
            background: red;
            
        .posts .highlighted 
          // ...

7. Необходимо по возможности максимально использовать классы и определять
   стили элементов через них, повышая устойчивость к случайным изменениям.

   Пример:
        .post
          .post-title 
            // title
          .post-body
            // body

8. Активно используем переменные.
   Все переменные (размеры шрифтов, цвета и размеры основных блоков)
   указываются только в variables.sass

   Все миксины указываются только в mixins.sass

9. Все шрифты, начертания, пути к файлам и т.д. указываются в fonts.sass
   (за исключением вынесенных в переменные названий вроде $baseFontFamily: 'Helvetica', Arial, sans-serif)

10. Framework-first! Внимательно изучаем ипользуемый фреймворк (чаще всего — thomas-mcdonald/bootstrap-sass),
   перед добавлением новой переменной или миксина проверяем их наличие во фреймворке.

11. Используем вложенность SASS, но в меру: не допускать вложенности дальше 4 уровня.
   Вложенность работает как для селекторов, так и для свойств.

   Пример:
         .post
            // ...
         .post-title
           border:
             top: 
               // ...
             bottom: 
               // ...
         .post-nav
           li
             a
               // ...

11. Файлы стилей которые используются только для импорта в другие файлы
    именовать без .css, например nagivation.sass вместо
    navigation.css.sass


