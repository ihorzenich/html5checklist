# Чеклист верстки

Для того чтобы отдавать вёрстку клиенту, достаточно соблюдения первых 5&nbsp;пунктов. 
Для выдачи в&nbsp;продакшен&nbsp;&mdash; первых 6.

*Подробности по&nbsp;каждому пункту: http://habrahabr.ru/post/114256/*

1. **Соответствие макету**
2. **Кроссбраузерность, кодировка и&nbsp;DOCTYPE**
3. **Валидность (включая CSSLint и JSHint), доступность (ARIA, WCAG), микроформаты (microformats 1 & 2, microdata)**
4. **Независимость блоков в&nbsp;CSS: минимизация каскада, использование техник БЭМ**
5. **Сайт должен нормально смотреться во&nbsp;всех стандартных разрешениях от&nbsp;320 и&nbsp;выше, не&nbsp;иметь горизонтального скролла и&nbsp;вписываться в&nbsp;экран мобильных устройств**
6. Корректная работа при вбивании реального текста, надёжность вёрстки
7. CSS должен быть написан с&nbsp;использованием препроцессоров (LESS/Sass/Stylus). Желательно использование систем сборки (Grunt/Gulp) и&nbsp;построцессоров (PostCSS/Autoprefixer).
8. Проверка и&nbsp;оптимизация скорости загрузки: https://github.com/ihorzenich/WebPerformanceChecklist
9. Поддержка Retina
10. Наличие Win/Mac/Linux-аналогов шрифтов
11. Доступность при выключенных(загружающихся) картинках
12. HTML5&nbsp;формы, линковка, валидация
13. Семантичность. Отсутствие глупостей в&nbsp;html и&nbsp;css, единообразие, аккуратность (смотри "Плохо/хорошо")
14. Правильная структура заголовков (H1,H2,… и&nbsp;т.д. и&nbsp;TITLE)
15. Работоспособность при выключенном (незагруженном) JavaScript
16. Работоспособность при выключенном Flash
17. Отсутствие багов при увеличенном шрифте

<h2>13. &quot;Плохо&quot;/&quot;Хорошо&quot;</h2>
Важно понимать что семантика&nbsp;&mdash; может быть не&nbsp;только в&nbsp;используемых элементах, но&nbsp;и&nbsp;в&nbsp;именах классов. И&nbsp;БЭМ-иерархия классов&nbsp;&mdash; это новый уровень семантики.

<b>Плохо:</b>
<ul><li><strong>Самое страшное, к&nbsp;счастью уже редкое&nbsp;&mdash; <code>float: left</code> для всех блоков.</strong> Безумный верстальщик эмулирует привычные ячейки таблиц, расставляя блоки как кирпичи друг за&nbsp;другом. Вон из&nbsp;профеcсии!<br/>
Проверяется в extension для браузеров <strong>Web Developer</strong> &rarr; Outline &rarr; Outline Floated Elements, если всё в&nbsp;красных блоках, вёрстку нужно выкидывать на&nbsp;помойку. <br/>
Так же, такая верстка получается при создании сайтов на <strong>Adobe Muse</strong>. <br/>
<strong>Примеры</strong>: <a href="http://www.cardiganium.ru/" target="_blank">один</a> - <a href="http://www.zebraproject.ru/" target="_blank">два</a> - <a href="http://www.jurist-kavykina.ru/" target="_blank">три</a>  
</li>
<li>Отступы между блоками на&nbsp;сайте должны быть за&nbsp;счёт margin у&nbsp;блоков, а&nbsp;не&nbsp;выпирающих наружу margin у&nbsp;содержимого блоков.</li>
<li>Плохо&nbsp;&mdash; отсутствие тайтлов.</li>
<li>Плохо&nbsp;&mdash; отсутствие alt у&nbsp;картинок.</li>
  <li>Плохо&nbsp;&mdash; хаки для браузеров внутри main.css (как без фильтров, так и&nbsp;с&nbsp;ними). Без фильтров&nbsp;&mdash; это когда когда просто пишем <code>{zoom: 1;}</code> — это&nbsp;оч. плохо, т.к. будет применяться ко&nbsp;всем&nbsp;IE, а&nbsp;не&nbsp;только к&nbsp;тому, в&nbsp;котором проблема. С&nbsp;фильтрами&nbsp;&mdash; когда пишут <code>(* html, *+html и т.д.)</code> — плохо, потому что это засоряет код, делает его менее читабельным, а&nbsp;какие-то хаки могут быть и&nbsp;вообще невалидными и&nbsp;нарушать прогон CSSLint. Conditional Comments&nbsp;&mdash; тоже плохо, хотя раньше считалось хорошей техникой, плохо т.к. это увеличение кол-ва css-файлов и&nbsp;главное&nbsp;&mdash; это разнесение кода в&nbsp;разные места. Сейчас рекомендуется использовать специальные классы типа <code>html.ie7, html.ie8,…</code> (из&nbsp;HTML5&nbsp;Boilerplate), Modernizer-детектирование фич (классы вида <code>html.js.flexbox.canvas.no-touch…</code>) и&nbsp;JS-детектирование браузера и&nbsp;платфорым (например CSS Browser Selector генерирующий классы вида <code>html.webkit.chrome.chrome25.win.win8…</code>)</li>
