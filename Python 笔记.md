
# 计算机 & 编程是啥

计算机 --- > 工具人 : 计算机仅是电子元件的电信号通电或断电组合成的各种指令(汇编). 通过电路完成计算

编程 --- > 和计算机进行沟通并告诉计算机完成什么内容

# 编程语言

## 编程语言 
为了优化计算机和人之间更高效的通信, 为计算机的汇编改进沟通的方式,诞生了编程语言

就像是人类的语言, 汉语, 英语, 日语 ······

## 编程语言有哪些

汇编 、VB、 C[C++,C#]、JAVA、Python、GO、JS、HTML、JSP、Angular····

## 编程技术框架 

各种框架只要语言用的相同, 那他们仅仅相当于各种方言: JAVA [Spring,Springboot], JS[Vue,React]

## 项目

某一个项目所有代码是一个整体, 换句话说就是让计算机集中在一个岗位上干活. 干的就是项目划分范围的职责


# 计算机&编程语言的关系

为了和计算机进行沟通,让其完成某个岗位的内容,我们通过以下方式和计算机沟通

通过一定的编程语言给计算机交代任务内容, 为了我们更快的部署任务, 我们采用了一定的框架进行高效协作

# 编程环境

计算机默认仅支持汇编、安装系统后的C ++ .

我们安装Python 就是为了让计算机先学会这门语言, 知道这个语言是啥意思, 然后我们就能用Python 和计算机沟通

## 环境变量

计算机是一个大的团体, 但对于执行人来说, 他会默认安排一个地方进行默认行为, 

如我们给其一个命令时, 计算机会去默认地方找这个命令是啥意思, 但如果找不到, 就只能报错命令不存在[我听不懂你啥意思]

所以配置环境变量就是将我们安装的Python 命令 放到默认的位置, 以便我们下命令时计算机知道在干啥

## 不配环境变量能不能用Python

可以, 既然默认地方找不到, 那我们就在下命令时告诉计算机应该去哪里查找并理解这个命令

将计算机的执行人带到命令所在地, 然后再执行

```shell
cd /**/smk/
python3

/**/smk/python3

```


# Python 基础

## 保留字(关键字)

为了更好的沟通, 预定义了一些特殊意义的字, 只要遇到这些字, 那一定会安装预定义的意思理解, 我们无法干预, 因此当我们不按照要求使用保留字时, python 干脆给我们报错

如:
```python
True False 一定是真和假
import 
if else elif while for 

```
https://www.w3cschool.cn/python3/python3-basic-syntax.html

## 数据类型

用python 和计算机约定我们要命名某个变量 是啥类型, 以便计算机快速判断它能干啥事

如我们告诉它a 是数字时, 它就能按照我们的需要进行计算, 但如果是字符串 就不能计算, 但python 会安装语法来执行推测计算


```python
a = 3
a = "3"
a = "smk"
a = true
a = false
a = (3,4,5,6)
a = [1,2,3,4,5,6]
a = {"name":"smk","phone":"138****"}
a = {1,2,3,4,5,6}

print(a)
print(type(a))

```


# 简易计算器

```python
ex = "否"  
while ex == "否":  
    a = int(input("a:"))  
    b = int(input("b:"))  
    flag = input("flag:")  
  
    if flag == "+":  
        result = a + b  
    elif flag == "-":  
        result = a - b  
    elif flag == "*":  
        result = a * b  
    elif flag == "/":  
        result = a / b  
    elif flag == "**":  
        result = a ** b  
    else:  
        print("你输的不对!!!")  
  
    print(result)  
    ex = input("是否要退出:")
```

# 完整计算器

```python
import tkinter as tk  
  
allowSampleSign = ("+","-","**","//","*","/","%")  
allowSign = ("^","&","<<",">>")  
  
root = tk.Tk()  
  
  
# 设置窗口大小  
window_width = 800  
window_height = 600  
root.geometry(f"{window_width}x{window_height}")  
  
# 获取屏幕的宽度和高度  
screen_width = root.winfo_screenwidth()  
screen_height = root.winfo_screenheight()  
  
# 计算窗口的居中位置  
x = (screen_width // 2) - (window_width // 2)  
y = (screen_height // 2) - (window_height // 2)  
  
# 设置窗口位置  
root.geometry(f"{window_width}x{window_height}+{x}+{y}")  
root.title( "计算器")  
root.wm_attributes("-type", "dialog")  
  
def calcresult(content:str):  
    result = eval(content)  
    result_area.delete("1.0", tk.END)  
    result_area.insert(tk.END, result)  
  
def on_key_press(event):  
    content = text_area.get("1.0", tk.END)  
    if content.endswith("\n"):  
        content = content[:-1]  
    if not content.strip() and (event.char in allowSampleSign or event.char in allowSign) :  
        return "break"  
  
    if (event.char in allowSampleSign or event.char in allowSign) and (content[-1] in allowSampleSign or content[-1] in allowSign) :  
        return "break"  
    if event.keysym == "Return":  
        if(content[-1] in allowSign or content[-1] in allowSampleSign):  
            return "break"  
        else :  
            calcresult(content)  
    if not (event.char.isdigit() or event.char == "." or event.keysym == "BackSpace" or event.char in allowSampleSign or event.char in allowSign):  
        return "break"  
  
text_area = tk.Text(root,height=10 , width=80)  
text_area.pack()  
text_area.bind("<KeyPress>", on_key_press)  
result_area = tk.Text(root,height=2 , width=10)  
result_area.place(x=600, y=100)  
def show_text(sign:str):  
    result = 0  
    if "=" == sign:  
        content = text_area.get("1.0", tk.END)  
        if content.endswith("\n"):  
            content = content[:-1]  
  
        calcresult(content)  
  
    else:  
        content = text_area.get("1.0", tk.END)  
        if content.endswith("\n"):  
            content = content[:-1]  
        if not content.strip() :  
            return  
        if content[-1] in allowSampleSign or content[-1] in allowSign:  
            return  
        else :  
            content += sign  
            text_area.insert(tk.END, sign)  
  
sample_frame = tk.Frame(root)  
# sample_frame.pack(side=tk.TOP, fill=tk.BOTH,expand=True)  
# sample_frame.pack_forget()  
def create_sample_calc():  
    line_index = 1  
    col_index = 1  
    for sign in allowSampleSign:  
        button = tk.Button(sample_frame,text=sign,command=lambda t=sign: show_text(t))  
        button.place(x=150 * col_index, y=150 +50* line_index)  
        if col_index > 3:  
            col_index = 0  
            line_index += 1  
  
        col_index += 1  
    else:  
  
        button = tk.Button(sample_frame, text="=",command=lambda : show_text("="))  
        button.pack()  
        button.place(x=150 * col_index, y=150 + 50 * line_index)  
    return  
calc_frame = tk.Frame(root)  
# calc_frame.pack(side=tk.TOP, fill=tk.BOTH, expand=True)  
# calc_frame.pack_forget()  
def create_calc():  
    line_index = 1  
    col_index = 1  
  
    for sign in allowSign:  
        button = tk.Button(calc_frame, text=sign,command=lambda t=sign: show_text(t))  
        button.place(x=150 * col_index, y=150 + 50 * line_index)  
        if col_index > 3:  
            col_index = 0  
            line_index += 1  
  
        col_index += 1  
    else:  
  
        button = tk.Button(calc_frame, text="=",command=lambda : show_text("="))  
        button.pack()  
        button.place(x=150 * col_index, y=150 + 50 * line_index)  
    return  
  
  
def show_sample_calc():  
  
    calc_frame.pack_forget()  
    sample_frame.pack(side=tk.TOP, fill=tk.BOTH, expand=True)  
  
  
def show_calc():  
    calc_frame.pack(side=tk.TOP, fill=tk.BOTH, expand=True)  
    sample_frame.pack_forget()  
  
sampleButton=tk.Button(root,text="数学计算器",command=show_sample_calc)  
sampleButton.place(x=10,y=10)  
calcButton = tk.Button(root,text="复杂计算器",command=show_calc)  
calcButton.place(x=10,y=50)  
  
create_sample_calc()  
create_calc()  
root.mainloop()
```


# 方法 & 类

# 封装? 继承? 