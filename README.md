# Python_base
Python構文のメモ

## 標準入力
```
input = input("input")
```

## formt関数
```
print("私の名前は={}".format("name"))
→name
print("私の名前は={name}".format(name="name"))
→name

name=原口
print(f"私の名前は={name}")
→原口
```

## if 
```
AGE = 15

if AGE >= 20:
    print('aaaa')
else:
    print('bbbb')
```

## 演算
```
// 割り算、切り捨て
% 剰余
** べきじょう
<< >>シフト演算
& | 論理積、論理和
```

## 2、8、16進数
``` python
age = 0b111 # 2進数(7)

age = 0o11 # 8進数(9)

age = 0x11 # 16進数(17)
#文字列へ変換
print(bin(15))
print(oct(15))
print(hex(15))
```

## 文字列型について
```python
fruit = 'apple'

print(fruit)  # apple
print(type(fruit))  # apple
print(fruit * 10)  # appleappleappleappleappleappleappleappleappleapple

fruit2 = '''apple
banana
grape
'''
print(fruit2)  # 改行付きで出力できる

print(fruit[3])  # 前から何番目 l
print(fruit[-1])  # 後ろから何番目　e

```
### encode,decode => bytes[]
```python
fruit = 'apple'
byte_fruits = fruit.encode('utf-8')
print(byte_fruits)  # b'apple'
print(type(byte_fruits))  # <class 'bytes'>

str_fruits = byte_fruits.decode('utf-8')
print(str_fruits)  # apple
print(type(str_fruits))  # <class 'str'>
```


### count (文字の個数を調べる)
```python
msg = 'abcdefgABCabc'

print(msg.count('ABC')) #1
print(msg.count('abc')) #2

```

### startswith,endwidth(開始文字列、終了文字列が一致するか)
```python
msg = 'abcdefgABCabc'

print(msg.startswith('ABC'))  # False
print(msg.startswith('abc'))  # True
print(msg.endswith('abc'))  # True
print(msg.endswith('abce'))  # False
``` 

### strip(両端), rstrip(右端), lstrip(左端)　削除する
```python
msg = ' ABC '

print
print(msg.strip()) #ABC

msg = 'ABCDEFABC'

print(msg.strip('A')) #BCDABCDB
print(msg.strip('CBA')) #DEF
print(msg.rstrip('CBA')) #ABCDEF
print(msg.lstrip('CBA')) #DEFABC
```

### upper(大文字)　,lower(小文字),swapcase(大文字小文字入れ替え), replace(置換), capitalize(最初だけ大文字に変換)
```python
msg = 'abcABC'

msg_u = msg.upper()  # 大文字
msg_l = msg.lower()  # 小文字
msg_s = msg.swapcase()  # 大文字小文字入れ替え

print(msg_u, msg_l, msg_s)  # ABCABC abcabc ABCabc
msg = 'ABCDEABCABC'

msg_r = msg.replace('ABC','FFF') 

msg_r1 = msg.replace('ABC','FFF',1) #前から1個目まで変換
msg_r1_1 = msg.replace('ABC','FFF',2) #前から２個目まで変換
msg_r2 = msg.replace('ABC','FFF',-1) #全部変換

print(msg_r,msg_r1,msg_r1_1,msg_r2) #FFFDEFFFFFF FFFDEABCABC FFFDEFFFABC FFFDEFFFFFF

msg = 'hellow world'

print(msg.capitalize()) #Hellow world
```

### 文字列の一部取り出し,islower,isupper
```python
msg = 'hello, my name is taro'

print(msg[:5]) #最初から5まで（hello）
print(msg[6:]) #6から最後まで（ my name is taro）
print(msg[1:6]) #要素1から6まで（ello,）
print(msg[1:10:2]) #1から10まで、２個飛ばし（el,m ）

msg = 'apple'
print(msg.islower()) #True
print(msg.isupper()) #False
```


### find, index, rfind, rindex
```python
msg = 'ABCDEABC'

print(msg.find('ABC'))#左端から見つかった場所の要素が表示される(0)
print(msg.rfind('ABC'))#右端から見つかった場所の要素が表示される(5)
print(msg.index('ABC'))#左端から見つかった場所の要素が表示される(0)
print(msg.rindex('ABC'))#右端から見つかった場所の要素が表示される(5)


print(msg.find('ABCE'))#見つからなかったら-1
print(msg.index('ABCE'))#見つからなかったらエラー(ValueError: substring not found)
```

