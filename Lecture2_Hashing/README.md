# Hashing

## Problem description link
  - https://school.programmers.co.kr/learn/courses/30/lessons/92334

## Using library
  - Collections [https://docs.python.org/ko/3/library/collections.html#collections.defaultdict]

## Code
```python
#collections 임포트
import collections
def solution(id_list, report, k):
    answer = []
    report = list(set(report)) 
    # 중복 제거를 위해 set 형태의 list로 형변환, 아래 문제 해결
    # --> 한 유저를 여러 번 신고할 수도 있지만, 동일한 유저에 대한 신고 횟수는 1회로 처리됩니다.
    print(report)
    
    reportHash = collections.defaultdict(set) 
    #key가 set 형태인 dict #해쉬# 를 생성 .defaultdict는 초기화를 있으면 그것, 없으면 none으로 해줌. dict[k].add() 값 추가
    stoped = collections.defaultdict(int) 
    #key가 int로 설정하면 dict[k]+=1 과 같이 간단히 카운팅 가능
    
    for x in report:
        #split(기준값) 분리
        a, b = x.split(' ')
        reportHash[a].add(b)
        stoped[b]+=1
        #print(stoped[b])
    for name in id_list:
        mail = 0
        for user in reportHash[name]:
            if stoped[user]>=k:
                mail+=1
        answer.append(mail)
    
    return answer
```
