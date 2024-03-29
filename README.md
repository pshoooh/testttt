import telebot
from telebot import types

# Telegram botunuzun API anahtarını buraya yazın
TOKEN = '6750148691:AAHrWphE5rf10Kxjtw9sqS70upUPu0njAF0'

# Bot nesnesini oluşturun
bot = telebot.TeleBot(TOKEN)

# /start komutuna cevap veren fonksiyon
@bot.message_handler(commands=['start'])
def send_welcome(message):
    # Başlangıç mesajını gönder
    bot.reply_to(message, "Hello, welcome! Please choose one:")

    # Butonları oluştur
    keyboard = types.InlineKeyboardMarkup(row_width=1)
    button1 = types.InlineKeyboardButton("F+ SIM", url="https://t.me/tapswap_bot?start=r_5541236874")
    button2 = types.InlineKeyboardButton("Gmail+", url="https://t.me/tapswap_bot?start=r_5541236874")
    button3 = types.InlineKeyboardButton("Free", url="https://t.me/tapswap_bot?start=r_5541236874")

    # Butonları klavyeye ekleyin
    keyboard.add(button1, button2, button3)

    # Klavyeyi mesaja ekleyin
    bot.send_message(message.chat.id, "Choose one option:", reply_markup=keyboard)

    # İngilizce mesajı gönder
    bot.send_message(message.chat.id, "You need to reach 3000 points")

# Sonsuz döngü
while True:
    try:
        # Botu çalıştırın
        bot.polling()

    except Exception as e:
        # Hata durumunda hata mesajını yazdırın
        print(e)