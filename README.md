# 🌊 Кнопка с анимацией "волна" 🌊

Источник: видео "Как сделать красивую кнопку с анимацией CSS HTML // CSS3 эффекты туториал // Фрилансер по жизни" 
https://vkvideo.ru/video-125918837_456239137?sel=19460369

![2024-12-21_14-35-20](https://github.com/user-attachments/assets/870646a4-683f-4c80-9884-1bb610d3fa7f)



https://github.com/user-attachments/assets/1beeb8fc-3bf9-4042-9617-d5f79b0c9c04



1. создаем проект в программе "WebStorm" для работы с JavaScript (скачать бесплатную версию https://www.jetbrains.com/webstorm/)
2. создаем файлы index.html, style.css, script.js в папке проекта
3. в файле index.html готовим шаблон

```html
<!--сообщаем браузеру, как стоит обрабатывать эту страницу-->
<!DOCTYPE html>
<!--оболочка документа, указываем язык содержимого-->
<html lang="ru">
<!--заголовок страницы, контейнер для других важных данных (не отображается)-->
<head>
    <!--заголовок страницы в браузере-->
    <title>Кнопка с волнами</title>
    <!--подключаем CSS-->
    <link rel="stylesheet" href="style.css">
    <!--кодировка страницы-->
    <meta charset="utf-8">
    <!--адаптив-->
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
    <title>Title</title>
</head>
<!--отображаемое тело страницы-->
<body>
<!--оболочка для демонстрации-->
<div class="wrapper">
    <!--контент-->

</div>
<!--
<script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
<script src="script.js"></script>
-->
</body>
</html>
```

4. в файле index.html создаем саму оболочку кнопки в разделе body

```html
<div class="wrapper">
    <!--контент-->
    <a href="" class="wave-btn">
        <!--оболочка для кнопки-->
        <span class="wave-btn_text">Кнопка</span>
        <!--span для текста-->
        <span class="wave-btn_waves"></span>
        <!--span с волнами-->
    </a>
</div>
```

5. в файле style.css вставляем шаблон

```css
/*обнуление, которое убирает padding, margin, border*/
*,*:before,*:after {
    padding: 0;
    margin: 0;
    border: 0;
    /*вычисляет ширину контента, чтобы padding не учитывался*/
    -moz-box-sizing: border-box; 
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
}
html,body {
    height: 100%;
}
/*стили для демонстрации, можно потом их убрать*/
body {

}
.wrapper{
    /*оболочка wrapper*/
    width: 100%;
    min-height: 100%;
    height: 100%;
    overflow: hidden;

}
/*основные стили*/
```

6. в файл style.css переносим классы из файла html

```css
.wave-btn {}
.wave-btn_text {}
.wave-btn_waves {}
```

7. в файл style.css задаем черный цвет фона в стилях для демонстрации

```css
body {
    background-color: #000;
}
```

8. в файл style.css в разделе .wrapper выравниваем кнопку по центру экрана

```css
display: -webkit-flex;
display: -moz-flex;
display: -ms-flex;
display: -o-flex;
display: flex;

position: relative;

/*параметры, которые отцентруют все содержимое в оболочке по центру/горизонтали и вертикали*/
justify-content: center;
align-items: center;
```

9. в файл style.css в разделе .wave-btn {} для четкой анимации

```css
.wave-btn {
    /*ширину и высоту потом придется регулировать*/
    width: 280px;
    height: 60px;
    display: -webkit-flex;
    display: -moz-flex;
    display: -ms-flex;
    display: -o-flex;
    display: flex;

    /*добавляем анимацию с префиксами, чтобы анимация работала в большинстве браузеров и их версий*/
    transition: all 0.8s ease 0s;
    -webkit-transition: all 0.8s ease 0s;
    -moz-transition: all 0.8s ease 0s;
    -ms-transition: all 0.8s ease 0s;
    -o-transition: all 0.8s ease 0s;

    /*выравниваем весь контент внутри кнопки по центру/горизонтали/вертикали*/
    justify-content: center;
    align-items: center;

    border-radius: 0 0 10px 10px; /*сверху слева и сверху справа - 0, а снизу справа и снизу слева - по 10 px*/

    /*убираем подчеркивание у ссылки кнопки*/
    text-decoration: none;
}
```

10. в файл style.css в разделе .wave-btn_text {} для изменения текста кнопки

```css
.wave-btn_text {
    font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
    /*задаем белый цвет*/
    color: #fff;
    /*чтобы сделать все буквы в верхнем регистре*/
    text-transform: uppercase;
    letter-spacing: 8px;

    /*чтобы текст кнопки выглядывал перед анимацией*/
    position: relative;
    z-index: 1;
}
```

11. в файл style.css в разделе .wave-btn_waves {} для оформления самих волн

```css
.wave-btn_waves {
    position: absolute;
    width: 280px;
    height: 280px;
    background-color: #4973ff;
    top: 0;
    left: 0;
    -webkit-box-shadow: inset 0 0 50px rgba(0, 0, 0, 0.5);
    box-shadow: inset 0 0 50px rgba(0, 0, 0, 0.5);
}
```

12. в файл style.css добавляем общий стиль для псевдоэлементов

```css
/*общие стили для псевдоэлементов*/
.wave-btn_waves:after,
.wave-btn_waves:before {
    content: "";
    position: absolute;
    top: 0;
    left: 50%;
    width: 250%;
    height: 250%;

    transition: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    -moz-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    -ms-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    -webkit-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    -o-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
}
```

13. в файл style.css добавляем стиль для каждого псевдоэлемента волны

```css
/*стили для каждого псевдоэлемента*/
.wave-btn_waves:before{
    background-color: #000; /*абсолютно черный*/
    border-radius: 48%;
}
.wave-btn_waves:after{
    background-color: rgba(0,0,0,0.5); /*полупрозрачный черный*/
    border-radius: 44%;
}
```

14. в файл style.css добавляем анимацию для каждого псевдоэлемента волны

```css
/*стили для каждого псевдоэлемента*/
.wave-btn_waves:before{
    /*анимация волны*/
    animation: waves 5s infinite linear;
    -webkit-animation: waves 5s infinite linear;
    -moz-animation: waves 5s infinite linear;
    -o-animation: waves 5s infinite linear;
}
.wave-btn_waves:after{
    /*анимация волны*/
    animation: waves 10s infinite linear;
    -webkit-animation: waves 10s infinite linear;
    -moz-animation: waves 10s infinite linear;
    -o-animation: waves 10s infinite linear;
}
```

15. в файле style.css настраиваем анимацию для всех браузеров

```css
/*настраиваем анимацию для всех браузеров*/
/*задаем имя анимации - waves*/
@keyframes waves{
    0%{
        transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    }
    100%{
        /*меняем только 0 на 360 градусов*/
        transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
    }
}
@-webkit-keyframes waves{
    0%{
        transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    }
    100%{
        /*меняем только 0 на 360 градусов*/
        transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
    }
}
@-moz-keyframes waves{
    0%{
        transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    }
    100%{
        /*меняем только 0 на 360 градусов*/
        transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
    }
}
@-o-keyframes waves{
    0%{
        transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    }
    100%{
        /*меняем только 0 на 360 градусов*/
        transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
    }
}
```

16. в файле style.css в разделе стиля волны для кнопки .wave-btn добавляем overflow

```css
overflow: hidden;
```

17. в файле style.css в отдельном новом разделе стиля волны для кнопки 
.wave-btn добавляем анимацию, чтобы при наведении кнопка наполнялась водой

```css
/*анимация заполнения водой кнопки при наведении курсора*/
.wave-btn:hover .wave-btn_waves{ /*к кнопке добавляем псевдокласс hover с обращением к нашим волнам .wave-btn_waves*/
    top: -50px;
    /*чтобы слишком быстро не заполнялась водой, то в разделе .wave-btn_waves изменяем анимацию с 0.3s на 0.8s*/
}
```

18. в файле style.css в том же новом разделе стиля волны для кнопки и для волны 
.wave-btn и в кнопке волны .wave-btn_waves добавляем анимацию, чтобы при наведении кнопка наполнялась водой плавно
и медленно

```css
.wave-btn
/*добавляем анимацию с префиксами, чтобы анимация работала в большинстве браузеров и их версий*/
transition: all 0.8s ease 0s;
-webkit-transition: all 0.8s ease 0s;
-moz-transition: all 0.8s ease 0s;
-ms-transition: all 0.8s ease 0s;
-o-transition: all 0.8s ease 0s;

.wave-btn_waves 
/*добавляем для плавной анимации заполнения водой кнопки при наведении курсора*/
transition: all 0.8s ease 0s;
-webkit-transition: all 0.8s ease 0s;
-moz-transition: all 0.8s ease 0s;
-ms-transition: all 0.8s ease 0s;
-o-transition: all 0.8s ease 0s;
```

19. в файле style.css в отдельном новом разделе стиля для кнопки .wave-btn добавляем анимацию, чтобы при наведении кнопка наполнялась водой плавно
    и медленно

```css
.wave-btn:hover {
    border-radius: 10px; /*чтобы со всех сторон были пиксели*/

    /*снова добавляем анимацию при hover, чтобы она заиграла немного позже - вместо 0s делаем 0.2s*/
    transition: all 0.8s ease 0.2s;
    -webkit-transition: all 0.8s ease 0.2s;
    -moz-transition: all 0.8s ease 0.2s;
    -ms-transition: all 0.8s ease 0.2s;
    -o-transition: all 0.8s ease 0.2s;
}
```

20. в файле style.css в том же новом разделе стиля для кнопки .wave-btn:hover добавляем тени для волн.
Для тени берем rgba из цвета волн.
Заходим на сайт http://hex2rgba.devoth.com/, вставляем в большое окошко #4973ff, программа выдает цвет в виде rgba

![20](https://github.com/user-attachments/assets/1cc880eb-b7c6-4051-8825-f63a6224eb1e)


```css
/*добавляем тени к кнопке - цвет такой же, как у волны .wave-btn_waves - background-color: #4973ff*/
/*Кнопка становится ярче при наведении курсора мыши*/
-webkit-box-shadow: 0 0 40px rgba(73, 115, 255, 0.6);
box-shadow: 0 0 40px rgba(73, 115, 255, 0.6);
```


# Итог:

1. файл index.html

```html
<!--сообщаем браузеру, как стоит обрабатывать эту страницу-->
<!DOCTYPE html>
<!--оболочка документа, указываем язык содержимого-->
<html lang="ru">
<!--заголовок страницы, контейнер для других важных данных (не отображается)-->
<head>
    <!--заголовок страницы в браузере-->
    <title>Кнопка с волнами</title>
    <!--подключаем CSS-->
    <link rel="stylesheet" href="style.css">
    <!--кодировка страницы-->
    <meta charset="utf-8">
    <!--адаптив-->
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
    <title>Title</title>
</head>
<!--отображаемое тело страницы-->
<body>
<!--оболочка для демонстрации-->
<div class="wrapper">
    <!--контент-->
    <a href="" class="wave-btn">
        <!--оболочка для кнопки-->
        <span class="wave-btn_text">Кнопка</span>
        <!--span для текста-->
        <span class="wave-btn_waves"></span>
        <!--span с волнами-->
    </a>
</div>
<!--
<script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
<script src="script.js"></script>
-->
</body>
</html>
```

![2024-12-21_14-24-40](https://github.com/user-attachments/assets/80385c8e-540c-4739-8389-dc7c0b9eae17)

2. файл style.css

```css
/*обнуление, которое убирает padding, margin, border*/
*,*:before,*:after {
    padding: 0;
    margin: 0;
    border: 0;
    /*вычисляет ширину контента, чтобы padding не учитывался*/
    -moz-box-sizing: border-box;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
}
html,body {
    height: 100%;
}
/*стили для демонстрации, можно потом их убрать*/
body {
    background-color: #000; /*задний фон*/
}
.wrapper{
    /*оболочка wrapper*/
    width: 100%;
    min-height: 100%;
    height: 100%;
    overflow: hidden;

    display: -webkit-flex;
    display: -moz-flex;
    display: -ms-flex;
    display: -o-flex;
    display: flex;

    /*параметры, которые отцентруют все содержимое в оболочке по центру/горизонтали и вертикали*/
    justify-content: center;
    align-items: center;

}
/*основные стили*/

.wave-btn:hover {
    border-radius: 10px; /*чтобы со всех сторон были пиксели*/

    /*снова добавляем анимацию при hover, чтобы она заиграла немного позже - вместо 0s делаем 0.2s*/
    transition: all 0.8s ease 0.2s;
    -webkit-transition: all 0.8s ease 0.2s;
    -moz-transition: all 0.8s ease 0.2s;
    -ms-transition: all 0.8s ease 0.2s;
    -o-transition: all 0.8s ease 0.2s;

    /*добавляем тени к кнопке - цвет такой же, как у волны .wave-btn_waves - background-color: #4973ff*/
    /*Кнопка становится ярче при наведении курсора мыши*/
    -webkit-box-shadow: 0 0 40px rgba(73, 115, 255, 0.6);
    box-shadow: 0 0 40px rgba(73, 115, 255, 0.6);
}

/*анимация заполнения водой кнопки при наведении курсора*/
.wave-btn:hover .wave-btn_waves{ /*к кнопке добавляем псевдокласс hover с обращением к нашим волнам .wave-btn_waves*/
    top: -50px;
    /*чтобы слишком быстро не заполнялась водой, то в разделе .wave-btn_waves изменяем анимацию с 0.3s на 0.8s*/
}


/*анимация волны у кнопки*/
.wave-btn {
    /*ширину и высоту потом придется регулировать*/
    width: 280px;
    height: 60px;
    display: -webkit-flex;
    display: -moz-flex;
    display: -ms-flex;
    display: -o-flex;
    display: flex;

    overflow: hidden; /*чтобы убрать лишнюю анимацию с кнопки*/

    position: relative;

    /*добавляем анимацию с префиксами, чтобы анимация работала в большинстве браузеров и их версий*/
    transition: all 0.8s ease 0s;
    -webkit-transition: all 0.8s ease 0s;
    -moz-transition: all 0.8s ease 0s;
    -ms-transition: all 0.8s ease 0s;
    -o-transition: all 0.8s ease 0s;

    /*выравниваем весь контент внутри кнопки по центру/горизонтали/вертикали*/
    justify-content: center;
    align-items: center;

    border-radius: 0 0 10px 10px; /*сверху слева и сверху справа - 0, а снизу справа и снизу слева - по 10 px*/

    /*убираем подчеркивание у ссылки кнопки*/
    text-decoration: none;
}
.wave-btn_text {
    font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
    /*задаем белый цвет*/
    color: #fff;
    /*чтобы сделать все буквы в верхнем регистре*/
    text-transform: uppercase;
    letter-spacing: 8px;

    /*чтобы текст кнопки выглядывал перед анимацией*/
    position: relative;
    z-index: 1;
}
.wave-btn_waves {
    position: absolute;
    width: 280px;
    height: 280px;
    background-color: #4973ff;
    top: 0;
    left: 0;
    -webkit-box-shadow: inset 0 0 50px rgba(0, 0, 0, 0.5);
    box-shadow: inset 0 0 50px rgba(0, 0, 0, 0.5);

    /*добавляем для плавной анимации заполнения водой кнопки при наведении курсора*/
    transition: all 0.8s ease 0s;
    -webkit-transition: all 0.8s ease 0s;
    -moz-transition: all 0.8s ease 0s;
    -ms-transition: all 0.8s ease 0s;
    -o-transition: all 0.8s ease 0s;
}

/*общие стили для псевдоэлементов*/
.wave-btn_waves:after,
.wave-btn_waves:before {
    content: "";
    position: absolute;
    top: 0;
    left: 50%;
    width: 250%;
    height: 250%;

    transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    -moz-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    -ms-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    -webkit-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    -o-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
}

/*стили для каждого псевдоэлемента*/
.wave-btn_waves:before{
    background-color: #000; /*абсолютно черный*/
    border-radius: 48%;

    /*анимация волны*/
    animation: waves 5s infinite linear;
    -webkit-animation: waves 5s infinite linear;
    -moz-animation: waves 5s infinite linear;
    -o-animation: waves 5s infinite linear;
}
.wave-btn_waves:after{
    background-color: rgba(0,0,0,0.5); /*полупрозрачный черный*/
    border-radius: 44%;

    /*анимация волны*/
    animation: waves 10s infinite linear;
    -webkit-animation: waves 10s infinite linear;
    -moz-animation: waves 10s infinite linear;
    -o-animation: waves 10s infinite linear;
}

/*настраиваем анимацию для всех браузеров*/
/*задаем имя анимации - waves*/
@keyframes waves{
    0%{
        transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    }
    100%{
        /*меняем только 0 на 360 градусов*/
        transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
    }
}
@-webkit-keyframes waves{
    0%{
        transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    }
    100%{
        /*меняем только 0 на 360 градусов*/
        transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
    }
}
@-moz-keyframes waves{
    0%{
        transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    }
    100%{
        /*меняем только 0 на 360 градусов*/
        transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
    }
}
@-o-keyframes waves{
    0%{
        transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(0deg) scale(1);
    }
    100%{
        /*меняем только 0 на 360 градусов*/
        transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -moz-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -ms-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -webkit-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
        -o-transform: translate3d(-50%,-96%,0) rotate(360deg) scale(1);
    }
}
```

![2024-12-21_14-25-00](https://github.com/user-attachments/assets/c1a0a7d6-c8ae-4b3e-92aa-e88f5225fea3)
![2024-12-21_14-25-22](https://github.com/user-attachments/assets/024cb2be-46ef-41bf-8c0c-c8fe50517f7c)
![2024-12-21_14-25-48](https://github.com/user-attachments/assets/e4a23def-6220-4d95-b89d-3f55344c2e71)
![2024-12-21_14-26-32](https://github.com/user-attachments/assets/d98ef4b4-2523-40d6-8138-f7700eea49f6)
![2024-12-21_14-26-52](https://github.com/user-attachments/assets/661426ae-116f-4ec5-bb9f-3045f122802b)


3. script.js пустой
