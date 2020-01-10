# simple_chatbot
from chatterbot import ChatBot
from chatterbot.trainers import ListTrainer
from tkinter import *


# creating ChatBot

bot = ChatBot("My Bot")

//dataset
convo = [
   'Halo',
    'Hai!',
    'Apa kabarmu?',
    'Kabar baik',
    'Siapa namamu?',
    'Aku adalah chatbot yang dibuat oleh Debby',
    'Kamu tinggal dimana?',
    'Aku tinggal di Medan',
    'Kamu lagi apa?',
    'Aku sedang membaca buku',
    'Apa hobimu?',
    'Hobiku adalah membaca buku',


]

trainer = ListTrainer(bot)

# now training the bot with the help of trainer
trainer.train(convo)

#answer  = bot.get_response("what is your name?")
#print(answer)

#print("Talk To Bot")
#while True:
#    query = input()
#    if query == 'exit':
#        break
#    answer = bot.get_response(query)
#    print("bot : ", answer)

main = Tk()

main.geometry("500x650")

main.title("My Chatbot")
img=PhotoImage(file="bot.png")

photoL=Label(main,image=img)

photoL.pack(pady=5)

def ask_from_bot():
    query=textF.get()
    answer_from_bot = bot.get_response(query)
    msgs.insert(END, "you : " + query)
    print(type(answer_from_bot))
    msgs.insert(END, "bot : " + str(answer_from_bot))
    textF.delete(0, END)

frame=Frame(main)

sc=Scrollbar(frame)
msgs=Listbox(frame, width=80, height=20)

sc.pack(side=RIGHT, fill=Y)

msgs.pack(side=LEFT, fill=BOTH, pady=10)

frame.pack()

# creating text field
textF=Entry(main, font=("Verdana", 15))
textF.pack(fill=X, pady=8)

btn=Button(main, text="Tanya pada bot", font=("Verdana", 11), command=ask_from_bot)
btn.pack()
main.mainloop()
