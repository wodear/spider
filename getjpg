#coding=utf-8
from urllib.request import*
import re
from tkinter import *
from tkinter.filedialog import askdirectory


root = Tk()

def getHtml(url):
    page = urlopen(url)
    html = page.read()
    return html


        
class App:
    def __init__(self, master):
        
        frame1 = Frame(master)
        frame1.pack()
        frame2 = Frame(master)
        frame2.pack()
        
        #输入图片存储位置
        w = Label(frame1,text="输入存储位置")
        w.pack(side = LEFT)
        #浏览地址输入框
        v = StringVar()
        e1 = Entry(frame1,textvariable=v, width=60)
        v.set("")
        self.v = v
        e1.pack(side = LEFT)
        b1 = Button(frame1, text="浏览", command=self.askdirec, width=20)
        b1.pack(side = RIGHT)

        #输入网址
        w = Label(frame2,text="输入网站网址")
        w.pack(side = LEFT)
        #网址输入框
        
        self.e = Entry(frame2, width=60)
        self.e.pack( side = LEFT)
        b = Button(frame2, text="确认", command=self.say_hi, width=20)
        
        b.pack( side = RIGHT)

    
    def say_hi(self):
        if(self.e.get() != ""):
            html = getHtml(self.e.get())

            html = html.decode('utf-8')

            print(self.getImg(html))
            messagebox.showinfo("Congratulations！", "该网页所有图片已帮您下载到硬盘咯~")
        else:
            print("No url~")
            messagebox.showwarning("Errer", "No Url~")

    def getImg(self,html):
        reg = r'src="(.+?\.jpg)" '
        imgre = re.compile(reg)
        imglist = re.findall(imgre,html)
        #return imglist
    
        x = 0
        for imgurl in imglist:
            urlretrieve(imgurl, self.v.get() +'/ %s.jpg' % x)
            x+=1

    def askdirec(self):
        self.v.set(askdirectory())
        
app = App(root)
root.mainloop()

