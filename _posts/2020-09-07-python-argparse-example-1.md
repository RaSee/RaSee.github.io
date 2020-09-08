---
title: Python argparse 예제 1
author: 전규범
date: 2020-09-09 01:11:00 +0800
categories: [python, argparse]
tags: [python, argparse, argument, example]
toc: false
last_modified_at : 2020-09-14T00:08+09:00
---

python argparse

python에는 프로그램 구동 시 받는 인자를 편리하게 해주는 argparse 모듈이 있다.

다음과 같이 사용할 수 있다.

argparse_example1.py

```python

import argparse

if __name__ == '__main__':
    
    parser = argparse.ArgumentParser()
    #위치 인자 받기
    parser.add_argument("a")
    parser.add_argument("b")

    args = parser.parse_args()

    print("a : ", args.a)
    print("b : ", args.b)
```

위의 코드를 실행하면 다음과 같은 결과를 얻을 수 있다.

```terminal
$ python3 argparse_example1.py 2 5
a :  2
b :  5
```


비교를 위해 인자를 받아올 수 있는 sys모듈을 사용해보았다.


```python

import sys

if __name__ == '__main__':
    
    print("a : ", sys.argv[1])
    print("b : ", sys.argv[2])
```

```terminal
$ python3 sys_args_example.py 2 5
a :  2
b :  5
```
argparse는 인자 인자 이름을 통해 변수의 역할을 짐작할 수 있다는 장점이 있지만
단순히 순서대로 인자를 받는거라면 sys module이 더 간편해보인다.

하지만 argparse에는 옵션인자를 사용하여 순서에 구애받지 않고 인자를 받아올 수 있다.

```python

import argparse

if __name__ == '__main__':
    
    #
    parser = argparse.ArgumentParser()
    parser.add_argument("--apple")
    parser.add_argument("--banana")

    args = parser.parse_args()

    print("apple  : ", args.apple)
    print("banana : ", args.banana)

```
```terminal
$ python3 argparse_example2.py --apple 2 --banana 5
apple  :  2
banana :  5
$ python3 argparse_example2.py --banana 5 --apple 2
apple  :  2
banana :  5
```

옵션 인자가 길다면 짧은 옵션을 사용하여 인자 이름을 줄일 수 있다.


```python
import argparse

if __name__ == '__main__':
    
    #
    parser = argparse.ArgumentParser()
    parser.add_argument("--apple", "-a")
    parser.add_argument("--banana", "-b")

    args = parser.parse_args()

    print("apple  : ", args.apple)
    print("banana : ", args.banana)
```
```terminal
$ python3 argparse_example2.py -a 2 -b 5
apple  :  2
banana :  5
```

sys 는 모든 인자를 str로 받아오지만
argparse는 각 인자의 type를 지정할 수 있다.


```python
import argparse

if __name__ == '__main__':
    
    #
    parser = argparse.ArgumentParser()
    parser.add_argument("--apple", "-a", type=int)
    parser.add_argument("--banana", "-b", type=str)

    args = parser.parse_args()

    print("apple  : ", args.apple, type(args.apple))
    print("banana : ", args.banana, type(args.banana))
```
```terminal
$ python3 argparse_example4.py  -a 2 -b 3
apple  :  2 <class 'int'>
banana :  3 <class 'str'>
```

이를 참고하여 인자를 쉽게 받아보자.



참고
1. https://docs.python.org/ko/3/howto/argparse.html