<li>Плохо&nbsp;&mdash; не&nbsp;проверять tabindex в&nbsp;формах.</li>
<li>Плохо&nbsp;&mdash; писать стили не&nbsp;думая о&nbsp;логике размещения элементов. Например, если элемент всегда находится сверху, у&nbsp;него должен быть большой z-index, нельзя надеяться на&nbsp;то&nbsp;что сейчас всё нормально смотрится&nbsp;&mdash; стили должны быть железобетонными. Если элемент всегда должен находится на&nbsp;каком-то месте, в&nbsp;независимости от&nbsp;окружающих его элементов&nbsp;&mdash; это position: absolute; а&nbsp;не&nbsp;float и&nbsp;т.д.
Блоки независящие друг от&nbsp;друга не&nbsp;должны быть внутри одного блока (например телефон компании и&nbsp;поиск по&nbsp;сайту). Блоки независящие по&nbsp;расположению друг от&nbsp;друга должны быть position absolute, а&nbsp;не&nbsp;float&rsquo;ится.</li>
<li>Очень плохо&nbsp;&mdash; презентационные классы (right, red).</li>
<li>Нежелательно когда вёрстка содержит пустые блоки для презентационных целей, для этого существуют псевдоэлементы</li>
<li>Плохо когда нет базовых стилей у&nbsp;стандартных элементов. Т.е. просто h1,h2,ul,table,etc без классов должны смотреться красиво и&nbsp;органично. Проще говоря&nbsp;&mdash; используйте Normalize, a&nbsp;не&nbsp;Reset CSS.</li>
<li>Плохо когда нет постепенного уточнения стилей для текста, когда стиль выписывается для каждого элемента отдельно, а&nbsp;за&nbsp;его пределами&nbsp;&mdash; внешний вид может быть кардинально другой. Речь о&nbsp;ситуации когда например текст, написанный без абзацев, имеет вообще не&nbsp;тот стиль что у&nbsp;всех элементов в&nbsp;блоке. Надо вести стили снизу вверх, постепенно уточняя&nbsp;их. Тут важно не&nbsp;путать стили для текста и&nbsp;стили для блоков. Для текста&nbsp;&mdash; каскад это добро, для блоков сайта&nbsp;&mdash; нужно использовать БЭМ.</li>
<li>Ещё хуже&nbsp;&mdash; чересчур детализированные глобальные стили. Например <code>a {font: italic 10px Tahoma;}</code> /* Ненависть! Ненависть! НЕНАВИСТЬ!!11 */ Потом приходится переопределять стиль ссылок для каждого блока.</li>
<li>Размеры и&nbsp;позиционирование элемента должны указываться в&nbsp;одних единицах измерения. Т.е. высота/ширина блока в&nbsp;px&nbsp;и&nbsp;margin/padding в&nbsp;em&nbsp;&mdash; это странно и&nbsp;скорей всего ошибка. Line-height&nbsp;&mdash; лучше задавать коэффициентом (1/1.2/1.4... т.е. без указания единицы измерения&nbsp;&mdash; это цифра на&nbsp;которую умножается font-size и&nbsp;получится межстрочный интервал). Если задали font-size/height в&nbsp;em&nbsp;&mdash; значит задаём и&nbsp;margin/padding тоже в&nbsp;em. Классический пример: список dl-dt-dd, где dt&nbsp;и&nbsp;dd&nbsp;ставятся друг на&nbsp;против друга с&nbsp;помощью подтягивания dd&nbsp;отрицательным margin вверх. Или&nbsp;&mdash; выделили padding&rsquo;ом место под position: absolute какого-то текстового блока. У&nbsp;текстовых элементов (абзацей, ячеек таблиц) задаём padding и&nbsp;height в&nbsp;em (чтоб корректно увеличивать размер шрифта) .</li>
<li><s>Плохо</s>(недопустимо!) вешать стили на&nbsp;селекторы вложенных стандартных тэгов, без классов. Т.е. допустим пишем что-то типа <code>h2&nbsp;a span {какая-то крепкая штука, типа картинки с&nbsp;графикой, что закрывает текст в заголовке}</code>, а&nbsp;потом клиент в&nbsp;визиге внезапно вбивает такое сочетание! И&nbsp;получаем невероятный баг. На просто одиночные теги для вывода текста из БД — можно, но используя блок .b-text (смотри BEM CSS).</li>
<li>Плохо&nbsp;&mdash; напрямую задавать визуальное отображение элементов через&nbsp;js: <code>$('.element').css(color,"#f00")</code>. Это должно делаться через установку/смену классов.</li></ul>

