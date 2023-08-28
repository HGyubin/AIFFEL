
# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 황규빈
- 리뷰어 : 김성진


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 네, 전처리, 토큰화, 모델 설계, 평가까지 작업 프로세스가 잘 이루어져 있습니다.  
  > epoch 가 거듭될 때마다 Loss 가 줄어들어 학습이 되고 있습니다.  

- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 네, 작업이 섹션별로 나뉘어 있어 잘 이해됩니다.
  
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 네, 없습니다.

- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 네, 작업 프로세스로 볼 때 잘 이해하고 있다고 판단됩니다.

- [X] 코드가 간결한가요?
  > 네, 아주 간결합니다.
     

> 중복 데이터 제거 및 길이 제한

```python
#중복 데이터 제거
raw = zip(ko_raw, en_raw)
cleaned_corpus = set(raw)

# 필터링하여 청소된 코퍼스를 생성합니다.
max_token_length = 40
tokenizer = Mecab()
corpus = set()
for ko_sent, en_sent in cleaned_corpus:
    ko_tokens = tokenizer.morphs(ko_sent)  # 한국어 문장을 토큰으로 분할합니다.
    en_tokens = en_sent.split()  # 영어 문장을 토큰으로 분할합니다.
    
    # 한국어와 영어 문장 모두 토큰 길이가 max_token_length 이하인지 확인
    if (len(ko_tokens) <= max_token_length) and len(en_tokens) <= max_token_length:
        corpus.add((ko_sent, en_sent))

# token 길이가 40보다 긴 문장을 cleaned_corpus에서 제외합니다.
ko_corpus, en_corpus = zip(*corpus)
print(len(ko_corpus), len(en_corpus))
```

# 예시

> 섹션에 대한 작업 계획 명시

```markdown
### Step 3. 데이터 토큰화
- 토큰화하고 텐서로 변환
- 텐서를 80%의 훈련 데이터와 20%의 검증 데이터로 분리

### Step 4. 모델 설계
 - 각각 1개의 GRU을 갖는 Encoder-Decoder 구조
 - BahdanauAttention
```

> 에포크에 따라 학습되는 과정

```markdown
Epoch  1: 100%|██████████| 775/775 [03:16<00:00,  3.95it/s, Loss 2.7453]  
Epoch  2: 100%|██████████| 775/775 [01:44<00:00,  7.44it/s, Loss 2.6959]
Epoch  3: 100%|██████████| 775/775 [01:44<00:00,  7.43it/s, Loss 2.6959]
Epoch  4: 100%|██████████| 775/775 [01:44<00:00,  7.43it/s, Loss 2.6951]
Epoch  5: 100%|██████████| 775/775 [01:44<00:00,  7.41it/s, Loss 2.4812]
Epoch  6: 100%|██████████| 775/775 [01:44<00:00,  7.42it/s, Loss 2.2912]
Epoch  7: 100%|██████████| 775/775 [01:44<00:00,  7.41it/s, Loss 2.1790]
Epoch  8: 100%|██████████| 775/775 [01:44<00:00,  7.43it/s, Loss 2.0874]
Epoch  9: 100%|██████████| 775/775 [01:44<00:00,  7.42it/s, Loss 2.0103]
Epoch 10: 100%|██████████| 775/775 [01:44<00:00,  7.43it/s, Loss 1.9470]
```

> 번역 결과

```markdown
Input: 커피는 필요 없다 .
Predicted translation: we re going to the <unk> . <end> 
```
