# 네이버 블로그 크롤러 (naver-blog-crawler)

네이버 블로그 크롤러입니다. 공부 목적으로만 활용하시기 바랍니다.

* Python(>=3.6.1)
* 코딩 스타일 가이드는 PEP 8을 따르고 있습니다.
* beautifulsoup4, requests, lxml 라이브러리가 필요합니다.

```sh
$ pip install beautifulsoup4
$ pip install requests
$ pip install lxml

```

#### 1. 기존의 네이버 블로그 검색 API를 활용한 크롤러입니다. 동작하기 위해서는 다음과 같은 선행 작업이 필요합니다.

 * [네이버 개발자 웹 페이지](https://developers.naver.com/main/)에서 애플리케이션 등록을 해야 합니다.

 * 클라이언트 ID와 SECRET을 확인해야 합니다. 애플리케이션을 등록하면 '내 애플리케이션'에서 확인할 수 있습니다.

 * API 권한 설정을 해야 합니다. '내 애플리케이션'의 'API 권한관리' 탭에서 사용하려는 API가 체크되어 있는지 확인합니다. 체크되어 있지 않을 경우 403 에러(API 권한 없음)가 발생합니다.

#### 2. 위의 선행 작업을 마쳤으면 코드 상단의 클라이언트 ID, SECRET에 자신이 발급받은 값을 넣습니다.

```
naver_client_id = "INPUT YOUR CLIENT ID"
naver_client_secret = "INPUT YOUR CLIENT SECRET"
```

#### 3. 메인에서 호출하는 함수의 파라미터 값은 다음과 같습니다.

```
if __name__ == '__main__':
    naver_blog_crawling("파이썬 컨벤션", 100, "sim")
```

* first parameter : 검색하고 싶은 키워드
* second parameter : 한 페이지당 표출할 개수
* third parameter : 포스팅 정렬 순서(sim (유사도순) / date (날짜순))

자신의 상황에 맞게 변경해서 사용하면 됩니다.

-----------------------------------------------

공부 목적으로 만들고 있기 때문에 잦은 버그 픽스나 기능 추가가 있을 수도 있습니다.<br>
버그나 문의 사항은 이슈에 남겨주시면 감사하겠습니다. :)

by 체리픽<br>
https://cherrypick.co.kr