<b>Хорошо:</b>
<ul><li><strong><a href="http://getbem.com/">БЭМ</a></strong>! Важно понимать что это методология, а&nbsp;не&nbsp;инструменты. Для обычных сайтов достаточно вёрстки по&nbsp;<a href="http://delka.github.io/talks/webcamp/2015/bem/">BEM CSS</a>, без использования библиотеки блоков и&nbsp;bem-tools. <a href="http://delka.name/blog/2013/04/bem-otkroveniya-prinyavshih-veru/">Я&nbsp;долго считал что &laquo;BEM&nbsp;&mdash; это классная идея, но&nbsp;это чересчур, так категорично не&nbsp;надо, надо чуть по-другому, под себя...&raquo;</a>, так вот&nbsp;&mdash; это неверно! Нужно обязательно уходить от&nbsp;каскада, а&nbsp;БЭМ&nbsp;&mdash; это один из&nbsp;отличных вариантов решения.</li>
<li>Хорошо&nbsp;&mdash; структурировать код в&nbsp;блоки описывающие логику документа. Т.е. создавать div даже там, где он&nbsp;для презентационных целей не&nbsp;нужен. И&nbsp;наоборот&nbsp;&mdash; стараться не&nbsp;ставить лишний div там, где структура этого не&nbsp;требует, а&nbsp;это нужно лишь для визуальных эффектов.</li>
<li><strong><a href="http://html5boilerplate.com">HTML5 Boilerplate</a></strong>&nbsp;&mdash; замечательный стартовый шаблон от&nbsp;&laquo;отцов&raquo;. Используйте и&nbsp;присоединяйтесь к&nbsp;разработке, добавляйте свои велосипеды туда! 
Раньше у&nbsp;нас был свой самописный framework-стартовый html, теперь используем Boilerplate как основу, а&nbsp;в&nbsp;него уже добавляем старые наработки.</li>
<li>Используйте наработанные решения, чужие модули, jQuery-плагины, не&nbsp;изобретайте велосипедов, а&nbsp;если изобретаете&nbsp;&mdash; поддерживайте&nbsp;их, ведите библиотеку кода (после каждого нового проекта добавляйте туда код, обновляйте старый).</li>
<li>Для текстовых блоков, что редактируются в&nbsp;админке, должна обеспечиваться атомарность текстовых стилей. Т.е. есть у&nbsp;нас страничка с&nbsp;каким-то текстовым блоком, примерно такой структуры:
```css
.content-text h1
.content-text .entry
.content-text .entry .somenamedblock
```
То .somenamedblock должен получать текстовые стили непосредственно&nbsp;&mdash; <code>.somenamedblock {font: …; color: …;}</code>, т.к. иначе в&nbsp;визиге админки мы&nbsp;не&nbsp;сможем их&nbsp;застайлить.</li>
<li>одинаковый html-код для блоков на&nbsp;морде и&nbsp;внутряках, с&nbsp;идентичным контентом, но&nbsp;разным визуальным представлением данных. Реализуется через модификаторы блоков и элементов, но не через модификацию от родителя (каскад от body.pagename например!)</li></ul> 

