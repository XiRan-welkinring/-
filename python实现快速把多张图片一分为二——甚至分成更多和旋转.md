# python实现快速把多张图片一分为二——甚至分成更多和旋转

因为笔者最近由于学习（娱乐）需要，需要把大量图片从中间一分为二。我翻遍了也没有找到这样的方法或者程序只好学以致用拿python写了一个。

主要使用了pillow库和os库，文章末尾会附一下参考链接

因为不会写函数（实际是写出来运行不了...）只好写两遍来达成对应目标了

需要注意的是要切割的那个文件夹里面不能有图片以外的文件格式，否则读取到的时候会报错（应该写个分支就能过滤掉）

截取图片所用的集合坐标(box)分别是要截取的部分的左上角和右下角；图片左上角坐标为(0,0), 右下角坐标是长宽的最大值

由于文件原因这里就不放我的结果预览啦

## 1.遍历一个文件夹中所有图片并把它们一分为二

```python
from PIL import Image
import os

path = 'X:\\文件\\新建文件夹'   #文件目录
#path这个目录处理完之后需要手动更改
path_list = os.listdir(path)
#path_list.remove('.DS_Store')   #macos中的文件管理文件，默认隐藏，这里可以忽略，如果是mac可能需要加回这行（笔者没有用过mac）
print(path_list)

for i in path_list: #截左半张图片
    a = open(os.path.join(path,i),'rb')
    img = Image.open(a)
    w = img.width       #图片的宽
    h = img.height      #图片的高
    print('正在处理图片',i,'宽',w,'长',h)

    box = (0,0,w*0.5,h) #box元组内分别是 所处理图片中想要截取的部分的 左上角和右下角的坐标
    img = img.crop(box)
    print('正在截取左半张图...')
    img.save('L'+i) #这里需要对截出的图加一个字母进行标识，防止名称相同导致覆盖
    print('L-',i,'保存成功')

for i in path_list: #截取右半张图片
    a = open(os.path.join(path,i),'rb')
    img = Image.open(a)
    w = img.width       #图片的宽
    h = img.height      #图片的高
    print('正在处理图片',i,'宽',w,'长',h)

    box = (w*0.5,0,w,h)
    img = img.crop(box)
    print('正在截取右半张图...')
    img.save('R'+i)
    print('R-',i,'保存成功')
    
print("'{}'目录下所有图片已经保存到本文件目录下。".format(path))


```

## 2.遍历一个文件夹中所有图片并把它们一分为十

同理，当需要截取图片的十个部分时可以增加运行次数并更改参数：