### append,extend,insert,clear
```python
list_a.append('apple')  # 要素の追加はappend
print(list_a)  # [10, 2, 3, 4, 'apple']
list_a.append(['apple', 'banana'])
print(list_a)  # [10, 2, 3, 4, 'apple', ['apple', 'banana']]

list_a.extend(['suika', 'ichigo'])  # extendではリストを一次元配列としてつなげることができる
print(list_a)  # [10, 2, 3, 4, 'apple', ['apple', 'banana'], 'suika', 'ichigo']

list_a.insert(1, 'grape')  # indexを指定して要素を追加する
print(list_a)  # [10, 2, 3, 4, 'apple', ['apple', 'banana'], 'suika', 'ichigo']
list_a.insert(4, 'orange')  # indexを指定して要素を追加する
# [10, 'grape', 2, 3, 'orange', 4, 'apple', ['apple', 'banana'], 'suika', 'ichigo']
print(list_a)

list_a.clear()  # listを空にする
print(list_a)　#[]

```
### remove,pop,count,index

```python
# removeは指定した値を左から探していき見つかったら削除するメソッド
list_a = [0, 0, 1, 1, 2, 2, 3, 3, 4, 4, 5, 5]
list_a.remove(3)  # 左から一番初めに出てきた3を削除する
print(list_a)  # [0, 0, 1, 1, 2, 2, 3, 4, 4, 5, 5]

list_b = ['apple', 'banana', 'kamaboko']
list_b.remove('kamaboko')  # 左から一番初めに出てきたkamabokoを削除する
print(list_b)  # ['apple', 'banana']

# popは一番最後の値を取り出す
value = list_b.pop()
print(list_b, value)

# countはlistの中に指定した値が何個あるかを返す
print(list_a.count(0))  # 2

# indexは左から探索して値が見つかった要素番号を返す,rindexとかはない
print(list_a.index(2))  # 4
# print(list_a.index(100)) #ValueError: 100 is not in list
```

### copy,sort,reverse
```python
# copyはリストをコピーできる
# 単純なイコールでのコピーは参照渡しになる為、cを書き換えたつもりがaも変わってしまう
list_c = list_a
print(list_c)  # [0, 0, 1, 1, 2, 2, 3, 4, 4, 5, 5]
list_c[0] = "apple"
print(list_a)  # ['apple', 0, 1, 1, 2, 2, 3, 4, 4, 5, 5]
print(list_c)  # ['apple', 0, 1, 1, 2, 2, 3, 4, 4, 5, 5]

# なので配列をコピーするときはcopyメソッドを使う
list_c = list_a.copy()
print(list_c)  # ['apple', 0, 1, 1, 2, 2, 3, 4, 4, 5, 5]
list_c[0] = "banana"
print(list_a)  # ['apple', 0, 1, 1, 2, 2, 3, 4, 4, 5, 5]
print(list_c)  # ['banana', 0, 1, 1, 2, 2, 3, 4, 4, 5, 5]

# sort,reverse
list_a = ['banana', 'apple', 'lemon']
list_a.sort()
print(list_a)  # ['apple', 'banana', 'lemon']
list_a.reverse()
print(list_a)  # ['lemon', 'banana', 'apple']

#sorted
list_a = sorted(list_a)
print(list_a)  # ['apple', 'banana', 'lemon']

```

### Dictionary(辞書型)
```python
car = {'brand': 'Toyota', 'model': 'Prius', 'year': '2015'}

# []で指定する方法、存在しない場合はKeyErrorが返る
print(car['brand'])  # Toyota
# print(car['aaaa'])  # KeyError: 'aaaa'

# .getで指定する方法、存在しない場合はNone、第二引数に値が設定してあったらその値が返る
print(car.get('brand'))  # Toyota
print(car.get('aaa'))  # None
print(car.get('aaa', '存在しない値だよ'))  # 存在しない値だよ

print(car.keys())  # keyの一覧を表示する、dict_keys(['brand', 'model', 'year'])

print(car.values())  # valueの一覧を表示する、dict_values(['Toyota', 'Prius', '2015'])

# keyとvalueのセット、全部が表示される、dict_items([('brand', 'Toyota'), ('model', 'Prius'), ('year', '2015')])
print(car.items())

for k, v in car.items():
    print(f'key = {k} value = {v}')

# carの中に'brand'のキーがあればTrue
if 'brand' in car:
    print('carのブランドは{}'.format(car.get('brand')))
```

