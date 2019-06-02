# 부산의 와이파이 현황

정보컴퓨터공학과 | 201624532 | 윤영채
---- | ---- | ---- 

정보컴퓨터공학과 | 201624532 | 윤영채


## 프로젝트 개요
현재 위치한 장소를 입력시 근처에 있는 와이파이의 설치 위치를 알려줍니다.

## 사용한 공공데이터 
[데이터보기](https://github.com/cybermin/python2019/blob/master/%EB%B6%80%EC%82%B0%EA%B5%90%ED%86%B5%EA%B3%B5%EC%82%AC_%EB%8F%84%EC%8B%9C%EC%B2%A0%EB%8F%84%EC%97%AD%EC%82%AC%EC%A0%95%EB%B3%B4_20190520.csv)

## 소스
* [링크로 소스 내용 보기](https://github.com/cybermin/python2019/blob/master/tes.py) 

* 코드 삽입
import pandas as pd
import matplotlib.pyplot as plt
import operator
#한글 폰트 사용
from matplotlib import font_manager, rc
font_name = font_manager.FontProperties(fname="c:/Windows/Fonts/malgun.ttf").get_name()
rc('font', family=font_name)

df = pd.read_csv('d.csv')
df1 = df['설치장소명']
df2 = df['위도']
df3 = df['경도']



dfn = []
dfw = []
dfk = []
for i in range(1909):
    dfn.append(df1[i])
for i in range(1909):
    dfw.append(df2[i])
for i in range(1909):
    dfk.append(df3[i])
dictw = dict(zip(dfn,dfw))
dictk = dict(zip(dfn,dfk))
sdictw = sorted(dictw.items(), key=operator.itemgetter(1))
sdictk = sorted(dictk.items(), key=operator.itemgetter(1))

you = input()
x = dictw[you]
y = dictk[you]

list1 = sorted(dfw)
list2 = sorted(dfk)


slistx = []
slisty = []

for i in range(0,1909):
    if list1[i] == x :
        for j in range(0,10):
            slistx.append(list1[i+j])
            slistx.append(list1[i-j])
        break

    else : continue


for i in range(0,1909):
    if list2[i] == y :
        for j in range(0,10):
            slisty.append(list2[i+j])
            slisty.append(list2[i-j])
        break
    else : continue

slistx = sorted(slistx)
slisty = sorted(slisty)


plt.title('부산 wifi')
plt.xlabel('위도')
plt.ylabel('경도')
plt.plot(slistx,slisty)
plt.show()








