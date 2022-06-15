# python-bot-
    import telebot

    from telebot import types

# ТОКЕН БОТА
# 5329117487:AAFC_tvYm45CMBEypBEFhXIHAxenL1ZHjtw @Библиотекарь
# 5394024692:AAHGTFRmD-V8UZNJaqJl9_N_reGVUyegrOw @Библиотека

    token = '5329117487:AAFC_tvYm45CMBEypBEFhXIHAxenL1ZHjtw'
    bot = telebot.TeleBot(token)


    @bot.message_handler(commands=['start'])
    def start_menu(message):
    bot.send_message(message.chat.id,
                     'Хотите почитать? '
                     '\n\nУ нас множество книг на любой вкус'
                     '\n\nДля перехода к списку жанров - /genre'
                     '\n\nНе нашли того чего искали? '
                     '\nЗдесь подробная инструкция - /info'
                     '\nВаш запрос максимально быстро удовлетворят')


    @bot.message_handler(commands=['genre'])
    def genrer(message):
    markup_inline = types.InlineKeyboardMarkup()
    item_lit = types.InlineKeyboardButton(text='Классика', callback_data='lit')
    item_strah = types.InlineKeyboardButton(text='Наука', callback_data='strah')
    item_fantastic = types.InlineKeyboardButton(text='Фантастика', callback_data='fantastic')
    item_busine = types.InlineKeyboardButton(text='Бизнес', callback_data='busines')
    markup_inline.add(item_lit, item_strah, item_fantastic, item_busine)
    bot.send_message(message.chat.id, 'Выберите жанр', reply_markup=markup_inline)


            # Выбор книги
    @bot.callback_query_handler(func=lambda call: True)
     def books(call):
      if call.data == 'lit':
        literature = types.ReplyKeyboardMarkup(resize_keyboard=True)
        puskin = types.KeyboardButton('Таинственный остров')
        shukovskiy = types.KeyboardButton('Евгений Онегин')
        tolstoy = types.KeyboardButton('Алые Паруса')
        lermontov = types.KeyboardButton('Морской волк')
        back = types.KeyboardButton('/genre')
        literature.add(puskin, shukovskiy, tolstoy, lermontov, back)
        bot.send_message(call.message.chat.id, 'Выберите книгу:', reply_markup=literature)
   
    elif call.data == 'strah':
        strah = types.ReplyKeyboardMarkup()
        hrebty = types.KeyboardButton('История России')
        tayny = types.KeyboardButton('Самогон')
        priut = types.KeyboardButton('Гравитация и эфир')
        back = types.KeyboardButton('/genre')
        strah.add(hrebty, tayny, priut, back)
        bot.send_message(call.message.chat.id, 'Выберите книгу:', reply_markup=strah)

    elif call.data == 'fantastic':
        fantasy = types.ReplyKeyboardMarkup()
        king = types.KeyboardButton('Последний бой')
        king2 = types.KeyboardButton('Любовь не с первого взгляда')
        king3 = types.KeyboardButton('Подари мне крылья')
        back = types.KeyboardButton('/genre')
        fantasy.add(king, king2, king3, back)
        bot.send_message(call.message.chat.id, 'Выберите книгу:', reply_markup=fantasy)

    elif call.data == 'busines':
        business = types.ReplyKeyboardMarkup()
        error0 = types.KeyboardButton('Уязвимость 0 дня')
        good = types.KeyboardButton('SMM Handbook')
        rework = types.KeyboardButton('Путь.')
        happy = types.KeyboardButton('Как хорошему разработчику не стать плохим менеджером')
        back = types.KeyboardButton('/genre')
        business.add(error0,good ,rework ,happy, back )
        bot.send_message(call.message.chat.id, 'Выберите книгу:', reply_markup=business)


    @bot.message_handler(content_types=['text'])
    def url_list(message):

                                 #КЛАССИКА

    if message.text == 'Таинственный остров':
        bot.send_message(message.chat.id,
                         'Вот ссылка для скачивания книги'
                         '\nhttps://disk.yandex.ru/i/rIEqJVjCLpAODg'
                         '\nПриятного времяпровождения!')

    elif message.text == 'Евгений Онегин':
        bot.send_message(message.chat.id,
                         'Вот ссылка для скачивания книги'
                         '\nhttps://disk.yandex.ru/i/hNmFbs1rXtkmpQ'
                         '\nПриятного времяпровождения!')

    elif message.text == 'Алые Паруса':
        bot.send_message(message.chat.id,
                         'Вот ссылка для скачивания книги'
                         '\nhttps://disk.yandex.ru/i/BvrkPaIhT2YiBQ'
                         '\nПриятного времяпровождения!')

    elif message.text == 'Морской волк':
        bot.send_message(message.chat.id,
                         'Вот ссылка для скачивания книги'
                         '\nhttps://disk.yandex.ru/i/AKMx__R7qtKYkA'
                         '\nПриятного времяпровождения!')



                        #ФАНТАСТИКА


    elif message.text == 'Последний бой':
        bot.send_message(message.chat.id,
                         'Вот ссылка для скачивания книги'
                         '\nhttps://disk.yandex.ru/i/2QZm5KdV5qCMmQ'
                         '\nПриятного времяпровождения!')

    elif message.text == 'Любовь не с первого взгляда':
        bot.send_message(message.chat.id,
                         'Вот ссылка для скачивания книги'
                         '\nhttps://disk.yandex.ru/i/RaEJncl0VJFSfQ'
                         '\nПриятного времяпровождения!')

    elif message.text == 'Подари мне крылья':
        bot.send_message(message.chat.id,
                         'Вот ссылка для скачивания книги'
                         '\nhttps://disk.yandex.ru/i/PNLpKoWEGK_XbQ'
                         '\nПриятного времяпровождения!')


                         #НАУКА


     elif message.text == 'История России':
        bot.send_message(message.chat.id,
                         'Вот ссылка для скачивания книги'
                         '\nhttps://disk.yandex.ru/i/kZGpnSbcofBuig'
                         '\nПриятного времяпровождения!')

     elif message.text == 'Самогон':
        bot.send_message(message.chat.id,
                         'Вот ссылка для скачивания книги'
                         '\nhttps://disk.yandex.ru/i/Y5-KwnyEG10Qig'
                         '\nПриятного времяпровождения!')

     elif message.text == 'Гравитация и эфир':
        bot.send_message(message.chat.id,
                         'Вот ссылка для скачивания книги'
                         '\nhttps://disk.yandex.ru/i/5fAVsDNE4yQ2ZQ\
                         nПриятного времяпровождения!')



                     #БИЗНЕС



     elif message.text == 'Уязвимость 0 дня':
        bot.send_message(message.chat.id,
                         'Вот ссылка для скачивания книги'
                         '\nhttps://disk.yandex.ru/i/CvI3i1_YkEMQpA'
                         '\nПриятного времяпровождения!')



        elif message.text == 'SMM Handbook':
        bot.send_message(message.chat.id,
                         'Вот ссылка для скачивания книги'
                         '\nhttps://disk.yandex.ru/i/ACUAlo70Mlxedg'
                         '\nПриятного времяпровождения!')

      elif message.text == 'Путь.':
        bot.send_message(message.chat.id,
                         'Вот ссылка для скачивания книги'
                         '\nhttps://disk.yandex.ru/i/SUo_Ail3MWRBsQ'
                         '\nПриятного времяпровождения!')

     elif message.text == 'Как хорошему разработчику не стать плохим менеджером':
        bot.send_message(message.chat.id,
                         'Вот ссылка для скачивания книги'
                         '\nhttps://disk.yandex.ru/i/bu3sN0p7rTCLnQ'
                         '\nПриятного времяпровождения!')


bot.polling()