##### 辞書型のメソッド
```python

tmp_car = {'country': 'japan', 'prefecture': 'Aichi', 'model': 'カローラ'}

car.update(tmp_car)  # 追加、更新

print(car)

car['city'] = 'toyota-si'  # これでも追加、更新できる
print(car)


value = car.popitem()  # 最後に追加した値を取り出せる
# {'brand': 'Toyota', 'model': 'カローラ', 'year': 2015, 'country': 'japan', 'prefecture': 'Aichi'}
print(car)
print(value)  # タプル型で取り出される ('city', 'toyota-si')

value = car.pop('model')  # キーを指定して値を取り出し

# {'brand': 'Toyota', 'year': 2015, 'country': 'japan', 'prefecture': 'Aichi'}
print(car)
print(value)  # valueだけ取り出される(カローラ)

car.clear()  # 変数を初期化

print(car)

del car  # 変数を削除
# print(car) #NameError: name 'car' is not defined
```

### タプル
+ タプルとはリストと似ていて値を複数入れることができる、値を変更削除できない
+ タプルのメリット
  - リストよりタプルの方がアクセスするスピードが速い
  - ハッシュ化して辞書型のキーとして利用できる
  - 値を変更したくない場合は保証ができる
```python
fruit = ('apple', 'banana', 'lemon')

print(type(fruit))
print(fruit[0])

fruit = fruit + ('grape',)  # タプルに要素を追加したい場合は再代入することによって追加できる

print(fruit)  # ('apple', 'banana', 'lemon', 'grape')

# リストをタプルに変換
list_fruit = ['apple', 'banana']
fruit = tuple(list_fruit)

print(fruit)  # ('apple', 'banana')
print(fruit.count('apple'))  # カウントする　→1
print(fruit.index('apple'))  # 検索する　→0(番目)


# 辞書型のキーにタプルを使用する方法（よくある方法）
pos = (135, 35)
countries = {pos: 'Japan'}

print(countries.get((135, 35)))  # Japan

```
### セット{}
リスト[]、タプル()と似たような複数の値を入れることが出来る

* 同じ値を持つことが出来ない
* 順序が保持されていない（重要）
* ユニオン、インターセクションなどの集合処理を高速で行える
* リストは入れられない(リストはハッシュ化できないため)

```python
set_a = {'a','b','c','a'} 

print(set_a) #{'a','b','c'} aは宣言で入れていても入らない

#セットの要素確認

#「'文字列' in セット」で確認できる
print('e' in set_a) # False
print('a' in set_a) # True
print('a' not in set_a) # False

#セットの長さの確認
print(len(set_a)) #4


#要素の追加
set_a.add('A')
print(set_a) # {'a','A','b','c'} 

#要素の削除
set_a.remove('a')
#set_a.remove('o') #存在しない要素を指定するとキーエラーとなる
print(set_a) # {'A','b','c'} 

#discard = 廃棄
set.discard('A')
set.discard('B') #discardは存在しない要素を指定してもエラーにはならない
print(set_a) # {'b','c'} 

val = set_a.pop()
print(val,set_a) # 'b'  {'c'} #セットのpopはランダムで値が取り出される。使いどころとしてはくじ引きプログラムとか？

#セットのクリア
set_a.clear()
print(set_a) #set()

```

#### セットのメソッド
使うときは基本的に記号を使ったほうが見やすいかも？

* union(|) ...和集合[合併]
* intersection(&) ...積集合[共通部分]
* defference(-) ...差集合[違い]
* symmetric_defference(^) ...どちらか一方にある要素の集合

* set_a.issubset(set_b) ... set_aの要素が全てset_bに含まれている場合は、set_aはset_bのサブセットということでTrueを返す。
* set_b.issuperset(set_a) ... set_aの要素が全てset_bに含まれている場合は、set_bはset_aのスーパーセットということでTrueを返す。
* set_b.isdisjoint(set_c) ... set_bの要素とset_cの要素が1つも被っていない場合Trueを返す

