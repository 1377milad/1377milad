from telegram import Update
from telegram.ext import Updater, CommandHandler, CallbackContext
import random

# تابعی برای ارسال رفتارهای همستر
def hamster_behavior(update: Update, context: CallbackContext) -> None:
    behaviors = [
        "همستر در حال دویدن است!",
        "همستر در حال خوردن دانه است!",
        "همستر در حال خوابیدن است!",
        "همستر با سرعت در حال دویدن روی چرخ است!",
        "همستر با خوشحالی در حال کاوش در اطراف است!"
    ]
    response = random.choice(behaviors)
    update.message.reply_text(response)

# تابع برای شروع ربات
def start(update: Update, context: CallbackContext) -> None:
    update.message.reply_text('سلام! من یک همستر ربات هستم. برای دیدن رفتارهای همستر از دستور /hamster استفاده کن.')

def main():
    # توکن ربات شما وارد شده است
    updater = Updater("8087872727:AAG6_Fy_SL6z-s_cJkojfihiBUVd-UfvSRM")

    # دستورات ربات
    dp = updater.dispatcher
    dp.add_handler(CommandHandler("start", start))
    dp.add_handler(CommandHandler("hamster", hamster_behavior))

    # شروع ربات
    updater.start_polling()

    updater.idle()

if __name__ == '__main__':
    main()
