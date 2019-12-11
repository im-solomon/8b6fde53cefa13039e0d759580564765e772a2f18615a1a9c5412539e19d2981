프로그래밍 언어론 과제 2
===========
### List를 써서 Set을 구현, 다음 함수를 Scheme으로 구현하시오. x는 int 타입의 숫자를 s, s1, s2등은 Set 타입의 개체를 나타낸다.  

* (define (contains? x s) ...._) ; 결과는 boolean
* (define (is-empty? s) ...._) ; 결과는 boolean
* (define (singleton-set x) ...) ; 결과는 Set
* (define (intersection s1 s2) ...) ; 결과는 Set
* (define (union s1 s2) ...) ; 결과는 Set
* (define (filter s p) ...) ; p는 int를 받아서 boolean을 리턴하는 함수, 결과는 Set

### 함수 설명 및 소스 코드
* (define (contains? x s) ...._) ;
  - set s에 int x가 포함되어 있는지 확인, boolean 타입 반환
```scheme
  (define (contains? x s)
	( cond
		((null? s) #f)
		((eq? x (car s)) #t)
		(else (contains? x (cdr s)))))
```
![1.contains](/img/1.contains_1.png)  
#

* (define (is-empty? s) ...._) ;
  - set s가 비어있는지 확인, boolean 타입 반환
```scheme
(define (is-empty? s) (null? s))
```
![2.is-empty](/img/2.is-empty_1.png)
#

* (define (singleton-set x) ...) ;
  - int x를 set으로 변환, set 타입 반환
```scheme
(define (singleton-set x) (cons x '()))
```
![3.singleton-set](/img/3.singleton-set_1.png)
#

* (define (intersection s1 s2) ...) ;
  - set s1을 기준으로 set s2와 비교하여 공통된 값 출력, set타입 반환
```scheme
(define (intersection s1 s2)
	(cond
	((is-empty? s1) '())
	((is-empty? s2) '())
	((contains? (car s1) s2) (cons (car s1) (intersection (cdr s1) s2)))
	(else (intersection (cdr s1) s2))))
```
![4.intersection](/img/4.intersection_1.png)
#

* (define (union s1 s2) ...) ;
  - set s1과 set s2의 원소를 합한 set 출력, set 타입 반환
```scheme
(define (union s1 s2)
	(cond
		((is-empty? s1) s2)
		((is-empty? s2) '())
		((contains? (car s1) s2) (union (cdr s1) s2))
		(else  (cons (car s1) (union (cdr s1) s2)))))
```
![5.union](/img/5.union_1.png)
#

* (define (filter s p) ...) ;
  - set s에 p함수를 적용시키는 함수, set 타입 반환
```scheme
(define (mod_3 n)
	(cond
		((= 0 (modulo n 3)) #t)
		(else #f)))

(define (filter s n)
	(cond
	((is-empty? s) '())
	((n (car s)) (cons (car s) (filter (cdr s) n)))
	(else (filter (cdr s) n))))
```
![6.filter](/img/6.filter_1.png)
#

### 추가 공부

* (define bubble-loop n s) ...);
  - set s의 원소를 오름차순으로 버블 정렬하는 함수, set 타입 반환
```scheme
(define (bubble s)
 (if (is-empty? (cdr s)) s
	(cond
	  ((< (car s) (cadr s)) (cons (car s) (bubble (cdr s))))
	  (else (cons (cadr s) (bubble (cons (car s) (cddr s) )))))))
	
	
(define (bubble-loop n s)
	(cond ((= n 1) (bubble s))
	(else (bubble-loop (- n 1) (bubble s)))))

예시
(bubble-loop (length (union '(7 8 9) '(1 4 7))) (union '(7 8 9) '(1 4 7)))
```
![7_1.bubble](/img/7_1.bubble.PNG)
![7_2.bubble-loop](/img/7_2.bubble-loop_1.png)
![7_3.bubble-loop_ex](/img/7_3.bubble-loop_ex.PNG)
#
