 import random
import datetime
import time

# 참가자 명단
participants = ['승훈', '태은', '영훈', '준우']

# 청소 역할 리스트
roles = ['쓸체폰', '걸레', '싱크대']

# 오늘 날짜 기반 시드 생성
today = datetime.date.today().isoformat()  # 'YYYY-MM-DD' 형식
random.seed(today)  # 고유 시드 설정 (날짜 기준)

# 청소 담당자와 역할 분배 (날짜 고정)
cleaners = random.sample(participants, len(roles))  # 역할 수만큼 담당자 선택
assigned_roles = dict(zip(cleaners, roles))  # 담당자와 역할 매칭

# 사용자 입력
user_name = input("이름을 입력하세요: ").strip()

# 전체 결과 출력 (입력한 이름은 제외, 1초 간격)
print("\n전체 결과:")
for person in participants:
    if person == user_name:
        continue  # 입력한 이름은 건너뜀
    time.sleep(1)  # 1초 대기
    if person in assigned_roles:
        print(f"{person}: 청소 {assigned_roles[person]}")
    else:
        print(f"{person}: 통과")

# 입력한 이름의 결과 출력
time.sleep(1)  # 마지막 출력 전 추가 대기
print("\n당신의 결과:")
if user_name not in participants:
    print("명단에 없는 이름입니다. 다시 확인해주세요.")
else:
    if user_name in assigned_roles:
        print(f"{user_name}: 청소 담당 ({assigned_roles[user_name]})")
    else:
        print(f"{user_name}: 통과")
