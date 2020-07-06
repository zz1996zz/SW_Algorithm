## 코딩하면서 배운 내용들
## 1. hash()
hash() 내장함수는 객체의 해시값(정수)을 반환한다. 해시란 어떠한 값을 식별할 수 있는 정해진 길이의 정수이다.  
모든 값은 고유의 해시를 가지고 있으므로, 다른 변수에 담겨있어도 값이 같으면 해시도 같다.

```python
>>>hash('jeongsu')  
-427518073
```
```python
>>>a='jeongsu'  
>>>hash(a)  
-427518073
```
위의 예시와 같이 값은 고유의 해시를 가지고 있어서 다른 변수에 담겨있어도 해시값이 같다.

## 2. collections.Counter()
collections.Counter()은 컨테이너에 동일한 값의 자료가 몇 개인지를 파악하는데 사용한다.  
결과값은 dictionary 형태로 출력된다.  
__주의할 점은 collections.Counter()은 내장함수가 아니므로 import collections를 선언해주어야 한다.__
```python
import collections  

list = ['a','a','b','b','c']  
print(collections.Counter(list))  

결과값
Counter({'a': 2, 'b': 2, 'c': 1})
```
collections.Counter()는 산술/집합 연산이 가능하다.  
```python
import collections

a=collections.Counter(['a','a','b','b','c'])
b=collections.Counter('banana')

print(a)
print(b)
print(a+b)

결과값
Counter({'a': 2, 'b': 2, 'c': 1})
Counter({'a': 3, 'n': 2, 'b': 1})
Counter({'a': 5, 'b': 3, 'n': 2, 'c': 1})
```
자세한 내용은 [바로가기](https://excelsior-cjh.tistory.com/94?category=966334) 

## 3. zip()
zip() 함수는 동일한 개수로 이루어진 자료형을 묶어주는 역할을 하는 함수이다.
```python
x=[1, 2, 3]
y=[4, 5, 6]

z=zip(x,y)
print(list(z))

결과값
[(1, 4), (2, 5), (3, 6)]
```
```python
a = 'abc'
b = 'def'
 
zipped3 = zip(a, b)
print(list(zipped3))

결과값
[('a', 'd'), ('b', 'e'), ('c', 'f')]
```
zip()을 활용하여 Dictionary의 {key : value} 중 value 값으로 최댓값과 최솟값 그리고 정렬을 할 수 있다.
```python
d = {'banana': 3, 'apple': 4, 'pear': 1, 'orange':2}
 
min_item = min(zip(d.values(), d.keys()))
max_item = max(zip(d.values(), d.keys()))
print(min_item)
print(max_item)

결과값
(1, 'pear')
(4, 'apple')
```
```python
d_sorted1 = sorted(zip(d.values(), d.keys()))
print(d_sorted1)

결과값
[(1, 'pear'), (2, 'orange'), (3, 'banana'), (4, 'apple')]
```
```python
d_sorted2 = sorted(d.items(), key= lambda t:t[1])
print(d_sorted2)

결과값
[('pear', 1), ('orange', 2), ('banana', 3), ('apple', 4)]
```

자세한 내용은 [바로가기](https://excelsior-cjh.tistory.com/100) 

## 4. reduce()
reduce()는 아래와 같은 매개변수를 갖는다.
```python
reduce(function, iterable, initializer=None)
```
function에는 람다식 함수나 정해준 함수가 들어가고, iterable에는 계산할 리스트가 입력됩니다.  
예를 들면
```python
from functools import reduce

result = reduce(lambda x,y : x+y, [1, 2, 3, 4, 5]) # ((((1+2)+3)+4)+5)
print(result)

결과값
15
```
initializer에 값을 넣어주게 되면 아래와 같이 계산된다.
```python
from functools import reduce

result = reduce(lambda x,y : x+y, [1, 2, 3, 4, 5], 100) #  ((((100+1)+2)+3)+4)+5)
print(result)

결과값
115
```

## 5. 문자열 공백 제거
문자열 속에 있는 공백을 제거하기 위해서는 strip(), replace(), join().split()이 있다.  
1) strip()함수는 문자열의 양쪽 공백을 모두 제거해주는 함수이다.  
문자열의 왼쪽 공백만 제거하려면 lstrip(), 오른쪽 공백만 제거하려면 rstrip()을 사용하면 된다.
```python
word='   apple'
word.lstrip()
>>>'apple'

word='grape   '
word.rstrip()
>>>'grape'

word='   orange   '
word.strip()
>>>'orange'
```
2) replace()함수는 어떤 문자를 다른 문자로 교체해주는 함수이다.
```python
word='   apple   '
word.replace(' ', '')
>>>'apple'
```
3) join()함수와 split()함수는 아래와 같이 사용하면 중복된 공백이 제거된다.
```python
word='apple  grape  orange'
' '.join(word.split())
>>>'apple grape orange'
```
결과값과 같이 2개의 공백이 1개로 줄어들었다.

