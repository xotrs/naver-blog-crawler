# 네이버 블로그 크롤러 (naver-blog-crawler)

검색 API를 활용한 네이버 블로그 크롤러입니다. 네이버 블로그 크롤러는 포스팅 URL, 포스팅 제목, 포스팅 설명, 포스팅 날짜, 블로거 이름, 포스팅 내용(Full Text)을 크롤링하고 있습니다. 공부 목적으로 활용 부탁드립니다. 크롤링 데이터의 저작권은 [네이버](https://www.naver.com/)에 있습니다.

* Python(>=3.6.1)
* 코딩 스타일 가이드는 PEP 8을 따르고 있습니다.
* beautifulsoup4, requests, lxml 라이브러리가 필요합니다.

```sh
$ pip install beautifulsoup4
$ pip install requests
$ pip install lxml
```

## 기본 설정


#### 1. 기존의 네이버 블로그 검색 API를 활용한 크롤러입니다. 동작하기 위해서는 다음과 같은 선행 작업이 필요합니다.

 * [네이버 개발자 웹 페이지](https://developers.naver.com/main/)에서 애플리케이션 등록을 해야 합니다.

 * 클라이언트 ID와 SECRET을 확인해야 합니다. 애플리케이션을 등록하면 '내 애플리케이션'에서 확인할 수 있습니다.

 * API 권한 설정을 해야 합니다. '내 애플리케이션'의 'API 권한관리' 탭에서 사용하려는 API가 체크되어 있는지 확인합니다. 체크되어 있지 않을 경우 403 에러(API 권한 없음)가 발생합니다.

#### 2. 위의 선행 작업을 마쳤으면 코드 상단의 클라이언트 ID, SECRET에 자신이 발급받은 값을 넣습니다.

```
naver_client_id = "INPUT YOUR CLIENT ID"
naver_client_secret = "INPUT YOUR CLIENT SECRET"
```

## 사용 방법

#### 1. 메인에서 호출하는 함수의 파라미터 값은 다음과 같습니다.

```
if __name__ == '__main__':
    naver_blog_crawling("파이썬 컨벤션", 100, "sim")
```

* first parameter : 검색하고 싶은 키워드
* second parameter : 한 페이지당 표출할 개수
* third parameter : 포스팅 정렬 순서(sim (유사도순) / date (날짜순))

자신의 상황에 맞게 변경해서 사용하면 됩니다.


## 출력 결과

```
/usr/local/Cellar/python3/3.6.1/Frameworks/Python.framework/Versions/3.6/bin/python3.6 /Users/rok/naver-blog-crawler/NaverBlogCrawler.py

키워드 파이썬 컨벤션에 해당하는 포스팅 수 : 110
키워드 파이썬 컨벤션에 해당하는 블로그 실제 페이징 수 : 2
키워드 파이썬 컨벤션에 해당하는 블로그 처리할 수 있는 페이징 수 : 2


포스팅 URL : http://blog.naver.com/rkdgml6332?Redirect=Log&logNo=220711492180
포스팅 제목 : 파이썬 코딩 컨벤션
포스팅 설명 : PEP8 : PEP8에 대해 잘 정리된 글:
포스팅 날짜 : 16.05.16
블로거 이름 : 인생의 게임
포스팅 내용 :

PEP8 : PEP 8 -- Style Guide for Python CodeThe official home of the Python Programming Languagewww.python.orgPEP8에 대해 잘 정리된 글:파이썬 코딩 컨벤션PEP 8을 통해 파이썬 코딩 컨벤션을 알아봅니다.spoqa.github.io 


포스팅 URL : http://blog.naver.com/rkawk01?Redirect=Log&logNo=70148803042
포스팅 제목 : 파이썬 Docstring
포스팅 설명 : 이때에 이 메소드는 슈퍼클래스의 메소드를 호출해선 안된다.만약 서브클래스 메서드에서 슈퍼클래스 메서드를 호출했다면 &quot;extend&quot; 동사를 써서 명시한다. 파이썬 네이밍 컨벤션은 여기서..
포스팅 날짜 : 12.10.10
블로거 이름 : 서쪽숲
포스팅 내용 :

http://www.python.org/dev/peps/pep-0257/#id20파이썬을 쓰다 어느순간 보니 코딩을 C++스럽게 하고 있는거 같아서코딩 컨벤션을 좀 뒤지다 엉뚱하게 Docstring이란 것을 발견해서 대충 요약.Docstring은 언어적으로 지원하는 정규화된 주석의 표현"""내용""" 와 같이 쌍따옴표 세개를 연속으로 붙여서 작성파일의 처음이나 클래스선언 다음, 함수 선언 바로 다음줄에 작성작성된 Docstring은 런타임에 __doc__멤버로 접근 가능다중라인 DocString첫줄엔 요약 내용 작성그 다음 한 줄을 공백으로 둠자세한 내용을 그 다음에 여러 줄로 작성모듈의 Docstring익스포트하고 있는 있는 클래스, 예외, 함수들을 각각 한 줄 짜리 요약과 함께 나열해야한다.함수의 Docstring함수의 행위와 인자, 리턴값, 영향, 발생하는 예외들을 요약한다.__init__ 및 private메서드들도 각자 Docstring을 작성한다.클래스의 Docstring클래스가 상속중이라면 클래스의 Docstring에 해당 내용을 언급하고 차이점을 요약해둔다.만약 슈퍼클래스의 메서드를 오버라이드 했다면 Docstring에 "override" 동사를 써서 명시한다. 이때에 이 메소드는 슈퍼클래스의 메소드를 호출해선 안된다.만약 서브클래스 메서드에서 슈퍼클래스 메서드를 호출했다면 "extend" 동사를 써서 명시한다.파이썬 네이밍 컨벤션은 여기서..



포스팅 URL : http://blog.naver.com/ktw1332?Redirect=Log&logNo=220547091498
포스팅 제목 : Python Coding Convention(파이썬 코딩 컨벤션)
포스팅 설명 : https://plus.google.com/+rowoonlee/posts/SFKzxEcs5qB http://kenial.tistory.com/902 http://gadgetlip.tistory.com/entry/PEP8-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EB%84%A4%EC%9D%B4%EB%B0%8D-%EC%BB...
포스팅 날짜 : 15.11.23
블로거 이름 : Comma
포스팅 내용 :

https://plus.google.com/+rowoonlee/posts/SFKzxEcs5qB안녕하세요^^
파이썬 코딩 컨벤션 관련 링크 몇개 올립니다~

PEP Index > PEP 8...안녕하세요^^
파이썬 코딩 컨벤션 관련 링크 몇개 올립니다~

PEP Index > PEP 8 -- Style Guide for Python Code
http://legacy.pytho...plus.google.comhttp://kenial.tistory.com/902PEP-0008 파이썬 코드 스타일 가이드(Style Guide for Python Code) 한글 번역이 문서는 현재 https://bitbucket.org/sk8erchoi/peps-korean에서 공동 번역이 이루어지고 있습니다. 관심 있는 분들의 참여 부탁드립니다.   ---...kenial.tistory.comhttp://gadgetlip.tistory.com/entry/PEP8-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EB%84%A4%EC%9D%B4%EB%B0%8D-%EC%BB%A8%EB%B2%A4%EC%85%98PEP8 파이썬 네이밍 컨벤션출처: http://legacy.python.org/dev/peps/pep-0008/ 패키지 및 모듈 이름 모듈은 짧은 소문자 이름이 좋다. 가독성을 높여준다면 밑줄정도는 사용...gadgetlip.tistory.com  


포스팅 URL : http://blog.naver.com/hico01?Redirect=Log&logNo=221127948082
포스팅 제목 : 파이썬을 여행하는... 사례와 실용 라이브러리로 더 파이썬답게
포스팅 설명 : / 책에서 다루는 내용 스타일, 컨벤션, 관용구를 배워 훌륭한 파이썬 코드 작성하기 파이썬 오픈 소스 라이브러리 속 훌륭한 코드 둘러보기 파이썬 코드 패키징과 배포를 위한 최고의 방법 알아보기 콘솔...
포스팅 날짜 : 17.10.29
블로거 이름 : 이미지로 보는 세상
포스팅 내용 :

거대한 파이썬 세상을 모험하는 프로그래머를 위한 안내서파이썬을 '파이썬답게' 쓰려면 어떻게 해야 할까? 파이썬스러운 코드라는 게 도대체 어떤 의미일까? 내가 작성한 코드를 파이썬답다고 판단할 수 있는 기준은 무엇일까? 『파이썬을 여행하는 히치하이커를 위한 안내서』는 속 시원하게 답을 찾기 어려운 '파이썬다운 프로그램 작성법'을 명료하고 간결하게 정리한 가이드다. 여기에는 초보자는 물론 더 나은 코딩 기술을 고민하는 중급 이상의 파이썬 프로그래머에게 통찰을 주는 내용을 담았다. 이 책은 세 가지 구성으로 나뉜다. 1부에서는 파이썬 2와 파이썬 3을 비교하며 상황에 맞는 텍스트 편집기와 대화형 개발 환경을 선택할 수 있도록 돕는다. 또한 다양한 인터프리터 옵션을 소개하므로, 아직 파이썬에서 가능한 게 뭔지 모르더라도 필요에 맞는 인터프리터를 찾을 수 있다. 2부에서는 오픈 소스 커뮤니티에서 모범이 되는 예제 코드를 통해 파이썬스러운 스타일이 무엇인지 설명한다. 2부를 다 읽고 나면 스스로 오픈 소스 코드를 심도 있게 읽어 보고 실험해 볼 수 있다. 3부에서는 파이썬 커뮤니티에서 주로 사용하는 광대한 라이브러리 은하계를 둘러본다. 이 책은 파이썬 커뮤니티 집단 지성의 결과물로, 파이썬 고수들의 좋은 습관이 배어 있는 모범 사례와 노하우를 문서화한 유용한 자료집이다. 진정한 '파이써니스타'가 될 준비가 되었는가? 이 책을 통해 파이썬을 '제대로' 쓰는 방법과 효율적이면서 성능을 높이는 파이썬 프로그램 작성법을 살펴보고, 파이썬 프로그래머로서 기본을 뛰어넘어 한 단계 도약해 보자./책에서 다루는 내용 스타일, 컨벤션, 관용구를 배워 훌륭한 파이썬 코드 작성하기 파이썬 오픈 소스 라이브러리 속 훌륭한 코드 둘러보기 파이썬 코드 패키징과 배포를 위한 최고의 방법 알아보기 콘솔 애플리케이션부터 GUI, 웹 어플리케이션까지 다양한 파이썬 사용자 상호작용 라이브러리 살펴보기/ 시스템 관리, C와 C++ 라이브러리와의 인터페이스, 파이썬 속도 향상을 위한 도구 배우기 비동기 동작, 직렬화, 암호를 위한 네트워킹 라이브러리 사용하기 이미지, 오디오 프로세싱 도구를 포함한 데이터 지속성과 데이터 작업 라이브러리 살펴보기(출판사 책소개)1부 들어가기1장 인터프리터 선택하기 __파이썬 2와 3 중 어느 버전을 선택할까?  __추천하는 파이썬 버전 __파이썬 3가 최선일까?  __구현 2장 파이썬 설치하기 __맥에 파이썬 설치하기 __리눅스에 파이썬 설치하기__윈도우에 파이썬 설치하기__상용 파이썬 재배포판3장 개발 환경__텍스트 편집기__통합 개발 환경__기능이 강화된 대화형 도구__격리 도구2부 실전 돌입하기4장 훌륭한 코드 작성하기 __코드 스타일__프로젝트 구조화하기__코드 테스트__문서__로그__라이선스 선택5장 훌륭한 코드 읽어 보기__프로젝트의 공통 특성 __HowDoI __Diamond __Tablib __Requests __Werkzeug __Flask 6장 훌륭한 코드 배포하기 __유용한 단어와 콘셉트 __코드 패키징__코드 동결하기3부 시나리오 가이드7장 사용자와의 상호작용 __Jupyter Notebook  __명령줄 애플리케이션 __GUI 애플리케이션__웹 애플리케이션8장 코드 관리와 개선__지속적 통합 __시스템 관리__속도9장 소프트웨어 인터페이스 __웹 클라이언트__데이터 직렬화 __분산 시스템 __암호10장 데이터 작업 __과학 애플리케이션 __텍스트 작업과 텍스트 마이닝__이미지 작업11장 데이터 지속성 __구조화된 파일 __데이터베이스 라이브러리  부록 A 추가적으로 참고할 사항 /


파이썬을 여행하는 히치하이커를 위한 안내서

작가
케네스 라이츠, 타냐 슐로서
출판
인사이트
발매
2017.10.31.

리뷰보기




포스팅 URL : http://blog.naver.com/side_dishs?Redirect=Log&logNo=30161478701
포스팅 제목 : 파이썬 코딩 컨벤션이 예제로 잘 정리된 링크
포스팅 설명 : https://github.com/collective/collective.gallery/tree/master/collective/gallery/tests
포스팅 날짜 : 13.03.04
블로거 이름 : 반찬가게 - 프로그래밍의 이것저것
포스팅 내용 :

https://github.com/collective/collective.gallery/tree/master/collective/gallery/tests


포스팅 URL : http://blog.naver.com/goddes4?Redirect=Log&logNo=220092875516
포스팅 제목 : 코딩컨벤션
포스팅 설명 : 파이썬 코딩 컨벤션 - 들여쓰기는 공백 4칸을 권장 - 한 줄은 최대 79자 까지 - 클래스 내의 메소드 정의는 1줄씩 띄어쓰기 - 불필요한 공백은 피함 - = 연산자는 붙여씀 - 주석은 항상 갱신, 불필요한 주석은...
포스팅 날짜 : 14.08.15
블로거 이름 : 태영이의 지식 창고
포스팅 내용 :

파이썬 코딩 컨벤션- 들여쓰기는 공백 4칸을 권장- 한 줄은 최대 79자 까지- 클래스 내의 메소드 정의는 1줄씩 띄어쓰기- 불필요한 공백은 피함- = 연산자는 붙여씀- 주석은 항상 갱신, 불필요한 주석은 삭제- 소문자 L, 대문자 O, 대문자 I는 변수명으로 사용하지 말것- 함수명은 소문자로 구성, 필요하면 밑줄로 나눔  


포스팅 URL : http://blog.naver.com/hownam?Redirect=Log&logNo=220568760840
포스팅 제목 : 파이썬 라이브러리를 활용한 데이터 분석
포스팅 설명 : 3 import 컨벤션 1.6.4 용어 1.7 감사의 말 CHAPTER 2 사례 소개 2.1 bit.ly의 1.usa.gov 데이터 2.1.1 순수 파이썬으로 표준시간대 세어보기 2.1.2 pandas로 표준시간대 세어보기 2.2 MovieLens의 영화 평점...
포스팅 날짜 : 15.12.15
블로거 이름 : 즐겁게 살기
포스팅 내용 :

 A.5 파일과 운영체제



포스팅 URL : http://blog.naver.com/warren7027?Redirect=Log&logNo=221023873854
포스팅 제목 : 6. 함수, Scoping Rule, 재귀함수
포스팅 설명 : PEP8 - 파이썬 코딩 컨벤션 기준# 들여쓰기 4 SPACE , 한줄은 최대 79자, 불필요한 공백은 피함.# 연산자는 1칸 이상 안띄움.# 주석은 항상 갱신, 불필요한 주석은 삭제# 함수는...
포스팅 날짜 : 17.06.07
블로거 이름 : 배움과 공유
포스팅 내용 :

# 33강-35강/71강#-------------- 함수 기본 (1) ---------------------# 여러명이서 코드를 함께 작성할 경우 함수별로 파트를 나눠 코딩한다.# 프로그램을 기능별로 나누는 방법 1. 함수, 2. 객체, 3. 모듈# 함수에 대한 기본 컨셉 공부# 같은 기능을 수행하는 코드# def calculate_rectangle_area(x,y):#     print("함수가 실행 중입니다.")#     return x*y## rectangle_x = 10# rectangle_y = 20# print("사각형 x의 길이", rectangle_x)# print("사각형 y의 길이", rectangle_y)# #area = [1.3,4,3,5,2]# #print(area)# print("사각형의 넓이",calculate_rectangle_area(rectangle_x \# ,rectangle_y))#** 제곱# parameter 설계된 인터페이스 그 자체.# argument 설계된 함수를 실제사용할 시 값.# 리턴 값 유무에 따라 함수 수행이 달라짐.# 화면을 지우는 함수는 리턴 값이 없음.# ctrl + / 주석#---------------- 함수 기본 (2) ------------------# 함수 호출 방식# 1. call by value , 2. call by reference# 값을 던져주느냐 , 참조값을 던저주느냐# 1. 함수에 인자를 넘길 때 값만 넘김.# 1. 함수내 인자값 변경시, 호출자에 영향을 주지 않음.# 2. 함수에 인자를 넘길 때 메모리 주소를 넘김# 파이썬은 객체의 주소가 함수로 전달되는 방식# ex) 리스트 생성 시 2개 생성하고 참조값 같도록 한다음 append하면 함께 추가됨.# def spam(eggs):#     eggs.append(1)#     eggs=[2,3]## ham = [0]# spam(ham)# print(ham)# 변수의 범위(Scoping Rule)# 변수가 사용되는 범위, 지역변수(함수내), 전역변수(프로그램 전체)## def test(t):#     print (x)#     t = 20#     print ("In fucntion:", t)## x = 10# test(x)# print(t)# 전역 변수는 함수에서 사용가능# but, 함수내에 전역변수와 같은 이름의 변수를 선언하면 새로운 지역변수가 생김.# Swap# 함수를 통해 변수 간의 값을 교환하는 함수# 재귀함수# 자기자신을 호출하는 함수, 반드시 종료 조건이 있어야함.# 5! , 5*4!, 5*4*3!, 5*4*3*2*1# def factorial(x):#     for x in range(x,x-1):#         if x == 1:#             x += x* x-1#         break#     return x## print(factorial(5))## x = 5# for x in range(x,0,-1):#     temp = x * x#     x = x - 1##     print(x)#     print(temp)##############재귀 함수 ex)###################### def factorial(n):#     if n == 1:#         return 1#     else:#         return n * factorial(n-1)# # print(factorial(int(input("재귀함수 테스트 : "))))#for j in range(i):#    i = 1#    i=i+1#    print("number of loop",i)# for i in range(1,10,2):#   print(i)# result = 1,3,5,7,9# for i in range(1,10,-1):#   print(i)# result = 10,9,8,7# while문# 조건이 만족하는 동안에 반복명령 수행# i = 1# while i < 10:# print(i)# i+=1# reult = 1,2,3,4,5,6,7,8,9# 반복제어 - break, continue    # for i in range(10):    #     if i == 5:    #         break # 많이 쓰임, 조건을 만나면 반복 중단을 함.    #     print(i)    # print("EOP")    #    # for i in range(10):    #     if i ==5: continue # 조건을 만나면 건너뜀, 잘안쓰임.    #     print(i)    # print("EOP")#########코딩 컨벤션과 함수 작성법########### 35/71# 프로그래밍 = 팀플레이# 좋은 코드 = 사람이 이해할 수 있는 코드# 사람의 이해를 돕기 위한 코딩 규칙 = 코딩 컨벤션# PEP8 - 파이썬 코딩 컨벤션 기준# 들여쓰기 4 SPACE , 한줄은 최대 79자, 불필요한 공백은 피함.# 연산자는 1칸 이상 안띄움.# 주석은 항상 갱신, 불필요한 주석은 삭제# 함수는 언제 만드는가?# 1. 한번이상 사용되는 코드.# 2. 복잡한 수식이나, 복잡한 코드는 식별이 가능한 함수로 변환 필요.# 3. 캡슐화, 내부로직은 모르지만 함수를 가져다 쓸 수 있도록 만듬.


포스팅 URL : http://blog.naver.com/pjt3591oo?Redirect=Log&logNo=220876911631
포스팅 제목 : [python] 단위 테스트 하기
포스팅 설명 : 파이썬에서는 컨벤션에 따라 테스트 함수는 test로 시작을 해야한다. $ python test.py C:\test&gt;python test.py ..... ---------------------------------------------------------------------- Ran 1...
포스팅 날짜 : 16.12.03
블로거 이름 : 멍개님의블로그
포스팅 내용 :

python에서는 unittest를 이용하여 단위테스트를 할 수 있다.test.py12345678910111213141516171819import unittest class UtilsTest(unittest.TestCase):     def setUp(self):        # 테스트에 필요한 설정     def test_get_home_url(self):        self.assertEqual(1, 1)    # 값이 같은지 검사        self.assertNotEqual(1, 1) # 값이 다른지 검사        assertTrue(True)          # true인지 검사        assertRaises(False)       # false인지      def tearDown(self):        # setUp과 반대        # 모든 테스트가 성공했을 때 실행 if __name__ == '__main__':    unittest.main()csunittest에서 TestCase를 상속 받아서 테스트 코드를 작성 할 수 있다.main()을 호출하면 test 시작하는 테스트 함수를 실행을 한다.파이썬에서는 컨벤션에 따라 테스트 함수는 test로 시작을 해야한다.$ python test.py
C:\test>python test.py
.....
----------------------------------------------------------------------
Ran 1 tests in 0.001s

OK

몇개의 테스트 실행했는지 나타나게 된다. assertEqual은 두개로 전달된 파라메터가 일치하지 않으면 에러를 띄운다.self.assertEqual(1, 2)$ python test.py
F....======================================================================FAIL: test_get_home_url (__main__.UtilsTest)----------------------------------------------------------------------Traceback (most recent call last):  File "test.py", line 27, in test_get_home_url    self.assertEqual(1, 2)AssertionError: 1 != 2    => 테스트가 실패 할 경우 해당 지점의 값을 보여준다.----------------------------------------------------------------------Ran 5 tests in 0.002sFAILED (failures=1)
 만약 테스트 실패가 날 경우 위처럼 해당 지점에서의 값을 보여주면서 실패했다고 띄어준다.javascript의 mocha와 비교 했을때는 비주얼 적으로도 mocha가 더 괜찮아 보인다. 사실 그럴 수 밖에 없는건 mocha는 프레임워크이고 unittest는 모듈이기 때문에 어쩔 수 없는것 같다.


포스팅 URL : http://blog.naver.com/seungbeomi?Redirect=Log&logNo=50164250549
포스팅 제목 : [python] Style Guide for Python Code
포스팅 설명 : 파이썬 코딩컨벤션 http://www.python.org/dev/peps/pep-0008/ http://blog.naver.com/joycestudy/100117593331 http://rasingbull.tistory.com/entry/%ED%8E%8Cpython-coding-rule
포스팅 날짜 : 13.02.26
블로거 이름 : devlog
포스팅 내용 :

파이썬 코딩컨벤션 http://www.python.org/dev/peps/pep-0008/http://blog.naver.com/joycestudy/100117593331http://rasingbull.tistory.com/entry/%ED%8E%8Cpython-coding-rule



Process finished with exit code 137 (interrupted by signal 9: SIGKILL)
```

-----------------------------------------------

공부 목적으로 만들고 있기 때문에 잦은 버그 픽스나 기능 추가가 있을 수도 있습니다.<br>
버그나 문의 사항은 이슈에 남겨주시면 감사하겠습니다. :)

by 체리픽<br>
https://cherrypick.co.kr
