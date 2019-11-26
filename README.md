# 7Segments
2. HW1_2
① 개요
 P2에 연결된 8개의 푸시버튼 스위치 입력을 받아, 스위치가 눌린 개수를 하나의      7-SEGMENT에 표시한다.


② 소스 코드
	ORG	0			;PC = 0H부터 시작
	MOV	P2, #0FFH 		;P2를 INPUT으로 선언
	MOV	DPTR, #300H		;DPTR는 300H를 가리킴

HERE:	MOV 	A, P2			;스위치 값을 읽어온다
	MOV	R1,#0			;R1값을 초기화 한다
	MOV	R0, #8		;반복횟수 = 8

LP: 	RRC	A			;A를 오른쪽으로 회전한다(비트 하나씩 값을 확인)
	JC	NP			;C값을 확인해서
	INC	R1			;0이면 스위치의 개수가 담긴 변수 값을 증가하고
NP:	DJNZ	R0, LP			;1이면 다시 반복문으로 돌아가 다음 비트를 확인한다
	MOV	A, R1			;눌러진 스위치의 개수를 불러와서
	MOVC A, @A+DPTR		;LOOK UP TABLE을 참조해 LED값을 가져온다
	MOV	P1, A			;그 값을 P1에 출력한다
	SJMP 	HERE			;처음으로 돌아가 스위치 값을 다시 확인한다

	ORG 300H
TABLE:				;LOOK UP TABLE
DB	192,249,164,176,153,146,130,216,128

END






③ 동작 확인 및 분석
-눌러진 스위치의 개수 : 0












LED가 0을 표시한다

-눌러진 스위치의 개수 : 1

LED가 1을 표시한다

-눌러진 스위치의 개수 : 2

LED가 2를 표시한다


-눌러진 스위치의 개수 : 3

LED가 3을 표시한다

-눌러진 스위치의 개수 : 4

LED가 4를 표시한다

-눌러진 스위치의 개수 : 5
LED가 5를 표시한다

-눌러진 스위치의 개수 : 6

LED가 6을 표시한다

-눌러진 스위치의 개수 : 7

LED가 7을 표시한다

-눌러진 스위치의 개수 : 8

LED가 8을 표시한다