## 6. enumerate
enumerate함수는 내장함수로 iterater객체(list, set, dictionary등)을 입력으로 받아 인덱스 값을 포함하는 enumerate 객체를 리턴한다.  
enumerate함수를 사용하여 출력하면, 인덱스와 값이 튜플 타입으로 출력된다.
```python
a=['a','b','c','d']
for i in enumerate(a):
    print(i, type(i))

결과값
(0, 'a') <class 'tuple'>
(1, 'b') <class 'tuple'>
(2, 'c') <class 'tuple'>
(3, 'd') <class 'tuple'>
```
인덱스와 값을 따로 받을 수 있다.
```python
a=['a','b','c','d']
for index, value in enumerate(a):
    print(index, ":", value)

결과값
0 : a
1 : b
2 : c
3 : d
```
딕셔너리를 enumerate함수를 사용해서 출력하면 아래와 같이 출력된다.
```python
b={'이름':'이정수','나이':'25','성별':'남자'}
for i,key in enumerate(b):
  	print(i,':',key,b[key])

결과값
0 : 이름 이정수
1 : 나이 25
2 : 성별 남자
```
## 7. operator.itemgetter()
딕셔너리에 입력된 key, value를 정렬할 때는 sorted()함수를 사용한다. 하지만 딕셔너리를 정렬할 수는 없기 때문에  
items()를 사용하여 key와 value를 튜플로 구성한 리스트를 정렬한다. 정렬을 해보면 아래와 같다.
```python
dic={'a':3,'b':5,'c':7,'db':2,'da':2}
sortedDic=sorted(dic.items())
print(sortedDic)

결과값
[('a', 5), ('b', 3), ('c', 7), ('da', 2), ('db', 2)]
```
위의 결과값은 key에 의해 정렬이 된 상태이다. 하지만 value에 의해 정렬을 원할 때가 있을 것이다.  
그때는 operator모듈의 itemgetter()함수를 사용하면 value로 정렬을 할 수 있다.
```python
from operator import itemgetter

dic={'a':3,'b':5,'c':7,'db':2,'da':2}
sortedDic=sorted(dic.items(), key=itemgetter(1))
print(sortedDic)

결과값
[('db', 2), ('da', 2), ('a', 3), ('b', 5), ('c', 7)]
```
key=itemgetter(1)을 사용하여 value에 의한 정렬을 하였다.  
itemgetter(1)은 dic.items()의 튜플의 0번째가 아닌 1번째를 key로 잡고 정렬을 하겠다는 것이다.  
그래서 위와같은 결과가 나오게 된것이다.  
결과값을 보면 'db'와 'da'는 같은 value를 갖는다. 하지만 'da'가 'db'보다는 사전적으로는 앞에 있어야한다.  
이 문제를 해결하기 위해서는 itemgetter(1, 0)로 변경하여 입력해주면 해결된다.  

itemgetter(1,0)은 일단 튜플의 1번째를 기준으로 정렬을 하고, 같은 값이 나오게 되면, 0번째를 기준으로 정렬을 한다는 것이다.
지금까지 정렬은 오름차순으로 정렬을 했다. 내림차순으로 정렬을 하려면 reverse=True를 넣어주면 된다.
```python
from operator import itemgetter

dic={'a':3,'b':5,'c':7,'db':2,'da':2}
sortedDic=sorted(dic.items(), key=itemgetter(1,0), reverse=True)
print(sortedDic)

결과값
[('c', 7), ('b', 5), ('a', 3), ('db', 2), ('da', 2)]
```
## 8. collections.defaultdict()
defaultdict()함수의 설명은 아래 링크에 자세하게 나와있으니 저기서 보고 깨우칠 것  
[바로가기](https://excelsior-cjh.tistory.com/95)  

## 9. collections.deque()
deque()함수의 설명은 아래 링크에 여러 기능이 자세히 나와있으니 링크를 통해 공부할 것.
[바로가기](https://excelsior-cjh.tistory.com/96)  
