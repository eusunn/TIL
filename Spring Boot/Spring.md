# 1강
- 스프링은 프레임워크다.
    - 틀 안에서 동작을 한다.
- 스프링은 오픈소스다.
    - 소스코드 공개!
    - 내부 → 뜯어 고칠 수 있다.
- IoC(Inversion of Control) 컨테이너를 가진다.
    - 주도권을 스프링이 갖고 있다.
        - Class → 설계도
            - Class      abstract Class(추상 클래스)
                1. 스프링이란?
        - Object → 실체화가 가능한 것
        - Instance → 실체화 된 것
    - 오브젝트 (메소드)
        
        public void make() s
        
        의자 s = new 의자();
        
        heap 메모리 영역에 의자를 넣고 실체화 됐다. 
        
        그런데 
        
        public void user() s
        
        의자 s = new 의자();
        
         이건 위에 의자와 다른 의자이기 때문에 heap 메모리 영역에 새로운 의자가 또 실체화 된다. 
        
- DI(Dependency Injection)를 지원한다.
    - 의존성 주입
    - 싱글톤
    - 스캔을 하면 의자가 한 번 뜨는데 그 의자를 공유해서 필요한 곳에 사용할 수 있다.

# 2강
- 스프링은 많은 필터를 가지고 있다.
    - 필터 : 검열의 기능  (문지기)
    - 스프링 자체가 기본적으로 가지고 있는 필터를 사용할 수도 있고
    - 사용되지 않는 필터를 사용하겠다고 할 수 있고
    - 직접 필터를 생성해서 사용할 수도 있다.
        - 톰켓 → web.xml , 스프링 컨테이너 → 인터셉터 (AOP)
- 스프링은 많은 어노테이션을 가지고 있다. (리플렉션, 컨파일 체킹)
# 3강
- MessageConverter를 가지고 있다. 기본값은 현재 Json이다.
    - 중간언어 : xml → json
        
 한국말을                 ——  영어 →                        외계인말
        
 외계인말을                 ——  영어 →                        한국말
        
Json데이터는 영어의 역할을 해준다. ((번역기))
        
        Class Animal {
          int num = 10;
          String  name =  “사자”;  
        }
        
        json은 아래처럼 생겼다. 
        {”num” : 10, “name” : “사자”} 
        
         메세지컨버터는 자바 오브젝트를 json으로 번역해주는 번역기 역할을 한다. 

messageConverter : jackson (기본 설정)(json으로 바꿔주는 라이브러리)
 
자바 프로그램 ———request ————> 파이썬 프로그램 
        
자바 프로그램<———response ———— 파이썬 프로그램 
        
- BufferedReader와 BufferedWriter를 쉽게 사용할 수 있다.
1byte : 통신 단위 
데이터가 통신 할 때 8bit 씩 끊어 읽는다.
  
바이트는 문자가 아니라서 문자로 캐스팅(형변환) 해줘야한다. 
문자 (char) 이게 귀찮으니까 새로운 클래스
InputStreamReader 이걸로 감싸면 
바이트를 문자 하나뿐만 아니라 배열로도 받는다. 근데 크기가 정해져 있어서 채팅같이 얼마만큼 많은 데이터가 올지 모르는 기능같은 경우 정해진 크기 밖에 데이터를 받지 못한다.  그래서 사용하는게 

BufferedReader를 사용함 : 가변 길이의 문자를 받을 수 있다. 

데이터를 요청받아서 받을 때 BufferedReader로 받아야한다. 

jsp에서 request.getReader를 사용하면 됌 

데이터를 보낼때도 Bufferedwriter를 사용해야함 

자바에서는 Printwriter도 사용함 , print, println

BufferedReader는

바이트 스트림을 통해 데이터를 전송할 때 문자열로 가변 길이 데이터를 쓰게 해주는 클래스이다. 

@ResponseBody → BufferedWriter 가 존재

@RequestBody →  BufferedReader 가 존재
