SGML(Standar Generalized MarkUp Language)
 - 문서용 마크업 언어를 정의하기 위한 메타 언어
 - IBM에서 1960년대에 개발한 GML의 후속

HTML(Hyper TextMarkup Language)
 - 웹에서 문서를 기술하는 방식
 - 표준 문법에 의해서 태그(Tag)에 대한 정의나 용도를 미리 지정

XML 등장
 - HTML이 재사용성 등 구조적 문서ㅓ 작성에 적합하지 않음.

XML의 개요
 - 웹상에서 구조화된 데이터의 전송이 가능하도록 설계된 언어
 - 다른 시스템, 특히 인터넷에 연결된 시스템 간의 데이터 전달과 공유
 - 1996년 : W3C(Worl Wide Web Consortium)에서 제안
 - 1998년 2월 : W3C의 권고안, XML 1.0발표

스팩
 - XML 문서라 불리는 데이터 객체(Object)
 - XML 구문 분석기(SAX, DOM)

## XML프로세서 (Processor)
 - 프로세서를 사용하여 XML 문서들을 읽고 분석
 - 내용(Content)과 구조에 접속을 제공
 - SAX 
  ```
   - 이벤트 중심의 인터페이스
   - 문서의 전체 구조 정보를 메모리 상으로 불러오지 않고 단순히 문서 내의 특정 엘리먼트(Element)만 처리
  ```
 - DOM
 ```
 XML 문서를 트리 구조로 구성
 ```
 ##QT에서의 XML 모듈
  - SAX 파서와 DOM파서(parser)를 제공
  - SAX는 SAX2 자바 구현의 디자인을 따라서 구현
  - DOM은 W3C의 DOM LEVEL2 구현과 네임스페이스(Namespace)를 지원
  - QT 디자이너에서 저장을 위해 XML 형식을 사용
  - rcc파일과 ui파일
  - XML은 모듈로 제공
  - 프로젝트 파일에 'QT += xml'을 추가