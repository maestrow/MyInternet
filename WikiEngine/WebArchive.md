# Сохранение веб-страниц (в архив) 

Что может потребоваться сохранить:

- Статью Википедии, которую только что написал или в которую внес существенную правку. При этом можно сохранять ссылку на ревизию. 
- Собственный развернутый комментарий, оставленный в форуме, который хочется сохранить. 
- Ценную страницу в интернете, для которой существует вероятность удаления или нежелательных изменений.

### Функционал

- Хранение версий. Для одного URL можно хранить несколько версий страницы. Для версии существуют реквизиты: дата, комментарий.
- При сохранении URL с mime-типов html есть три варианта поведения: а) сохранять выделенный фрагмент, б) сохранять только html, в) сохранять html + картинки.

### Архитектура

Статья и веб-страница - это ресурс, у них общая таблица в БД. Версионность можно реализовать позже, версии - это отдельная табличка в БД, актуальная версия хранится в таблице ресурсов.


