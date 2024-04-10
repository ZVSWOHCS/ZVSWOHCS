import telebot
from telebot import types
import random

@bot.message_handler(commands=['start'])
def start(message):
    markup = types.ReplyKeyboardMarkup(resize_keyboard=True)
    btn1 = types.KeyboardButton("👋 Привет")
    markup.add(btn1)
    bot.send_message(message.from_user.id, "👋 Привет!", reply_markup=markup)
    print(f"{message.from_user.first_name} {message.from_user.username} Старт")

@bot.message_handler(content_types=['text'])
def get_text_messages(message):
    if message.text == '👋 Привет':
        markup = types.ReplyKeyboardMarkup(resize_keyboard=True) #создание новых кнопок
        btn1 = types.KeyboardButton('A')
        btn2 = types.KeyboardButton('B')        
        btn4 = types.KeyboardButton('C')
        btn3 = types.KeyboardButton('D')
        markup.add(btn1,btn2)
        markup.add(btn3)
        markup.add(btn4)
        bot.send_message(message.from_user.id, 'Test', reply_markup=markup) #ответ бота
    
    elif message.text == 'A':
        bot.send_message(message.from_user.id, 'A', parse_mode='Markdown')
    
    elif message.text == 'B':
        bot.send_message(message.from_user.id, 'B', parse_mode='Markdown')
        
    elif message.text == 'C':
        bot.send_message(message.from_user.id, 'C', parse_mode='Markdown')
        
    elif message.text == 'D':
        bot.send_message(message.from_user.id,'D',parse_mode='Markdown')
                                                                                                                                                                                         
bot.polling(none_stop=True, interval=0) 