<h2>Важные мелочи</h2>

<ul><li>Лого на&nbsp;внутряках должно вести на&nbsp;титулку. На&nbsp;титулке logo = h1, на&nbsp;внутряках H1=заголовок контента, а&nbsp;Logo=div</li>
  <li>У&nbsp;каждой страницы должен быть свой уникальный TITLE формата <code>About Us&nbsp;&mdash; %CompanyName%</code></li>
  <li>Все страницы должны быть слинкованы и&nbsp;<a href="http://home.snafu.de/tilman/xenulink.html">проверены на&nbsp;наличие битых ссылок</a>.</li>
  <li>Все ссылки должны как-то реагировать на :hover, :active и :focus&nbsp;&mdash; показыванием/убиранием подчёркивания, сменой цвета, чем угодно. У&nbsp;всех ссылок, кроме пунктов меню, должна быть реакция на :visited</li>
  <li>Проверять что все интерактивные элементы страницы что должны работать&nbsp;&mdash; работают.</li>
  <li>&laquo;Контент в&nbsp;начале страницы&raquo;&nbsp;&mdash; содержимое страницы должно идти в&nbsp;начале кода, до&nbsp;всяких сайдбаров и&nbsp;прочего.</li>
  <li>Все созданные странички изначально должны быть порезаны на шаблоны, чтоб программеру было легче их интегрировать.</li>
  <li><a href="http://habrahabr.ru/blogs/typography/23812/">Копирайт должен быть написан правильно</a>.</li>
  <li>Должны быть favicon.ico (желательно с&nbsp;включенными внутрь неё 32&times;32, 48&times;48 и&nbsp;64&times;64&nbsp;вариациями) и&nbsp;apple-touch-icon</li>
  <li>В&nbsp;вёрстке не&nbsp;должны оставаться закомментированные &laquo;на&nbsp;всякий случай&raquo; куски кода, лишние неиспользуемые файлы, старые версии файлов и&nbsp;т.п. Все бекапы можно вытянуть из&nbsp;системы контроля версий (например Git или SVN), а&nbsp;на&nbsp;живом проекте &laquo;мусор&raquo; потом мешает разобраться как что работает.</li>
  <li>Размеры для блоков, чьи размеры зависят от&nbsp;содержащегося в&nbsp;них текста, нужно задавать в&nbsp;em, а&nbsp;не&nbsp;px.</li>
  <li>Если url ссылки неизвестен, то&nbsp;он&nbsp;должен быть равен её&nbsp;анкору, написанному латиницей с&nbsp;заменой пробелов/спецсимволов на&nbsp;тире.</li>
  <li>Skype-плагин не&nbsp;должен ломать вёрстку</li>
  <li>Ресайз textarea не&nbsp;должен ломать вёрстку</li>
  <li>При проверке frontend в&nbsp;целом&nbsp;&mdash; 404-страница должна отдаваться с&nbsp;кодом 404&nbsp;а не&nbsp;200.</li>
  <li>Нужно подстраховываться фиксируя в&nbsp;css размеры картинок, выводящихся программно.</li>
  <li>Проверка орфографии Word&rsquo;ом или <a href="http://www.artlebedev.ru/tools/orfograf/">Орфографом</a>, желательно&nbsp;&mdash; <a href="http://www.artlebedev.ru/tools/typograf/">оттипографить</a> контент.</li>
  <li>Ссылки на&nbsp;чужие сайты должны быть с&nbsp;<code>target="_blank"</code>, желательно выделять их&nbsp;иконкой &laquo;внешняя ссылка&raquo;.</li>
  <li>Разумеется картинки должны быть в&nbsp;отдельной папке, css&nbsp;&mdash; в&nbsp;отдельной и&nbsp;js&nbsp;&mdash; в&nbsp;отдельной. Графика, не являющаяся частью дизайна (всякие илююстрации, фото в новостях и т.д.) — нужно положить в отдельную папку, например userfiles.</li>
  <li>Изображения должны масштабироваться в зависимости от размера окна <code>(max-width:100%; height:auto;)</code></li>
</ul>

