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
