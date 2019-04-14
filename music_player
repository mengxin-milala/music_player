import os
import time
from tkinter import scrolledtext
from tkinter import filedialog
from tkinter import *
import os.path
import pygame
pygame.init()
pygame.mixer.init()

wd = Tk()
wd.title("音乐播放器1.0")
wd.geometry("600x600")

#歌曲名字变量
varlabelmusicname = StringVar()
varlabelmusicname.set("歌曲名字")

LANGS = [
    ("循环播放",1),
    ("随机播放",2),
    ("单曲循环",3)]
v4 = IntVar()
v4.set(1)


#找到MP3 返回一个列表
def find(path, x=[], s='.mp3'):
    
    if not os.path.isdir(path):
        return
    for i in os.listdir(path):
        file = os.path.join(path, i)

        if os.path.isdir(file):
            find(file, s)

        elif str(os.path.splitext(file)[1]) == s:
            x.append(file)
    return x

#找到一个文件夹，返回这个文件夹的路径
def ChoiceMusicMulu():
    
    global musicpath
    #获取某个文件夹下的音乐文件返回一个列表
    musicpath = filedialog.askdirectory()

    global musiclist
    musiclist = find(musicpath)
    for i in range(len(musiclist)):
        geming = os.path.split(musiclist[i])
        listboxgedan.insert(0, str(geming[1]))

def xiabiao(suiji):
    indexs = listboxgedan.curselection()
    index = int(indexs[0])
    xiabiao = index
    varlabelmusicname.set(str(listboxgedan.get(xiabiao)))
    return xiabiao

def MuluPlay():
    geming = os.path.split(musiclist[len(musiclist)-xiabiao(1)-1])
    pygame.mixer.music.load(musicpath+'/'+str(geming[1]))
    pygame.mixer.music.play(1)
    
def Pause():
    pygame.mixer.music.pause()

def Unpause():
    pygame.mixer.music.unpause()
 
def Next():
    i = (i+1)%len(musiclist)
    pygame.mixer.music.load(os.path.split(musiclist[i+1]))
    pygame.mixer.music.play()

def Shang():
    pass

def Stop():
    pygame.mixer.music.stop()

listboxgedan = Listbox(wd)
listboxgedan.place(x=50, y=150, width=400, height=350)


pygame.mixer.music.set_volume(0.2)

buttonAdd = Button(wd, text="选择目录", command=ChoiceMusicMulu)
buttonAdd.place(x=100, y=50)

buttonPlay = Button(wd, text="播放", command=MuluPlay)
buttonPlay.place(x=200, y=50)

buttonPause = Button(wd, text="暂停", command=Pause)
buttonPause.place(x=200, y=100)

buttonUnpause = Button(wd, text="继续", command=Unpause)
buttonUnpause.place(x=250, y=100)

buttonNext = Button(wd, text="下一首", command=Next)
buttonNext.place(x=300, y=100)

buttonShangyishou = Button(wd, text="上一首", command=Shang)
buttonShangyishou.place(x=150, y=100)

buttonStop = Button(wd, text="停止", command=Stop)
buttonStop.place(x=250, y=50)

group = LabelFrame(wd, text="播放模式:", padx=5, pady=5)
group.place(x=450, y=25)

for lang, num in LANGS:
    l = Radiobutton(group, text=lang, variable=v4, value=num, indicatoron=False)
    l.pack(anchor=N)

mainloop()
