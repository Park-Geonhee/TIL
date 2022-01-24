# Pandas 

## 01.Pandas 사용하기
- Pandas : 2차원 정렬 데이터를 다루는 모듈입니다.
- 데이터 분석에서 `Pandas`의  `Series`, `DataFrame` 을 주로 다룹니다.
```python
import pandas as pd
from pandas import Series, DataFrame
```

### Series
- 1차원의 자료 구조이며, pandas의 기본 단위입니다.
- 하나의 데이터 타입을 허용합니다.

#### Series 기본 
- 기본 형식
```python
s = Series([1,2,3,4],index=['a','b','c','d'])
print(s)
```
```
a    1
b    2
c    3
d    4
dtype: int64
```

- 인덱스가 이미 존재할 경우
```python
Series(s, index = ['A','B','C','D'])
```
```
A   NaN
B   NaN
C   NaN
D   NaN
dtype: float64
```

---
### DataFrame
- 2차원의 자료 구조입니다.

#### DataFrame 기본

---
02
---
03
---
04
---
05
---
06
---
## 07. Merge & Concat
- 행이 서로 분리되어 있는 하나의 데이터프레임으로 합치기
- 컬럼이 서로 분리되어 있는 하나의 데이터프레임으로 합치기
- 참조 조건 사용, 연관된 두 데이터를 병합(join)
- SQL query 문과 유사

### concat
- `pandas.concat?` 명령어로 정의를 알 수 있습니다.
- 행의 결합이 주요 기능입니다.

- 실습을 위해 DataFrame을 저장합니다.
```python
df1 = DataFrame(np.arange(1,7).reshape(2,3), columns = ['A','B','C'])

```
```
   A  B  C     
0  1  2  3  
1  4  5  6  
```
```python
df2 = DataFrame(np.arange(10,61,10).reshape(2,3), columns = ['A','B','C'])
```
```
    A   B   C
0  10  20  30
1  40  50  60
```
- 이 두 DataFrame을 concat 함수를 이용하여 합칩니다.
```python
pd.concat([df1, df2])
# 행의 결합 
# 기본(default; axis = 0)은 세로방향으로 합쳐짐
```
```
    A   B   C
0   1   2   3
1   4   5   6
0  10  20  30
1  40  50  60
```
```python
pd.concat([df1, df2], axis = 1)
# 가로방향으로 합쳐짐 (열의 결합)
```
```
   A  B  C   A   B   C
0  1  2  3  10  20  30
1  4  5  6  40  50  60
```

```python
pd.concat([df1,df2],ignore_index=True)
# 기존의 index를 무시하고 결합 > 순차적인 인덱스 번호 부여됨
```
```
    A   B   C
0   1   2   3
1   4   5   6
2  10  20  30
3  40  50  60
```

### merge
- `pandas.merge?` 명령어로 정의를 알 수 있습니다.
```python
pd.merge(left,          # 첫 번째 데이터프레임
         right,         # 두 번째 데이터프레임
         how='inner',   # 조인 방법(default = 'inner')
         on=,           # 조인하는 컬럼(컬럼명이 서로 같을 떄)
         left_on=,      # 첫 번째 데이터프레임 조인(컬럼명이 서로 다를 때)
         right_on=)     # 두 번째 데이터프레임 조인(컬럼명이 서로 다를 때)
```
- merge는 실습을 통하여 알아보며, 실습에서는 로컬 csv 파일을 이용합니다.

- 첫 번째 DataFrame
```python

emp = pd.read_csv('./Desktop/BigData_code/data_bigdata_cert/emp.csv')
```
```
   empno  ename  deptno   sal
0      1  smith      10  4000
1      2  allen      10  4500
2      3   ford      20  4300
3      4  grace      10  4200
4      5  scott      30  4100
5      6   king      20  4000
```

- 두 번째 DataFrame
```python
df_dept = DataFrame({'deptno':[10,20,30],'dname':['인사부','총무부','IT분석팀']})
```
```
   deptno  dname
0      10    인사부
1      20    총무부
2      30  IT분석팀
```
```python
pd.merge(emp, df_dept, on='deptno') # how = "inner"
```
```
   empno  ename  deptno   sal  dname
0      1  smith      10  4000    인사부
1      2  allen      10  4500    인사부
2      4  grace      10  4200    인사부
3      3   ford      20  4300    총무부
4      6   king      20  4000    총무부
5      5  scott      30  4100  IT분석팀
```
- 만약 두 DataFrame 이 서로 매칭이 안된다면, 가령 `df_dept` 의 성분이 다음과 같다면, `inner join` 과 `outer join`이 크게 달라집니다.

- 다음은 `default = inner join` 일 경우입니다.
```python
df_dept_new = DataFrame({'deptno':[10,20],'dname':['인사총무부','IT분석팀']})

pd.merge(emp, df_dept_new, on = 'deptno') # 30번 부서원 생략
```
```
   empno  ename  deptno   sal  dname
0      1  smith      10  4000  인사총무부
1      2  allen      10  4500  인사총무부
2      4  grace      10  4200  인사총무부
3      3   ford      20  4300  IT분석팀
4      6   king      20  4000  IT분석팀
```
- `outer join`일 경우입니다.
```python
pd.merge(emp, df_dept_new, on = 'deptno', how = 'outer')
```
   empno  ename  deptno   sal  dname
0      1  smith      10  4000  인사총무부
1      2  allen      10  4500  인사총무부
2      4  grace      10  4200  인사총무부
3      3   ford      20  4300  IT분석팀
4      6   king      20  4000  IT분석팀
5      5  scott      30  4100    NaN
```
