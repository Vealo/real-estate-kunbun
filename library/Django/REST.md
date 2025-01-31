## REST

Representational State Transfer — это архитектура, т.е. принципы построения распределенных гипермедиа систем, того что другими словами называется World Wide Web, включая универсальные способы обработки и передачи состояний ресурсов по HTTP.

Автор идеи и термина Рой Филдинг 2000г. REST на сегодняшний день практически вытеснил все остальные подходы, в том числе дизайн основанный на SOAP и WSDL.

### Что нам дает REST подход?

- Масштабируемости взаимодействия компонентов системы (приложения)
- Общность интерфейсов
- Независимое внедрение компонентов
- Промежуточные компоненты, снижающие задержку, усиливающие безопасность

### Когда использовать REST?

- Когда есть ограничение пропускной способности соединения
- Если необходимо кэшировать запросы
- Если система предполагает значительное масштабирование
- В сервисах, использующих AJAX

### Преимущества REST:

- Отсутствие дополнительных внутренних прослоек, что означает передачу данных в том же виде, что и сами данные. Т.е. данные не оборачиваются в XML, как это делает SOAP и XML-RPC, не используется AMF, как это делает Flash и т.д. Просто отдаются сами данные.
    
- Каждая единица информации (ресурс) однозначно определяется URL — это значит, что URL по сути является первичным ключом для единицы данных. Причем совершенно не имеет значения, в каком формате находятся данные по адресу — это может быть и HTML, и jpeg, и документ Microsoft Word.
    
- Как происходит управление информацией ресурса — это целиком и полностью основывается на протоколе передачи данных. Наиболее распространенный протокол конечно же HTTP. Для HTTP действие над данными задается с помощью методов : GET (получить), PUT (добавить, заменить), POST (добавить, изменить, удалить), DELETE (удалить). Таким образом, действия CRUD (Create-Read-Update-Delete) могут выполняться как со всеми 4-мя методами, так и только с помощью GET и POST.
    

###   
Правила REST:

- **Модель клиент-сервер:**  
    Первым ограничением, применимым к гибридной модели, является приведение архитектуры к модели клиент-сервер. Разграничение потребностей является принципом, лежащим в основе данного накладываемого ограничения.  
    Отделение потребности интерфейса клиента от потребностей сервера, хранящего данные, повышает переносимость кода клиентского интерфейса на другие платформы, а упрощение серверной части улучшает масштабируемость.  
    Наибольшее же влияние на всемирную паутину, пожалуй, имеет само разграничение, которое позволяет отдельным частям развиваться независимо друг от друга, поддерживая потребности в развитии интернета со стороны различных организаций.

- **Отсутствие состояния:**  
    Протокол взаимодействия между клиентом и сервером требует соблюдения следующего условия: в период между запросами клиента никакая информация о состоянии клиента на сервере не хранится (Stateless protocol или «протокол без сохранения состояния»).  
    Все запросы от клиента должны быть составлены так, чтобы сервер получил всю необходимую информацию для выполнения запроса. Состояние сессии при этом сохраняется на стороне клиента.  
    Информация о состоянии сессии может быть передана сервером какому-либо другому сервису (например, в службу базы данных) для поддержания устойчивого состояния, например, на период установления аутентификации.  
    Клиент инициирует отправку запросов, когда он готов (возникает необходимость) перейти в новое состояние. Во время обработки клиентских запросов считается, что клиент находится в переходном состоянии.  
    Каждое отдельное состояние приложения представлено связями, которые могут быть задействованы при следующем обращении клиента.

- **Кэширование:**  
    Как и во Всемирной паутине, клиенты, а также промежуточные узлы, могут выполнять кэширование ответов сервера.  
    Ответы сервера, в свою очередь, должны иметь явное или неявное обозначение как кэшируемые или некэшируемые с целью предотвращения получения клиентами устаревших или неверных данных в ответ на последующие запросы.  
    Правильное использование кэширования способно частично или полностью устранить некоторые проблемы клиент-серверного взаимодействия, ещё больше повышая производительность и масштабируемость системы.

