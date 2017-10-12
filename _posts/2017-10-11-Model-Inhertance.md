# Model Inhertance


1. Abstact inheritance
	- 추상 클래스
	- 비슷한 값 정의용으로 사용할 클래스, 실제로 테이블이 생성되지는 않음
	- 클래스 메타 부분에 abstract = True를 부여 하여 생성 
2. Multi-table inheritance
	- 테이블 상속 클래스
	- 부모의 모든 값을 내려 받아 테이블 생성
	- 부모의 속성 값을 가져와서 사용(자동으로 OneToOne으로 연결됨
3. Inheritance and reverse ralation