```python
s = {'a','b','c','d'}
t = {'c','d','e','f'}

#和集合
u = s | t
#u = s.union(t)
#s |= t #そのまま合体させることもできる
print(u) # {'a','b','c','d','e','f'}(セットだから順不同)

#積集合
u = s & t 
# u = s.intersection(t)
print(u) # {'c','d'}

#差集合
u = s - t 
# u = s.deffernce(t)
print(u) # {'a','b'}

#どちらか一方に含まれているけど両方に含まれていない要素
u = s ^ t
# s.symmetric_defference(t)
print(u) # {'a','b','e','f'}


#boolean系
s = {'apple','banana'}
t = {'apple','banana','lemon'}
u = {'cherry'}

print(s.issubset(t)) # True
print(t.issuperset(s)) # True
print(s.isdisjoin(t)) # False
print(s.isdisjoin(u)) # True
```

### if 

#### all,any
* all(タプルまたはリスト)、any(タプルまたはリスト)
* allを使用すると条件をANDでつなげなくてよくなるから可読性が良くなる。
* anyを使用すると、条件をOrでつなげなくてよくなる
```python 
if all((True,True,True)):
    print('全ての条件がTrueの場合')

if any((True,False,True))
    print('1つでもTrueの場合')
```
### for

* アンダースコアだけの変数は慣習的に使わない値を格納するのにつかわれる
* ループでよく使われるのはrange関数

```python
for i in range(10):
    print(i)
for i in range(2,20,3): #2から20まで3飛ばしで
    print(i)

for _ in range(100)
    print'100回ループする')

sample = ['A','B','C']
#enumerate[列挙する](valueと同時に要素番号も取得)
for index,value in enumerate(sample):
    print(index) #123
    print(value) #ABC

#zip(2つのリストの中身を同時に取得)
for a,b in zip(list1,list2):
    print(a,b)

#while
count=0
while count < 10:
    print(count)
    count += 1


#elseを使うと処理終了時に処理を実行できる
for i in range(10):
    print(i)
else:
    print("終了しました")

#ただ、breakで抜けた場合はelseは実行されない
for i in range(10):
    print(i)
    break
else:
    print("終了しました")
    
```
### セイウチ演算子

:= イコールの前にコロンをつけた演算子
* 変数の代入と変数の使用を同時に実行委できる

```python
# whileが一番使いやすそう
if (n := 10) > 5:
    print('5より大きい: {}'.format(n))

n = 0
while(n := n+1) < 10:
    print(n)

```

### メソッド一覧取得
```python
print(dir(list))
```

