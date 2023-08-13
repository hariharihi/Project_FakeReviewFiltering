# 1. Data Exceeded 이슈
> IOPub data rate exceeded.
> The notebook server will temporarily stop sending output to the client in order to avoid crashing it.
> To change this limit, set the config variable `--NotebookApp.iopub_data_rate_limit`.

- 해결: https://dev-cini.tistory.com/38

# 2. 리뷰 총 개수랑 list length랑 일치하지 않는 이슈
- 트러블슈팅: 긁기 전에 제대로 된 데이터를 탐색 및 선택(css select)할 시간이 부족 >> 중복되어 긁힘
- 해결: driver.find_elements로 클릭하기 전에 time.sleep() 꼭 해줘야 함

# 3. 리뷰 링크 안에서, review_num까지는 잘 찍히는데, list 데이터 3까지만 찍히는 이슈
### 트러블슈팅1: (X) 클릭이 안 되었거나
- (확인) 클릭 수 찍어보기 by 함수 3 no.38(print('click!') >> 추가
- 함수 3 no.23(webdriverwait(3,code))의 시간을 더 늘리기???
### 트러블슈팅2: (X) css select가 제대로 안 되었거나
- (확인) css selector 값 찍어보기 by 함수 3 no.36(print(f'버튼명: {element.text}') >> 추가
- 함수 3 no.78(time.sleep(n)) 추가하기???
### 트러블슈팅3: 다른 css selector를 선택
- '메뉴 더보기'가 있는 경우, 이 css selector를 먼저 선택하게 됨
- 해결: 코드 추가 (if문 - '후기 더보기'일 경우 작동)

# 4. 크롤링 하다가 disconnnected 되는 이슈
> Message: stale element reference: stale element not found
> 그 이후에 맛집 정보랑 리뷰 정보 불일치함 (전자가 잘못 들어감)
- 긁기 전에 제대로 된 데이터를 탐색 및 선택(css select)할 시간이 부족 >> 정보 불일치
- 해결: 함수 3 no.23(webdriverwait(3,code)) 더 주기
