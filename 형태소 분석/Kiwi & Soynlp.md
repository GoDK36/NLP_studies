	1. Kiwi
		a. 정의
			Kiwipiepy는 한국어 형태소 분석기인 Kiwi(Korean Intelligent Word Identifier)의 Python 모듈입니다. C++로 작성되었고 다른 패키지에 의존성이 없으므로 C++ 컴파일이 가능한 환경이라면 어디에서나 Kiwipiepy를 사용 가능합니다.
			
			출처: <https://bab2min.github.io/kiwipiepy/v0.8.0/kr/> 
			
			
		b. 사용법
			i. Pip install kiwipiepy
		c. 특징
			i. 멀티스레딩 지원
				1) 단순 analyze는 단일 스레드를 지원하기에 코드를 직접 짜야한다
			ii. 코퍼스로부터 미등록 단어 추출 가능
				1) extract_word(reader, min_cnt= , max_word_len= , min_score= )
					a) reader -> 호출 가능한(callable) 객체여야 한다?
					b) min_cnt -> 추출할 단어가 입력 텍스트 내에서 최소 몇 번 이상 등장할지
					c) max_word_len -> 추출할 단어의 최대 길이
					d) min_score -> 추출할 단어의 최소 점수  
			iii. 사용자 사전 추가 가능
				1) add_user_word(word, tag="NNP", score=0)
				2) 사용자 정의 사전은 UTF-8로 인코딩된 텍스트 파일이어야한다
					a) 형식 -> 단어1 [탭문자] 품사태그 [탭문자] 단어점수
						i) 단어점수는 생략시 0점이다
			iv. 형태소 분석
				1) 점수제 방식으로 지원
					a) 사용자 사전에서 단어별 태깅의 수를 크게주냐 적게 주냐의 차이로 우선순위 선정 가능
				
	2. Soynlp
		a. 정의
			한국어 분석을 위한 pure python code 입니다. 학습데이터를 이용하지 않으면서 데이터에 존재하는 단어를 찾거나, 문장을 단어열로 분해, 혹은 품사 판별을 할 수 있는 비지도학습 접근법을 지향합니다.
			
			출처: <https://github.com/lovit/soynlp> 
			
		b. 사용법
			i. pip install soynlp
		c. 특징
			i. Noun Extracter
				1) _compunds_components
					a) 복합명사를 구성하는 단일명사 추출기
				2) LRGraph
					a) 명사의 양옆 정보를 get_l, get_r 형식으로 가지고 있다
			ii. Word Extracter
				1) OOV(Out of Vocabulary)문제를 해결하기 위한 기능
					a) https://github.com/lovit/soynlp/blob/master/tutorials/wordextractor_lecture.ipynb
				2) branching Entropy
					a) 단어의 양 옆(한국어에서는 주로 오른쪽)의 정보를 통해 어떤 단어일지에 대한 불확실성을 줄여가는 것
				3) Accesor Variety
					a) 단어 다음에 나올수있는 가지 수를 계산
					b) Branching Entropy의 하위 개념
				4) Cohesion Score
					a) open class(명사, 형용사, 동사, 부사)에서 새로운 단어가 생기기에 그 품사들을 바탕으로 분석을 진행하는 특징을 이용.
					b) 위의 두 가지 기법을 이용해서 수식을 통해 계산해서 점수를 부여.
			iii. Tokenizer
				1) Ltokenizer
					a) 한국어에선 왼쪽만 인식을 잘하면 오른쪽(ex. 조사)는 알아서 딸려온다
					b) WordExtracter로 단어에 점수를 부여하여 계산
				2) MaxScoreTokenizer
					a) 띄어쓰기가 제대로 이루어지지않은 문장에서 활용
				3) RegexTokenizer
					a) 규칙기반으로 토크나이징
					b) 언어가 바뀌는 부분을 단어로 인식(영어, 숫자 혼합)
			iv. POS Tagger
				1) 단어 사전을 통해 품사 태깅
			v. Vectorizer
				1) doc_to_bow, BOW 등으로 변환 가능
				2) 단, vectorizer.vocabulary_에 들어있지 않은 단어는 벡터화 불가
			vi. Normalizer
				1) 텍스트 정규화 가능
			vii. Point Wise Mutual Infomation(PMI)
				1) 이는 (words, context), (input, output)간의 상관관계를 측정하는 방법이다
				2) https://github.com/lovit/soynlp/blob/master/tutorials/pmi_usage.ipynb


	3. Khaiii
		a. 카카오에서 개발한 한국어 형태소 분석기
		b. 윈도우 지원안함 끝!


	- 비교
		○ 성능비교
	- 
	
