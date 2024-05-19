# Шаблон для быстрого создания бота

## **Удобная админ панель**

![enter image description here](https://media.discordapp.net/attachments/1016980262569128016/1241741279117971556/image.png?ex=664b4d2f&is=6649fbaf&hm=7be96932183494c7d44a56392807b95fee8a65998f8e8174d14577b34c36728e&=&format=webp&quality=lossless&width=378&height=291)
### Удобная рассылка
**Вы можете отправлять текст и картинки**

![enter image description here](https://media.discordapp.net/attachments/1016980262569128016/1241741900969672734/image.png?ex=664b4dc3&is=6649fc43&hm=9dcf1c042aa3169b8c4ea5d7d404cf361306dc906d3e6917b2fbd84668fc2607&=&format=webp&quality=lossless&width=653&height=593)

### Переключатели

**Функции которые можно включить и выключить**
![enter image description here](https://media.discordapp.net/attachments/1016980262569128016/1241742161926426674/image.png?ex=664b4e01&is=6649fc81&hm=2aed4b359a798ea0767cedc00e2bc60eabde7e650f8570ff51405101eb371c4c&=&format=webp&quality=lossless&width=670&height=235)

***Что делает 1 функция?***
Это функция отвечает за автоматическое открытие админ панели для админа при вводе команды */start*

## Встроенная анти флуд система

    async def anti_flood(*args, **kwargs):
		m = args[0]
		await m.answer("⚠Не так быстро!")
Данная функция отправляет сообщение при быстрой отправке запросов боту

***Как её используют?***

    @dp.message_handler(commands=['start'])
    @dp.throttled(anti_flood,rate=0.01)
    async def start(msg: types.Message):
	    print('Привет мир!')

Перед обозначением handler вставляем строку `@dp.throttled(anti_flood,rate=0.01)` где *rate* это время


## Сразу встроенная база данных на SQLITE3

***Что входит в базу данных?***
В бд используется 1 значение и это *Id*, которое автоматически заполняется при команде */start*

***Как брать значение юзера из базы данных***
За заполнение и нахождение профиля используется 1 функция и это *main* в файле `modules/db.py`

Для того чтобы взять значение достаточно ввести `db.main(msg)[0] #Берет id человека`