[README IN ENGLISH]

Layout checklist
In order to give the layout to the client, it is enough to comply with the first 5 points. For distribution to production - the first 6.

Details for each item: http://habrahabr.ru/post/114256/

Compliance with the layout
Cross-browser, encoding and DOCTYPE
Validity (including CSSLint and JSHint), accessibility (ARIA, WCAG), microformats (microformats 1 & 2, microdata)
Block independence in CSS: minimizing the cascade, using BEM techniques
The site should look normal in all standard resolutions from 320 and higher, not have horizontal scrolling and fit into the screen of mobile devices
Correct work when driving in real text, layout reliability
CSS should be written using preprocessors (LESS / Sass / Stylus). It is desirable to use build systems (Grunt / Gulp) and builders (PostCSS / Autoprefixer).
Checking and optimizing download speed: https://github.com/ihorzenich/WebPerformanceChecklist
Retina support
Availability of Win / Mac / Linux-like fonts
Availability with disabled (loading) pictures
HTML5 forms, linking, validation
Semantics. No nonsense in html and css, uniformity, neatness (see "Good / bad")
Correct heading structure (H1, H2, ... etc. and TITLE)
Performance with disabled (unloaded) JavaScript
Performance when Flash is off
No bugs with large font
13. "Bad" / "Good"
It is important to understand that semantics can be not only in the elements used, but also in the class names. And the BEM class hierarchy is a new level of semantics.
Bad:

The worst thing, fortunately already rare, is float: leftfor all blocks. Crazy layout designer emulates familiar table cells, placing blocks like bricks one after another. Get out of the profession!
It is checked in the browser extension Web Developer → Outline → Outline Floated Elements, if everything is in red blocks, the layout needs to be thrown into the trash.
Also, such a layout is obtained when creating sites in Adobe Muse .
Examples : one - two - three
Indents between blocks on the site should be due to the margin of the blocks, and not protruding margins of the content of the blocks.
Bad - the lack of titles.
Bad - the lack of alt in images.
Bad - hacks for browsers inside main.css (both without filters and with them). Without filters - this is when when we just write {zoom: 1;}- it's very good. bad because will apply to all IEs, not just the one with the problem. With filters - when they write (* html, *+html и т.д.)- it is bad, because it clogs the code, makes it less readable, and some hacks may be generally invalid and break the CSSLint run. Conditional Comments is also bad, although it was previously considered a good technique, it is bad because this is an increase in the number of css files, and the main thing is the distribution of the code to different places. Now it is recommended to use special classes like html.ie7, html.ie8,…(from HTML5 Boilerplate), Modernizer-detection of features (view classes html.js.flexbox.canvas.no-touch…) and JS-detection of browser and platform (for example, CSS Browser Selector generating view classes html.webkit.chrome.chrome25.win.win8…)
Bad - not checking tabindex on forms.
It's bad to write styles without thinking about the logic of the elements' placement. For example, if an element is always on top, it should have a large z-index, you can't hope that everything looks fine now - the styles should be reinforced concrete. If an element should always be in some place, regardless of the surrounding elements, this is position: absolute; not float, etc. Blocks that are independent of each other should not be inside the same block (for example, company phone number and site search). Blocks that are independent of each other should be position absolute, not floated.
Very bad - presentation classes (right, red).
It is undesirable when the layout contains empty blocks for presentation purposes, for this there are pseudo-elements
It's bad when standard elements do not have basic styles. Those. just h1, h2, ul, table, etc without classes should look nice and organic. Simply put - use Normalize, not Reset CSS.
It's bad when there is no gradual refinement of styles for the text, when the style is written for each element separately, and outside of it - the appearance can be radically different. We are talking about a situation when, for example, text written without paragraphs has a completely different style than all the elements in the block. It is necessary to lead the styles from the bottom up, gradually refining them. It is important not to confuse text styles and block styles here. For text - a cascade is good, for site blocks - you need to use BEM.
Worse, overly detailed global styles. For example a {font: italic 10px Tahoma;}/ * Hate! Hatred! HATE !! 11 * / Then you have to override the link style for each block.
The dimensions and positioning of the element must be specified in the same units of measurement. Those. block height / width in px and margin / padding in em is strange and most likely a bug. Line-height - it is better to set it by a factor (1 / 1.2 / 1.4 ... i.e. without specifying the unit of measurement - this is the number by which the font-size is multiplied and the line spacing will be obtained). If we set the font-size / height in em, then we set the margin / padding in em too. Classic example: list dl-dt-dd, where dt and dd are stacked against each other by pulling dd up with a negative margin. Or - we allocated a padding space under the position: absolute of some text block. For text elements (paragraph, table cells), set padding and height in em (to correctly increase the font size).
It is bad (unacceptable!) To hang styles on the selectors of nested standard tags, without classes. Those. let's say we write something like h2 a span {какая-то крепкая штука, типа картинки с графикой, что закрывает текст в заголовке}, and then the client in the vizig suddenly drives in such a combination! And we get an incredible bug. On just single tags to display text from the database - it is possible, but using the .b-text block (see BEM CSS).
Bad - directly set the visual display elements through js: $('.element').css(color,"#f00"). This should be done through setting / changing classes.
Okay:

