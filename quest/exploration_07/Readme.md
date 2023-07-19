# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 황규빈
- 리뷰어 : [이태훈](https://github.com/git-ThLee)


# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 네! 에폭을 늘리면 성능이 향상할 것 같습니다!
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 네! 주석이 좀 더 많으면 좋겠습니다. 이왕이면 한글로...ㅎ
  ```python
  out = image.random_flip_left_right(out)        # flip left & right
    out = image.random_flip_up_down(out)           # flip up & down
  ```
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 네! 정상적으로 작동합니다!
  ```python
  EPOCHS = 20

  generator = UNetGenerator()
  discriminator = Discriminator()
  history = {'gen_loss':[], 'l1_loss':[], 'disc_loss':[]}

  for epoch in range(1, EPOCHS+1):
      for i, (seg, orig) in enumerate(train_images):
          g_loss, l1_loss, d_loss = train_step(seg, orig)
          history['gen_loss'].append(g_loss)
          history['l1_loss'].append(l1_loss)
          history['disc_loss'].append(d_loss)
                  
          # 1 epoch마다 손실을 출력합니다.
          if (i+1) % 250 == 0:
              print(f"EPOCH[{epoch}] - STEP[{i+1}] \
                      \nGenerator_loss:{g_loss.numpy():.4f} \
                      \nL1_loss:{l1_loss.numpy():.4f} \
                      \nDiscriminator_loss:{d_loss.numpy():.4f}", end="\n\n")
  ```
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 네! Loss 로그가 자주 발생해서, 코드를 수정햇습니다.
  ```python
  if (i+1) % 250 == 0:
            print(f"EPOCH[{epoch}] - STEP[{i+1}] \
                    \nGenerator_loss:{g_loss.numpy():.4f} \
                    \nL1_loss:{l1_loss.numpy():.4f} \
                    \nDiscriminator_loss:{d_loss.numpy():.4f}", end="\n\n")
  ```
- [X] 코드가 간결한가요?
  > 네! 이미지를 출력할 때, 코드가 복잡하지 않습니다!
  ```python
  plt.figure(figsize=(15,13))
  img_n = 1
  for i in range(1, 13, 2):
      augmented_seg, augmented_orig = apply_augmentation(seg, orig)
      
      plt.subplot(3,4,i)
      plt.imshow(denormalize(augmented_seg)); plt.title(f"Image {img_n}")
      plt.subplot(3,4,i+1); 
      plt.imshow(denormalize(augmented_orig)); plt.title(f"Image {img_n}")
      img_n += 1
  ```

# 예시