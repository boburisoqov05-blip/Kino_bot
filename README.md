from telegram import Update
from telegram.ext import ApplicationBuilder, CommandHandler, ContextTypes, MessageHandler, filters

TOKEN = "8411940019:AAHMEXSL2iteLdmDPpHIM3kqxZReq7_SPYs"

KINOLAR = {
    "avatar": "https://t.me/kino_world_555/1",
    "spiderman": "https://t.me/kino_world_555kino_world_555/2",
}

async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text(
        "🎬 Kino botga xush kelibsiz!\n\n"
        "Kino nomini yozing:\nMasalan: avatar"
    )

async def kino_qidir(update: Update, context: ContextTypes.DEFAULT_TYPE):
    text = update.message.text.lower()
    if text in KINOLAR:
        await update.message.reply_text(f"🎥 Kino havolasi:\n{KINOLAR[text]}")
    else:
        await update.message.reply_text("❌ Bunday kino topilmadi")

app = ApplicationBuilder().token(TOKEN).build()
app.add_handler(CommandHandler("start", start))
app.add_handler(MessageHandler(filters.TEXT, kino_qidir))

app.run_polling()