- **Единообразие интерфейса:**  
    Наличие унифицированного интерфейса является фундаментальным требованием дизайна REST-сервисов. Унифицированные интерфейсы позволяют каждому из сервисов развиваться независимо.  
      
    К унифицированным интерфейсам предъявляются следующие четыре ограничительных условия:
    - Идентификация ресурсов:  
        Все ресурсы идентифицируются в запросах, например, с использованием URI в интернет-системах.  
        Ресурсы концептуально отделены от представлений, которые возвращаются клиентам. Например, сервер может отсылать данные из базы данных в виде HTML, XML или JSON, ни один из которых не является типом хранения внутри сервера.  
         
    - Манипуляция ресурсами через представление:  
        Если клиент хранит представление ресурса, включая метаданные — он обладает достаточной информацией для модификации или удаления ресурса.  
         
    - «Самоописываемые» сообщения:  
        Каждое сообщение содержит достаточно информации, чтобы понять, каким образом его обрабатывать. К примеру, обработчик сообщения (parser), необходимый для извлечения данных, может быть указан в списке MIME-типов.  
         
    - Гипермедиа как средство изменения состояния приложения:  
        Клиенты изменяют состояние системы только через действия, которые динамически определены в гипермедиа на сервере (к примеру, гиперссылки в гипертексте). Исключая простые точки входа в приложение, клиент не может предположить, что доступна какая-то операция над каким-то ресурсом, если не получил информацию об этом в предыдущих запросах к серверу.

- **Слои:**  
    Клиент обычно не способен точно определить, взаимодействует ли он напрямую с сервером или же с промежуточным узлом, в связи с иерархической структурой сетей (подразумевая, что такая структура образует слои).  
    Применение промежуточных серверов способно повысить масштабируемость за счёт балансировки нагрузки и распределённого кэширования.  
    Промежуточные узлы также могут подчиняться политике безопасности с целью обеспечения конфиденциальности информации.

- **Код по требованию (необязательное):**  
    REST может позволить расширить функциональность клиента за счёт загрузки кода с сервера в виде апплетов или скриптов.

  
Давайте представим сообщения от Клиента к Серверу через Web API в стиле REST.

У нас есть объект Кошка, и мы хотим создать запись о кошке на Сервере. Для этого мы отправляем запрос на сервер:

`POST http://www.pets-server.ru/cats/`

С данными в теле запроса

``` json
Name: "My Best Cat"
Color: "Red"
Age: 2
```

Плюс к этому запросу (и всем другим) может быть добавлен ключ аутентификации.

`Auth-Token: "IPjxTy7Lodas343Fswv2"`

Ключ будет нужен, чтобы Сервер понял, что запрос происходит от авторизованного Клиента. Как мы помним из правила REST, каждый запрос от Клиента должен содержать всю необходимую информацию для обработки этого запроса Сервером. Здесь это правило работает: Сервер ничего не знает о Клиенте до запроса, но сам запрос содержит ключ авторизации, по которому Сервер определяет, что это за Клиент.

Сервер ответит на этот запрос вот таким сообщением:

``` json
Id: 21
Name: "My Best Cat"
Color: "Red"
Age: 2
```

Сервер взял все поля, переданные клиентом, и добавил к ним поле `Id`. Здесь работает правило REST, согласно которому каждый ресурс должен иметь уникальный идентификатор и быть доступным по определенному URL. Сервер создал ресурс и вернул нам его `Id`.

Теперь мы можем получить данную запись по URL:

`GET http://www.pets-server.ru/cats/21`

Ответ сервера:

``` json
Id: 21
Name: "My Best Cat"
Color: "Red"
Age: 2
```

Что, если Клиент хочет изменить созданные им данные на сервере?

Отправляем запрос:

`PUT http://www.pets-server.ru/cats/21`

С телом запроса:

``` json
Name: "My Best Cat"
Color: "Black"
Age: 2
```

Ответ сервера:

``` json
Name: "My Best Cat"
Color: "Black"
Age: 2
```

Метод PUT используется для изменения данных. Номер `21` в URL говорит о том, какой именно объект нужно изменить. Теперь наша кошка имеет цвет `Black`.

Для удаления записи на Сервере достаточно отправить запрос:

`DELETE http://www.pets-server.ru/cats/21`

Тут также мы указываем в `Id` объекта в URL, но передавать никаких данных в теле запроса для удаления объекта уже не требуется.