### 例外処理
```python
from traceback import print_exc
import traceback

try:
    b = [10, 20, 30]
    a = b[4]
    a = 10 / 0
except ZeroDivisionError as e:

    traceback.print_exc()  # 何行目でエラーになったか表示(詳細を表示)

    # eにはエラー内容が入っている(division by zero:<class 'ZeroDivisionError'>)
    print(f'{e}:{type(e)}')

    pass  # 何もしない行
except IndexError as e:
    traceback.print_exc()

except Exception as e: #全ての例外をキャッチ
    print(type(e))

else: 
    print('例外が発生しない場合に実行される') #elseで例外が発生した場合はキャッチされない
finally:
    print('例外が発生してもしなくても実行される')

```
#### raiseと自作例外
```python
class MyException(Exception):
    pass


def devide(a, b):
    if b == 0:
        # raise ZeroDivisionError('0では割り切れません')
        raise MyException('0では割り切れません')  # 自作例外
    else:
        return a / b

try:
    c = devide(10, 0)
except Exception as e:
    print(e, type(e))

```
### 関数
```python
def print_hello():
    print('hello world')


print_hello()

# コロンの後に型を指定することもできる、
# ただし厳密に指定できるわけじゃなくてstrとしていてもint渡せる（IDEのヒントにこの関数はこの引数だよ〜って出せる）


def num_max(a: int, b: str):
    print('a = {},b = {}'.format(a, b))
    if a > b:
        return a
    else:
        return b


print(num_max(10, 20))
print(num_max(b=100, a=20))  # 直接関数の変数を指定することもできる
```
#### デフォルト値、可変調引数、複数の返り値
```python
# デフォルト値
def sample(arg1, arg2=100):
    print(arg1, arg2)


sample(200, 300)
sample(200)  # 第二引数がなくてもデフォルト値がarg2には入る(200 100)

# 可変調引数
# 同じ可変調引数は複数は使えない
# ただ、タプル型と辞書型の可変調引数は混在OK
# 可変調引数は引数の一番最後に設定する


def spam(arg1, *arg2):  # 引数の前を*とすることで可変調のタプルとして複数の引数を受け取れるようになる
    # arg1 = 1,arg2 = (2, 3, 4, 5)
    print("arg1 = {},arg2 = {}".format(arg1, arg2))
    print(type(arg2))  # <class 'tuple'>


spam(1, 2, 3, 4, 5)


def spam2(arg1, **arg2):  # 引数の前を**とすることで可変調の辞書として複数の引数を受け取れるようになる
    # arg1 = 1,arg2 = {'name': 'taro', 'age': 20}
    print("arg1 = {},arg2 = {}".format(arg1, arg2))
    print(type(arg2))  # <class 'dict'>


spam2(1, name='taro', age=20)


def spam2(arg1, *arg2, **arg3):  # 可変調タプルと可変長辞書を宣言するパターン
    print("arg1 = {},arg2 = {},arg3 = {}".format(arg1, arg2, arg3))


# arg1 = 1,arg2 = (2, 3, 4, 5),arg3 = {'name': 'taro', 'age': 20}
spam2(1, 2, 3, 4, 5, name='taro', age=20)

# 複数の返り値


def sample_2():
    return 1, 2


a, b = sample_2()#カンマで区切って渡すと複数返せる。すごい

print(a,b)
```
### グローバル変数
```python
def printAnimal():
    global animal
    animal = 'cat'
    print('関数内animal = {}, id = {}'.format(animal, id(animal)))


animal = 'Dog'
printAnimal()

print('関数外animal = {}, id = {}'.format(animal, id(animal)))
```
### inner関数 ノンローカル変数
```python
# inner関数の用途
# 関数の中に関数の外からアクセスできないような関数を作成する
# 関数の中で同じ処理が何度も発生する場合などに使用する
# デコレータ関数を作成する

def outer():
    outer_value = '外側の変数'

    def inner():
        nonlocal outer_value  # ノンローカルで変数を宣言すると外側の値を参照するようになる,逆に宣言しないと新しい変数として扱われる
        outer_value = '内側の変数'
        # inner:outer_value = 内側の変数,id = 140404362253200
        print('inner:outer_value = {},id = {}'.format(
            outer_value, id(outer_value)))
    inner()
    # outer:outer_value = 内側の変数,id = 140404362253200
    print('outer:outer_value = {},id = {}'.format(outer_value, id(outer_value)))


# inner() 関数の外側から関数の中にある関数は呼べない
outer()

```
### ジェネレーター関数
ジェネレーターの一番の使い道はメモリ使用量の削減  
出番としてはDBから大量のデータを引っ張ってきて使用する場合  
配列にデータを入れていき、、みたいなことをすると大量のデータが必要になるが  
ジェネレーターを使うとメモリ消費量をほぼ0にすることができる  
```python

from typing import ValuesView


def generator(max):
    print('ジェネレーター作成')
    for n in range(max):
        yield n
        print('yield実行')


gen = generator(10)
# n = next(gen)  # yieldの値が返る
# print('n = {}'.format(n))  # n = 0
# n = next(gen)
# print('n = {}'.format(n))  # n = 1
# n = next(gen)
# print('n = {}'.format(n))  # n = 2

# ループでもかける,ループで書く場合はnextしなくても値が取れる
for x in gen:
    print('x = {}'.format(x))


# send,throw,close
def generator2(max):
    print('ジェネレーター作成')
    for n in range(max):
        x = yield n
        print('x = {}'.format(x))
        print('yield実行')


gen = generator2(10)

next(gen)  # yieldまで進む　（ジェネレーター作成）
gen.send(100)  # 値を送り込んで次のyieldまで進む(x = 100)

# throwを使用すると無理矢理例外処理を出力する(ValueError: Invalid Value)
# gen.throw(ValueError('Invalid Value'))

gen.close()  # ジェネレータをクローズさせる

next(gen)  # StopIteration
```
### サブジェネレータ
ジェネレータからジェネレータを呼び出すことができる
この時、呼び出し元がジェネレータ、呼び出し先がサブジェネレータとなる
yield from と記述しジェネレータからサブジェネレータを呼び出す
+ 呼び出し先のサブジェネレータからさらに別のジェネレータを呼び出すこともできる
+ サブジェネレータにreturnを追加すると呼び出し元に値を返せる
+ サブジェネレータでyieldを実行すると一番最初の呼び出し元に値を返す
```python

def sub_sub_generator():
    yield "３Sub Subのyield"
    return "Sub sub のreturn"

def sub_generator():
    yield "２Subのyield"
    res = yield from sub_sub_generator()
    print("４sub res = {}".format(res))

def generator():
    yield "１generatorのyield"
    res = yield from sub_generator()
    print('５gen res = {}'.format(res))
    return 'generatorのreturn'

gen = generator()

print(next(gen))
print(next(gen))
print(next(gen))
print(next(gen))
print(next(gen))
```

