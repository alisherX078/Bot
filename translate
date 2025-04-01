import telebot
from telebot.types import Message
from deep_translator import GoogleTranslator

TOKEN = '7381640788:AAHxN4l1765y6M1xTveCpUXoF4kl7kHKSno'

bot = telebot.TeleBot(TOKEN)


def translate_text(text: str, target_lang: str = "fr") -> str:
    """Переводит текст на целевой язык."""
    try:
        translator = GoogleTranslator(source="auto", target=target_lang)
        return translator.translate(text)
    except Exception as e:
        return f"Ошибка перевода: {e}"


@bot.message_handler(commands=["start", "help"])
def send_welcome(message: Message):
    """Отправляет приветственное сообщение."""
    bot.reply_to(message, "Привет! Отправь мне текст, и я его переведу на английский.")


@bot.message_handler(func=lambda message: True)
def handle_message(message: Message):
    """Обрабатывает входящие сообщения и переводит их."""
    translated_text = translate_text(message.text, "fr")
    bot.reply_to(message, f"Перевод: {translated_text}")


if __name__ == "__main__":
    bot.polling(none_stop=True)