BEM ! It is important to understand that this is a methodology, not tools. For ordinary sites, layout using BEM CSS is enough , without using a block library and bem-tools. For a long time I thought that “BEM is a great idea, but this is too much, so categorically it is not necessary, it is necessary a little differently, for yourself ...” , and so - this is not true! It is imperative to leave the cascade, and BEM is one of the great solutions.
It's good to structure the code into blocks that describe the logic of the document. Those. create a div even where it is not needed for presentation purposes. And vice versa - try not to put an extra div where the structure does not require it, and this is necessary only for visual effects.
HTML5 Boilerplate  is a great starter template from the fathers. Use and join development, add your bikes there! Previously, we had our own self-written framework-starting html, now we use Boilerplate as a basis, and we are already adding old developments to it.
Use well-established solutions, other people's modules, jQuery plugins, don't reinvent the wheel, but if you do, support them, maintain the code library (add code there after each new project, update the old one).
For text blocks that are edited in the admin panel, the atomicity of text styles must be ensured. Those. we have a page with some kind of text block, something like this: `` '' css .content-text h1 .content-text .entry .content-text .entry .somenamedblock `` Then .somenamedblock must receive text styles directly - .somenamedblock {font: …; color: …;}since otherwise, we will not be able to freeze them in the admin panel visig.
the same html-code for the blocks on the face and inside, with identical content, but different visual presentation of data. It is implemented through block and element modifiers, but not through the modification from the parent (cascade from body.pagename for example!)
Important little things
The logo on the inner liners should lead to the title. On the title, logo = h1, on the inner liners, H1 = content title, and Logo = div
Each page must have its own unique TITLE format About Us — %CompanyName%
All pages must be linked and  checked for broken links .
All links should somehow react to: hover,: active and: focus - by showing / removing the underline, changing the color, whatever. All links except menu items must have a reaction to: visited
Check that all interactive elements of the page that should work - work.
"Content at the beginning of the page" - the content of the page should go at the beginning of the code, before any sidebars and other things.
All created pages should initially be cut into templates to make it easier for the programmer to integrate them.
The copyright must be correct .
There should be a favicon.ico (preferably with 32 × 32, 48 × 48 and 64 × 64 variations included inside it) and an apple-touch-icon
The layout should not contain pieces of code commented out "just in case", unnecessary unused files, old versions of files, etc. All backups can be pulled from the version control system (for example, Git or SVN), and on a live project, "garbage" then prevents you from figuring out how what works.
Sizes for boxes whose sizes depend on the text they contain should be specified in em, not px.
If the url of the link is unknown, then it must be equal to its anchor, written in Latin, with spaces / special characters replaced with dashes.
Skype plugin shouldn't break the layout
Resize textarea should not break the layout
When checking the frontend as a whole, a 404 page should be returned with a 404 code, not 200.
You need to be on the safe side by fixing the sizes of images displayed programmatically in css.
Check spelling by Word or Spelling , preferably - to print the content.
Links to other people's sites should be with  target="_blank", it is desirable to highlight them with an "external link" icon.
Of course, pictures should be in a separate folder, css - in a separate one and js - in a separate one. Graphics that are not part of the design (all sorts of illustrations, photos in the news, etc.) - must be placed in a separate folder, for example userfiles.
Images should be scaled based on window size (max-width:100%; height:auto;)