### 高階関数
関数を引数にしたり返り値にする関数を高階関数という

```python
def print_hello():
    print('hello')


def print_goodbye():
    print('goodbye')


var = ['AA', 'BB', print_hello, print_goodbye]

var[2]()  # hello
var[3]()  # goodbye


def print_world(msg):
    print('{} world'.format(msg))


def print_konnichiwa():
    print('こんにちは')


def print_hello(func):
    func('hello')
    return print_konnichiwa


var = print_hello(print_world)

# hello world
# こんにちは
var()

```
### ifを一行で書く方法
```python
y = 10
x = 0 if y > 0 else 1
print(x) #0

```

# lambda式
```python
lambda_a = lambda x: x * x #引数x 返り値x*y

print(lambda_a(10)) #100

lambda_b = lambda x,y,z=5: x * y * z #引数x 返り値x*y

print(lambda_b(10,5)) #250

# 条件式付きlambda
lambda_c = lambda x,y:y if x < y else x 
print(lambda_c(6,4)) #6
```
lambda式をvscodeで書くと保存の際にdef式に修正されてしまう  
なぜなのか調べたら現在lambda式を変数に代入するやり方は非推奨となっているからみたい　　
https://pep8-ja.readthedocs.io/ja/latest/#id41　　

以下、def式に修正されたlambda  
```python
def lambda_a(x): return x * x  # 引数x 返り値x*y

print(lambda_a(10))  # 100

def lambda_b(x, y, z=5): return x * y * z  # 引数x 返り値x*y
print(lambda_b(10, 5))  # 250

# 条件式付きlambda

def lambda_c(x, y): return y if x < y else x
print(lambda_c(6, 4))  # 6
```

### 再帰
```python
# 再帰は基本的に使わない
# 読みづらいのと無限ループしてしまう可能性があるため

def sample(a):
    if a < 0:
        return
    else:
        print(a)
        sample(a-1)


sample(10)
```
### リスト内包表記
```python
# リストをappendなどを使わず一行で作成できる
# 可読性が良くなる

list_a = (1, 2, 3, 'a', 4, 'b')

list_b = [x*2 for x in list_a]

print(list_b)  # [2, 4, 6, 'aa', 8, 'bb']

list_c = [x*2 for x in list_a if type(x) == int]  # 条件式で中身を評価することもできる

print(list_c)  # [2, 4, 6, 8]

list_d = [x for x in range(100) if x % 7 == 0]  # 7の倍数だけ取り出す
print(list_d)  # [0, 7, 14, 21, 28, 35, 42, 49, 56, 63, 70, 77, 84, 91, 98]

dict_a = {
    'a': 'Apple',
    'b': 'Banana'
}

list_e = [dict_a.get(x) for x in list_a if type(x) == str]

print(list_e)  # ['Apple', 'Banana']

```

### デコレータ関数
* デコレータは関数を引数にとって引数にとった関数を実行時に変更する
* デコレータは関数の間である処理を共通に利用したい場合に使われます
* 関数の前に@マークをつけてをデコレータ関数名を書くと使える
* wrapperの中のfuncが[func_a]だったり[func_b]になる
```python
def my_decorator(func):
    def wrapper(*args, **kwargs):
        print('*' * 100)
        func(*args, **kwargs)
        print('*' * 100)
    return wrapper


@my_decorator
def func_a(*args, **kwargs):
    print('func_aを実行')
    print(args)


@my_decorator
def func_b(*args, **kwargs):
    print('func_bを実行')
    print(args)


func_a(1, 2, 3)
func_b(1, 2, 3, 4)

```
