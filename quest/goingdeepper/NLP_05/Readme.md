# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 황규빈
- 리뷰어 : 황인준
  


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 아직은 프로그램 실행중이어서 문제 해결능력을 확인 못 했지만 전반적으로 동작을 제대로 할 것으로 생각됩니다

- [O] 주석을 보고 작성자의 코드가 이해되었나요?
  > 주석 및 이미지가 꼼꼼하게 삽입되어 있어서 이해하기 쉽도록 구성되어있습니다
  
- [O] 코드가 에러를 유발할 가능성이 없나요?
  > 발견된 에러 메세지는 없었습니다. 

- [O] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > transformer의 구조를 이해하고 그를 구현하기 위해 노력한 것이 보입니다.

- [O] 코드가 간결한가요?
  > 코드를 간결하게 작성하여 가독성을 높였습니다.
  
# 참고 링크 및 코드 개선
```python
# 모델 초기화
# 하이퍼파라미터
NUM_LAYERS = 2 # 인코더와 디코더의 층의 개수
D_MODEL = 512 # 인코더와 디코더 내부의 입, 출력의 고정 차원
NUM_HEADS = 8 # 멀티 헤드 어텐션에서의 헤드 수 
UNITS = 2048 # 피드 포워드 신경망의 은닉층의 크기
DROPOUT = 0.2 # 드롭아웃의 비율
POS_LEN=200
```

- NUM_LAYERS = 2 인경우, 제 경우에는 생각보다 번역 능력이 떨어졌던것을 확인했었습니다. 이번 learning이 끝나고 나서 적절한 번역 능력이 확인되지 않는다면, 층을 늘려보는것을 추천 드립니다.
