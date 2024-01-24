개인 프로젝트 반려동물 다이어리 서버

- 펫 다이어리 DB 및 서버 구현(메인 프로젝트)(개인)
ㄴ Rest API를 사용하여 API 명세서 및 ERD 작성(Notion, https://www.notion.so/399d9a4d48264e229e404796baef8666)
ㄴ 서버는 스프링부트, DBMS는 MySQL 사용
ㄴ 디자인 패턴 적용 정리
    ㄴ 전략패턴 : 서비스의 기능 분할 - 각 기능(인증, 캘린더, 체크리스트, 커뮤니티)의 서비스에 들어가는 세부 기능들을 각각 알고리즘군으로 추상화
        ㄴ 각 알고리즘군은 트리형태이고, 각 알고리즘의 루트에 해당하는 추상클래스를 서비스에서 필드로 갖고 있는 형태
        ㄴ 다른 알고리즘을 사용한다면 구현 기능의 형태에 따라 루트의 자식으로 있는 추상클래스를 구현하여 사용 - 서비스 코드를 변경할 필요 없음
    ㄴ 추상 팩토리 패턴 : 각 기능의 서비스마다 기능 실행 전략 인스턴스를 생성 - 다른 전략 인스턴스로 구성할 시, 얘를 새로 구현하면 됨
    ㄴ 퍼사드 패턴 : 서비스의 기능을 각각 기능 전략 알고리즘의 한 메소드로 묶음 - 서비스 객체는 서버 내부 구현 방식에 대한 세부 내용을 알 필요 없음
    ㄴ 템플릿 메소드 패턴 : 체크리스트에서 사용자 아이디, 작성일 확인 시 작성 내역을 확인하는 방식을 추상화 - 작성 내역 확인 방식을 하위 클래스에서 결정하게 함
        ㄴ 확인 방식이 달라지면 템플릿 메소드를 갖고 있는 추상 클래스를 새로 구현하면 됨 - 확장성 보장
    ㄴ MVC 패턴 : 리액트 네이티브라는 View에서 Rest API를 스프링부트의 Controller에 전달 - Controller는 이를 Service(Model)에 전달하여 DB 및 관련 기능 수행
