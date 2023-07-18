# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 황규빈
- 리뷰어 : 초ㅣ한준


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 네
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 네
    ```python
    def print_word_frequency(input_train, threshold_value=0):

    tokenizer = Tokenizer() # 토크나이저 정의
    tokenizer.fit_on_texts(input_train) # 입력된 데이터로부터 단어 집합 생성

    threshold = threshold_value
    total_cnt = len(tokenizer.word_index) # 단어의 수
    rare_cnt = 0 # 등장 빈도수가 threshold보다 작은 단어의 개수를 카운트
    total_freq = 0 # 훈련 데이터의 전체 단어 빈도수 총 합
    rare_freq = 0 # 등장 빈도수가 threshold보다 작은 단어의 등장 빈도수의 총 합

    # 단어와 빈도수의 쌍(pair)을 key와 value로 받는다.
    for key, value in tokenizer.word_counts.items():
        total_freq = total_freq + value

        # 단어의 등장 빈도수가 threshold보다 작으면
        if(value < threshold):
            rare_cnt = rare_cnt + 1
            rare_freq = rare_freq + value

    print('단어 집합(vocabulary)의 크기 :', total_cnt)
    print('등장 빈도가 %s번 이하인 희귀 단어의 수: %s'%(threshold - 1, rare_cnt))
    print('단어 집합에서 희귀 단어를 제외시킬 경우의 단어 집합의 크기 %s'%(total_cnt - rare_cnt))
    print("단어 집합에서 희귀 단어의 비율:", (rare_cnt / total_cnt)*100)
    print("전체 등장 빈도에서 희귀 단어 등장 빈도 비율:", (rare_freq / total_freq)*100)

    ```
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 네
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 네
- [X] 코드가 간결한가요?
  > 네

# 예시