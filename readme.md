# ⚡ PostgreSQL 기본 개념 및 성능 개선 노하우
## 📄 소개
PostgreSQL의 기본 개념과 함께 운영환경에서 데이터베이스 관리 및 성능 향상 경험을 공유하기 위한 Repository입니다. [산업의 역군](https://www.sankun.com/)에서 건설 분야의 '빅'데이터를 PostgreSQL 관계형 데이터베이스로 관리하며 얻은 실질적인 노하우와 성능 개선 방법을 기록하였습니다. 스타트업이 마주하는 자원의 한계 속에서도, 효율적인 자원 분배와 체계적인 모니터링을 통해 매일 수만 건의 데이터를 실시간으로 동기화하고, 수천만 건의 데이터를 효과적으로 조회하는 방법을 탐구합니다.

본 자료는 단순히 데이터베이스의 인덱스 설정이나 파티셔닝을 넘어, PostgreSQL의 구조와 원리를 정확히 이해하고 이를 바탕으로 최적화된 데이터베이스 설계 및 운영 전략을 마련하기 위한 것입니다. 이 과정에서 PostgreSQL [공식 문서](https://www.postgresql.org/)를 근간으로 삼아, 기본 개념을 명확히 하고, 실제 운영 데이터를 기반으로 한 성능 개선 사례들을 공유하여, 다양한 DB 스펙과 데이터 양에 따른 최적화 방안을 제시하고자 합니다.

이 Repository는 계속해서 업데이트될 예정이며, 더 깊이 있는 정보와 경험을 공유하고자 합니다. 실제 적용 예제들은 [junhkang.tistory.com](http://junhkang.tistory.com/)에서 더욱 상세히 다루고 있으니 참고하시길 바랍니다.

## 📜 목차
### 개념

- [2단계 커밋 프로토콜(Two-Phase Commit Protocol), Prepare transaction](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/2%EB%8B%A8%EA%B3%84%20%EC%BB%A4%EB%B0%8B%20%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C(Two-Phase%20Commit%20Protocol)%2C%20Prepare%20transaction.md)
- [MVCC (Multi-Version Concurrency Control)](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/MVCC%20(Multi-Version%20Concurrency%20Control).md)
- [PostgreSQL Lock이란? (조회 및 kill, Dead lock)](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/Postgresql%20Lock%EC%9D%B4%EB%9E%80%3F%20(%EC%A1%B0%ED%9A%8C%20%EB%B0%8F%20kill%2C%20Dead%20lock).md)
- [Trigger, Procedure, Function (history 관리하기)](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/Trigger%2C%20Procedure%2C%20Function%20(history%20%EA%B4%80%EB%A6%AC%ED%95%98%EA%B8%B0).md)
- [Vacuum 개념 및 적절한 사용](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/Vacuum%20%EA%B0%9C%EB%85%90%20%EB%B0%8F%20%EC%A0%81%EC%A0%88%ED%95%9C%20%EC%82%AC%EC%9A%A9.md)
- [WAL (Write-Ahead Logging), 아카이브 모드 백업(Archive mode backup)의 개념 및 장단점](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/WAL%20(Write-Ahead%20Logging)%2C%20%EC%95%84%EC%B9%B4%EC%9D%B4%EB%B8%8C%20%EB%AA%A8%EB%93%9C%20%EB%B0%B1%EC%97%85(Archive%20mode%20backup)%EC%9D%98%20%EA%B0%9C%EB%85%90%20%EB%B0%8F%20%EC%9E%A5%EB%8B%A8%EC%A0%90.md)
- [데이터베이스 상속(Inheritance)의 개념과 사용법 및 성능비교 (Inherits, Only)](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4%20%EC%83%81%EC%86%8D(Inheritance)%EC%9D%98%20%EA%B0%9C%EB%85%90%EA%B3%BC%20%EC%82%AC%EC%9A%A9%EB%B2%95%20%EB%B0%8F%20%EC%84%B1%EB%8A%A5%EB%B9%84%EA%B5%90%20(Inherits%2C%20Only).md)
- [뷰(VIEW) 테이블 개념 및 사용, 생성(CREATE), 수정(CREATE OR REPLACE), 삭제(DROP)](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%EB%B7%B0(VIEW)%20%ED%85%8C%EC%9D%B4%EB%B8%94%20%EA%B0%9C%EB%85%90%20%EB%B0%8F%20%EC%82%AC%EC%9A%A9%2C%20%EC%83%9D%EC%84%B1(CREATE)%2C%20%EC%88%98%EC%A0%95(CREATE%20OR%20REPLACE)%2C%20%EC%82%AD%EC%A0%9C(DROP).md)
- [시퀀스(Sequence)의 개념과 사용법(생성, 삭제, 조회 등)](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%EC%8B%9C%ED%80%80%EC%8A%A4(Sequence)%EC%9D%98%20%EA%B0%9C%EB%85%90%EA%B3%BC%20%EC%82%AC%EC%9A%A9%EB%B2%95(%EC%83%9D%EC%84%B1%2C%20%EC%82%AD%EC%A0%9C%2C%20%EC%A1%B0%ED%9A%8C%20%EB%93%B1).md)
- [역할 및 권한 (ROLE, USER, GROUP) 개념 및 설정](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%EC%97%AD%ED%95%A0%20%EB%B0%8F%20%EA%B6%8C%ED%95%9C%20(ROLE%2C%20USER%2C%20GROUP)%20%EA%B0%9C%EB%85%90%20%EB%B0%8F%20%EC%84%A4%EC%A0%95.md)
- [외래키(Foreign Keys) 개념, 사용법, 장단점, 적용검토](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%EC%99%B8%EB%9E%98%ED%82%A4(Foreign%20Keys)%20%EA%B0%9C%EB%85%90%2C%20%EC%82%AC%EC%9A%A9%EB%B2%95%2C%20%EC%9E%A5%EB%8B%A8%EC%A0%90%2C%20%EC%A0%81%EC%9A%A9%EA%B2%80%ED%86%A0.md)
- [윈도우 함수(Window Functions)의 개념, 성능 및 사용법 (over, sum, rank, ntitle, cume_dist 등...)](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%EC%9C%88%EB%8F%84%EC%9A%B0%20%ED%95%A8%EC%88%98(Window%20Functions)%EC%9D%98%20%EA%B0%9C%EB%85%90%2C%20%EC%84%B1%EB%8A%A5%20%EB%B0%8F%20%EC%82%AC%EC%9A%A9%EB%B2%95%20(over%2C%20sum%2C%20rank%2C%20ntitle%2C%20cume_dist%20%EB%93%B1...).md)
- [제약조건 (Constraint) 개념 및 설정 (Primary Keys, Foreign Keys, Unique, Not null, Check)](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%EC%A0%9C%EC%95%BD%EC%A1%B0%EA%B1%B4%20(Constraint)%20%EA%B0%9C%EB%85%90%20%EB%B0%8F%20%EC%84%A4%EC%A0%95%20(Primary%20Keys%2C%20Foreign%20Keys%2C%20Unique%2C%20Not%20null%2C%20Check).md)
- [트랜잭션(Transaction)의 개념 및 사용](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98(Transaction)%EC%9D%98%20%EA%B0%9C%EB%85%90%20%EB%B0%8F%20%EC%82%AC%EC%9A%A9.md)
- [트랜잭션(Transaction)의 작동 원리](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98(Transaction)%EC%9D%98%20%EC%9E%91%EB%8F%99%EC%9B%90%EB%A6%AC.md)
- [함수(Function)의 정의 및 상세 사용법 (다양한 예제)](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%ED%95%A8%EC%88%98(Function)%EC%9D%98%20%EC%A0%95%EC%9D%98%20%EB%B0%8F%20%EC%83%81%EC%84%B8%20%EC%82%AC%EC%9A%A9%EB%B2%95%20(%EB%8B%A4%EC%96%91%ED%95%9C%20%EC%98%88%EC%A0%9C).md)
- 인덱스 (index)
	- [인덱스(INDEX)개념 및 생성, 삭제, 분석, 설계 방법](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%EC%9D%B8%EB%8D%B1%EC%8A%A4/%EC%9D%B8%EB%8D%B1%EC%8A%A4(INDEX)%EA%B0%9C%EB%85%90%20%EB%B0%8F%20%EC%83%9D%EC%84%B1%2C%20%EC%82%AD%EC%A0%9C%2C%20%EB%B6%84%EC%84%9D%2C%20%EC%84%A4%EA%B3%84%20%EB%B0%A9%EB%B2%95.md)
	- [B-tree 인덱스의 원리 및 특징](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%EC%9D%B8%EB%8D%B1%EC%8A%A4/B-tree%20%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%9D%98%20%EC%9B%90%EB%A6%AC%20%EB%B0%8F%20%ED%8A%B9%EC%A7%95.md)
	- [GIN인덱스의 원리 및 특징](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%EC%9D%B8%EB%8D%B1%EC%8A%A4/GIN%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%9D%98%20%EC%9B%90%EB%A6%AC%20%EB%B0%8F%20%ED%8A%B9%EC%A7%95.md)
	- [GiST인덱스의 원리 및 특징](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%EC%9D%B8%EB%8D%B1%EC%8A%A4/GiST%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%9D%98%20%EC%9B%90%EB%A6%AC%20%EB%B0%8F%20%ED%8A%B9%EC%A7%95.md)
	- [Hash 인덱스의 원리 및 특징](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%EC%9D%B8%EB%8D%B1%EC%8A%A4/Hash%20%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%9D%98%20%EC%9B%90%EB%A6%AC%20%EB%B0%8F%20%ED%8A%B9%EC%A7%95.md)
	- [SP-GiST인덱스의 원리 및 특징](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%EC%9D%B8%EB%8D%B1%EC%8A%A4/SP-GiST%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%9D%98%20%EC%9B%90%EB%A6%AC%20%EB%B0%8F%20%ED%8A%B9%EC%A7%95.md)
	- [BRIN 인덱스의 원리 및 특징](https://github.com/junhkang/postgresql/blob/main/%EA%B0%9C%EB%85%90/%EC%9D%B8%EB%8D%B1%EC%8A%A4/BRIN%20%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%9D%98%20%EC%9B%90%EB%A6%AC%20%EB%B0%8F%20%ED%8A%B9%EC%A7%95.md)
### 사용
- [날짜 형태 검증하기 (ERROR date time field value out of range)](https://github.com/junhkang/postgresql/blob/main/%EC%82%AC%EC%9A%A9/%EB%82%A0%EC%A7%9C%20%ED%98%95%ED%83%9C%20%EA%B2%80%EC%A6%9D%ED%95%98%EA%B8%B0%20(ERROR%20date%20time%20field%20value%20out%20of%20range).md)
- [문자열내 중복 공백, 단어 제거](https://github.com/junhkang/postgresql/blob/main/%EC%82%AC%EC%9A%A9/%EB%AC%B8%EC%9E%90%EC%97%B4%EB%82%B4%20%EC%A4%91%EB%B3%B5%20%EA%B3%B5%EB%B0%B1%2C%20%EB%8B%A8%EC%96%B4%20%EC%A0%9C%EA%B1%B0.md)
- [CREATE TABLE AS (결과물을 테이블로)](https://github.com/junhkang/postgresql/blob/main/%EC%82%AC%EC%9A%A9/CREATE%20TABLE%20AS%20(%EA%B2%B0%EA%B3%BC%EB%AC%BC%EC%9D%84%20%ED%85%8C%EC%9D%B4%EB%B8%94%EB%A1%9C).md)
- [ERROR text search configuration name "english" must be schema-qualified](https://github.com/junhkang/postgresql/blob/d3ae0de823d09d1bbb23efb15b2b2c6fb94eb3ad/ERROR%20text%20search%20configuration%20name%20%22english%22%20must%20be%20schema-qualified.md)
### 성능개선
- [쿼리 성능향상 (실행계획 보는 법, 상세 확인방법, Explain의 어떤 지표를 봐야할까?)](https://github.com/junhkang/postgresql/blob/main/%EC%84%B1%EB%8A%A5%ED%96%A5%EC%83%81/%EC%BF%BC%EB%A6%AC%20%EC%84%B1%EB%8A%A5%ED%96%A5%EC%83%81%20(%EC%8B%A4%ED%96%89%EA%B3%84%ED%9A%8D%20%EB%B3%B4%EB%8A%94%20%EB%B2%95%2C%20%EC%83%81%EC%84%B8%20%ED%99%95%EC%9D%B8%EB%B0%A9%EB%B2%95%2C%20Explain%EC%9D%98%20%EC%96%B4%EB%96%A4%20%EC%A7%80%ED%91%9C%EB%A5%BC%20%EB%B4%90%EC%95%BC%ED%95%A0%EA%B9%8C%3F).md)
- [미사용 인덱스(INDEX) 찾기 및 삭제, 성능향상](https://github.com/junhkang/postgresql/blob/main/%EC%84%B1%EB%8A%A5%ED%96%A5%EC%83%81/%EB%AF%B8%EC%82%AC%EC%9A%A9%20%EC%9D%B8%EB%8D%B1%EC%8A%A4(INDEX)%20%EC%B0%BE%EA%B8%B0%20%EB%B0%8F%20%EC%82%AD%EC%A0%9C%2C%20%EC%84%B1%EB%8A%A5%ED%96%A5%EC%83%81.md)
- [Full Text Search를 활용한 데이터베이스 성능 향상](https://github.com/junhkang/postgresql/blob/main/%EC%84%B1%EB%8A%A5%ED%96%A5%EC%83%81/Full%20Text%20Search%EB%A5%BC%20%ED%99%9C%EC%9A%A9%ED%95%9C%20%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4%20%EC%84%B1%EB%8A%A5%20%ED%96%A5%EC%83%81.md)
- [대량 데이터 인서트 시 성능 개선 및 주의사항](https://github.com/junhkang/postgresql/blob/main/%EC%84%B1%EB%8A%A5%ED%96%A5%EC%83%81/%EB%8C%80%EB%9F%89%20%EB%8D%B0%EC%9D%B4%ED%84%B0%20%EC%9D%B8%EC%84%9C%ED%8A%B8%20%EC%8B%9C%20%EC%84%B1%EB%8A%A5%20%EA%B0%9C%EC%84%A0%20%EB%B0%8F%20%EC%A3%BC%EC%9D%98%EC%82%AC%ED%95%AD.md)
- [명시적 JOIN 절로 플래너(Planner) 제어, 성능 향상](https://github.com/junhkang/postgresql/blob/main/%EC%84%B1%EB%8A%A5%ED%96%A5%EC%83%81/%EB%AA%85%EC%8B%9C%EC%A0%81%20JOIN%20%EC%A0%88%EB%A1%9C%20%ED%94%8C%EB%9E%98%EB%84%88(Planner)%20%EC%A0%9C%EC%96%B4%2C%20%EC%84%B1%EB%8A%A5%20%ED%96%A5%EC%83%81.md)
- [인덱스(INDEX)와 정렬(ORDER BY), ORDER BY 성능개선, 효율적인 인덱스 적용](https://github.com/junhkang/postgresql/blob/main/%EC%84%B1%EB%8A%A5%ED%96%A5%EC%83%81/%EC%9D%B8%EB%8D%B1%EC%8A%A4(INDEX)%EC%99%80%20%EC%A0%95%EB%A0%AC(ORDER%20BY)%2C%20ORDER%20BY%20%EC%84%B1%EB%8A%A5%EA%B0%9C%EC%84%A0%2C%20%ED%9A%A8%EC%9C%A8%EC%A0%81%EC%9D%B8%20%EC%9D%B8%EB%8D%B1%EC%8A%A4%20%EC%A0%81%EC%9A%A9.md)
