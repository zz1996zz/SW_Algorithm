# Programmers의 예제문제들은 PYTHON으로 코드를 작성하였습니다.
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