```python
from PIL import Image
import os

path = 'X:\\文件\\拼图a4'   #文件目录
#path这个目录截完之后需要手动更改
path_list = os.listdir(path)
print(path_list)

for i in path_list:
    a = open(os.path.join(path,i),'rb')
    img = Image.open(a)
    w = img.width       #图片的宽
    h = img.height      #图片的高
    print('正在处理图片',i,'宽',w,'长',h)

    box = (0,0,w*0.1,h)
    img = img.crop(box)
    print('正在截取第一部分...')
    img.save('A'+i)
    print('A-',i,'保存成功')

for i in path_list:
    a = open(os.path.join(path,i),'rb')
    img = Image.open(a)
    w = img.width       #图片的宽
    h = img.height      #图片的高
    print('正在处理图片',i,'宽',w,'长',h)

    box = (w*0.1,0,w*0.2,h)
    img = img.crop(box)
    print('正在截取第二部分...')
    img.save('B'+i)
    print('B-',i,'保存成功')

for i in path_list:
    a = open(os.path.join(path,i),'rb')
    img = Image.open(a)
    w = img.width       #图片的宽
    h = img.height      #图片的高
    print('正在处理图片',i,'宽',w,'长',h)

    box = (w*0.2,0,w*0.3,h)
    img = img.crop(box)
    print('正在截取第三部分...')
    img.save('C'+i)
    print('C-',i,'保存成功')

for i in path_list:
    a = open(os.path.join(path,i),'rb')
    img = Image.open(a)
    w = img.width       #图片的宽
    h = img.height      #图片的高
    print('正在处理图片',i,'宽',w,'长',h)

    box = (w*0.3,0,w*0.4,h)
    img = img.crop(box)
    print('正在截取第四部分...')
    img.save('D'+i)
    print('D-',i,'保存成功')

for i in path_list:
    a = open(os.path.join(path,i),'rb')
    img = Image.open(a)
    w = img.width       #图片的宽
    h = img.height      #图片的高
    print('正在处理图片',i,'宽',w,'长',h)

    box = (w*0.4,0,w*0.5,h)
    img = img.crop(box)
    print('正在截取第五部分...')
    img.save('E'+i)
    print('E-',i,'保存成功')

for i in path_list:
    a = open(os.path.join(path,i),'rb')
    img = Image.open(a)
    w = img.width       #图片的宽
    h = img.height      #图片的高
    print('正在处理图片',i,'宽',w,'长',h)

    box = (w*0.5,0,w*0.6,h)
    img = img.crop(box)
    print('正在截取第六部分...')
    img.save('F'+i)
    print('F-',i,'保存成功')

for i in path_list:
    a = open(os.path.join(path,i),'rb')
    img = Image.open(a)
    w = img.width       #图片的宽
    h = img.height      #图片的高
    print('正在处理图片',i,'宽',w,'长',h)

    box = (w*0.6,0,w*0.7,h)
    img = img.crop(box)
    print('正在截取第七部分...')
    img.save('G'+i)
    print('G-',i,'保存成功')

for i in path_list:
    a = open(os.path.join(path,i),'rb')
    img = Image.open(a)
    w = img.width       #图片的宽
    h = img.height      #图片的高
    print('正在处理图片',i,'宽',w,'长',h)

    box = (w*0.7,0,w*0.8,h)
    img = img.crop(box)
    print('正在截取第八部分...')
    img.save('H'+i)
    print('H-',i,'保存成功')

for i in path_list:
    a = open(os.path.join(path,i),'rb')
    img = Image.open(a)
    w = img.width       #图片的宽
    h = img.height      #图片的高
    print('正在处理图片',i,'宽',w,'长',h)

    box = (w*0.8,0,w*0.9,h)
    img = img.crop(box)
    print('正在截取第九部分...')
    img.save('I'+i)
    print('I-',i,'保存成功')

for i in path_list:
    a = open(os.path.join(path,i),'rb')
    img = Image.open(a)
    w = img.width       #图片的宽
    h = img.height      #图片的高
    print('正在处理图片',i,'宽',w,'长',h)

    box = (w*0.9,0,w,h)
    img = img.crop(box)
    print('正在截取第十部分...')
    img.save('J'+i)
    print('J-',i,'保存成功')

print("'{}'目录下所有图片已经保存到本文件目录下。".format(path))


```

## 3.遍历一个文件夹中所有图片并把它们按宽度旋转

通过pillow库我们还可以来顺带旋转图片到自己想要的方向：

```python
from PIL import Image
import os

path = 'X:\\文件\\新建文件夹'   #文件目录
#path这个目录截完之后需要手动更改
path_list = os.listdir(path)
print(path_list)

for i in path_list:
    a = open(os.path.join(path,i),'rb')
    img = Image.open(a)
    w = img.width       #图片的宽
    h = img.height      #图片的高
    print('正在处理图片',i,'宽',w,'长',h)
    if h > w:
        img.rotate(270, expand=True).save('0'+i) #这里具体去看pillow里的rotate方法
        print('旋转成功')
    
print("'{}'目录下所有图片已经保存到本文件目录下。".format(path))


```

## 参考

pillow.Image常用操作如图片裁剪，旋转，缩放，翻转等https://blog.csdn.net/weixin_42074867/article/details/90440294

操作图像4-pillow-旋转,翻转图像、更改单个元素https://blog.csdn.net/qq_36482772/article/details/53346511

Python实现图片裁剪的两种方式——Pillow和OpenCVhttps://blog.csdn.net/hfutdog/article/details/82351549

python顺序读取文件夹中的图片方法https://blog.csdn.net/gbz3300255/article/details/108238083

Python获取文件夹下的文件和子文件夹(https://blog.csdn.net/JohinieLi/article/details/76660733)

