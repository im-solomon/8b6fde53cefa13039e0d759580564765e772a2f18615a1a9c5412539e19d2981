# 프로그래밍 언어론 과제 2
### List를 써서 Set을 구현, 다음 함수를 Scheme으로 구현하시오. x는 int 타입의 숫자를 s, s1, s2등은 Set 타입의 개체를 나타낸다.  
![문법](/img/image01.png)
* (define (contains? x s) ...._) ; 결과는 boolean
* (define (is-empty? s) ...._) ; 결과는 boolean
* (define (singleton-set x) ...) ; 결과는 Set
* (define (intersection s1 s2) ...) ; 결과는 Set
* (define (union s1 s2) ...) ; 결과는 Set
* (define (filter s p) ...) ; p는 int를 받아서 boolean을 리턴하는 함수, 결과는 Set

### 함수 설명 및 소스 코드

* (define (contains? x s) ...._) ;
  - set s에 int x가 포함되어 있는지 확인, boolean 타입 반환
  ```
  (define (contains? x s)
	( cond
		((null? s) #f)
		((eq? x (car s)) #t)
		(else (contains? x (cdr s)))))
	
		

* (define (is-empty? s) ...._) ;
  - set s가 비어있는지 확인, boolean 타입 반환
  
* (define (singleton-set x) ...) ;
  - int x를 set으로 변환, set 타입 반환
  
* (define (intersection s1 s2) ...) ;
  - set s1을 기준으로 set s2와 비교하여 공통된 값 출력, set타입 반환
  
* (define (union s1 s2) ...) ;
  - set s, set 타입 반환
  
* (define (filter s p) ...) ;
  - set s에 x가 포함되어 있는지 확인하는 함수, set 타입 반환
  
