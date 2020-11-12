# java_20days_ingeritance_interface_
상속 코딩 예제 / 인터페이스 문법 / 

문제 1) 

class X {
	
	public static int a;
	public static void modify(int a) {
		a++;
	}
}


public class Objc1 {

	public static void main(String[] args) {
		X.modify(X.a);   
		System.out.println(X.a); 

	}

}

문제 1-정답) 

class X {
	
	public static int a; //0 <속성변수>
	public static void modify(int a) { //<매개변수><지역변수>
		a++;// <- 여기에 1이 되겠지만. a는 지역변수다.. 매개변수.. 그래서 위에 속성변수 a에 1이 올라가지않는다 
	}
}


public class Objc1 {

	public static void main(String[] args) {
		X.modify(X.a);   //<-- 이게 속성변수 a 인지 메소드안 매개변수 a를 말하는건지 파악해야.
					     // static이 붙어있으니 객체생성 없이 클래스명.속성변수명으로 바로 호출가능.
		System.out.println(X.a); //a는 속성변수 0의 a다.

	}

}
// What is the result?
// 정답 = 0




문제 2)

class A{
	public byte getNumber() {return 1;}
}
class B extends A{
	public short getNumber() {return 2;} 
	
}
public class Objc2 {

	public static void main(String[] args) {
		
		B b = new B();
		System.out.println(b.getNumber());
	}

}



// 정답 7번줄에서 에러가 난다.
//메소드 이름 같은 메소드를 두개 선언했다. 오버라이딩 시도하고있는데


문제 3)

class Base{
	Base() { System.out.print("Base"); }
}
class Alpha extends Base{

}
public class Objc3 {

	public static void main(String[] args) {
		
		Alpha a = new Alpha();
		Base b = new Base();
	}

}




문제 3-정답)

class Base{
	Base() { System.out.print("Base"); }
}
class Alpha extends Base{
//	public Alpha() {
//		//super();
//	}

}
public class Objc3 {

	public static void main(String[] args) {
		
		Alpha a = new Alpha();
		Base b = new Base();
	}

}
// 생성자에대해 아느냐 모르느냐 묻는 문제
// 생성자를 생략해도 생성자가 있다. 
// 부모 생성자도 숨어있다.

// 정답 = BaseBase 



문제 4)


public class Objc4 {

		Objc4(){}

}
class BB extends Objc4{
BB(){}
}


/* 참인것은 무엇인가?  
1.	B's constructoris public  
2.	B's constructor has no arguments
3.	B's constructor include a call to this()
4.	B's constructor include a call to super()

 */
 
//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ 
// 디폴트 생성자가 생략되어있다는건 public B(){}
정답 2. 4

//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ




// 문제 5 )
// Which two allow the class Thing to be instantiated using new Thing()? (Choose two.)
//new Thing을 사용해서 객체화가 될 수있는 Thing 이라는 객체화를 허락하는건 뭐냐 

/*
 
 A. public class Thing{ }
 
 B. public class Thing{
 		public Thing(){}
 	}
 
 C. public class Thing{
 		public Thing(void){}
 	}
 
 D. public class Thing{
 		public Thing(String s){ }
 	}
 
 E. public class Thing{
 		public void Thing(){}
 		public Thing(String s){}
 	}
 
 new Thing() 라는 코딩으로 객체 생성이 가능한 클래스를 2개 골라라.
 

 //ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 Answer :  A,B
 c는 void 라는 키워드를 매개변수로 사용 불가능
 d는 이미 코딩으로 생성자를 선언하였으므로 디폴트 생성자가 없다.
 e는 생성자 앞에 리턴형이 올 수 없다.
 
 c, e 에러 객체화도 안된다. 
 
//ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ


문제 6)
 
 public class Test{ }
 
 What is the prototype of the default constructor?
 
 A. Test()
 B. Test(void)
 C. public Test()
 D. public Test(void)
 E. public void Test()
 
 
 //ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 Answer : C
 	코딩된 생성자가 0개면 [public] 생성자명(){} 을 넣어준다.
 
 디폴트 새성자 : [public] 생성자명() {}
 
 //ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 
 
 문제 7 ) 디폴트 생성자가 들어가는 걸 골라라.
 
 In which two cases does the compiler supply a default constructor for class A?
 (choose two.)
 
 A. class A{
 }
 B. class A{
 public A()
 }
 C. class A{
 public A(int x){}
 }
 D. class A { }
    class A extends Z{
        void A(){}
 }
 //ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

(정답 AD)
D 의 경우 A 클래스가 2개 선언된 경우 나중에 선언된 클래스 A는 
선언되지 못하고 에러가 발생하지만 처음 선언된 A 클래스는 정상적으로
선언되므로 디폴트 생성자도 서비스 받아 삽입된다.
 //ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 문제 8 )
 
 
 B. class A {
 }
 class B extends A{
 	B(){}
 }
 
 C. class A {
 A(){}
 }
 class B extends A{
 public B(){}
 }
 
 D. class Z{
 public Z (int v){}
 }
 class A extends Z{
 }

 //ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

Answer : D

 @@@@자식에는 디폴트 생성자가 있는데 부모쪽에 생성자가 없어서 에러가 터진다@@@@ 
 
	=> D의 A 클래스 안에는 A(){super();} 가 있는 것과 같다.
	super() 는 부모 생성자 중에 매개변수가 없는 부모 생성자를 호출하란 얘기인데
	현재 부모 생성자 중에 매개변수가 없는 생성자는 없다.
 
  //ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

 
 문제 9)
 
 class A{
 public int get Number (int a){
 return a+1;
 }
 
 class B extends A{
 public int get Number (int a){
 return a+2;
 }
 class BExe{
 
 	puvlic static void main(String args[]){
 	A a = new B();
 	System.out.println(a.getNumber(0));
 	}
 }
 
 what is the result ?
 A. 1
 B. 2
 C. 컴파일 에러 lines 8
 D. 컴파일 에러 lines 13
 E. 컴파일 에러 lines 14
 
 
 //ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ

 
 정답 B
 
 객참변수의 자료형을 부모걸 썼으니 (오버라이딩 개념을 알아야 풀 수 있다.)
 고유멤버 가 아니라 오버라이딩은 고유멤버에 속하지 않으니 호출 가능하다.
 
 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 문제 10)
 
  class A{
 public int get Number(int a){
 return a+1;
 }
 
 class B extends A{
 public int get Number (int a, char c){
 return a+2;
 }
 class BExe{
 
 	puvlic static void main(String args[]){
 	B b = new B();
 	System.out.println(b.getNumber(0));
 	}
 }
 
 what is the result ?
 A. 1
 B. 2
 C. 컴파일 에러 lines 8
 D. 컴파일 에러 lines 14
 
 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 
 
 정답 1 A
 자식께 없으면 부모걸로 올라가서 있는지 확인하고 호출한다.
 
 
 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 
 문제 11 )
 
 class A{
	public static int a(int x) {return 1;}
} 
 
 class B extends A {
 	public static int a(int x){ return 2;}
 	}
 	public class AExe {
 		public static void main(String args[]){
 		A x = new B();
 		System.out.print(x.a(1));
 	}
 }
 정답 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 
static 묻는 문제(static 붙으면 독단저긍로 쓰는것. static은 자식클래스에서 오버라이딩 금지한다 -> 고유멤버다.) 
 객참변수 부모걸 쓰면 무슨 의미냐. 
 
 static 이 붙어 객체 생성 없이 독단적으로 호출되는 메소드는 자식 클래스에서 오버라이딩을 금지한다.
 독단적으로 호출되는 이질적인 메소드를 자식이 갖다 쓰는 걸 금지한다.
 B 클래스의 a 메소드는 형식적으로 오버라이딩 시도를 가지고 있으나 서로 static 이 붙어오버라이딩 금지 성격을 가지므로
 독단적인 메소드로 보는 것이다
 그러므로 B클래스의 a메소드는 고유메소드로 보아 호출하지 않고 부모의 클래스의 a 메소드를 호출하는것이다
 만약 public static int a(int x) {return 2;} 에서 static을 빼면 
 static 이 붙은 메소드를 오버라이딩 한것으로 보아 에러가 난다.
  정답 : 1
 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 
 
  문제12)
 
 public class ConstOver {
 	public ConstOver(int x, int y, int z) { }
 	}
 	
 	
 	which two overload the ConstOver constructor? (Choose two.)
 	A. ConstOver(){}
 	B. protected int ConstOver(){}
 	C. private ConstOver(int z, int y, byte x) {}
 	D. public Object ConstOver(int x, int u, int z){}
 	E. public void ConstOver(byte x, byte y, byte z){}
  
 정답ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ 

  오버로드 규칙
  1. 생성자이름 같아야 
  
  2. 매개변수 갯수 다르거나 
  3. 매개변수 갯수 똑같으면 자료형이 달라야.******중요******
  4. 매개변수 자료형 순서 달라야한다.
  5. 리턴(return)형은 상관없다. 
 

 생성자는 자료형이 나오면 안된다.
  (정답 = a, c )

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ 
문제 13) 
 
public class MethodOver{
public void setVar(int a, int b, float c) {}
}

Which  two overload the setVar Method?(choose two.)

A. private void setVar(int a, float c, int b) {}
B. protected void setVar(int a, int b, float c) {}
C. public int setVar(int a, float c, int b) {return a;}
D. public int setVar(int a, int b, float c) {return a;}
E. protected float setVar(int a, int b, float c) {return c;}

 정답ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 
 (정답  a c)
 //B  매개변수 갯수 같아서 안된다  
 //A  매개변수 자료형의 순서가 달라서 오버로드 된다.
 //C  매개변수 자료형 순서 달라서 오버로드 된다. (리턴형은 관계 없다.상관없다)
 //D  매개변수 갯수 같아서 안된다. 자료형도 같다. ( 리턴형 관계 없다
 //E  메서드 자료형이 달라서 안된다. 
 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 문제14)
 
 class BaseClass {
 private float x = 1.0f;
 protected float getVar() { return x;}
 }
 
 class SubClass extends BaseClass {
 private float x = 2.0f;
 //line 7
 }
 
 which two are valid examples of method overridng when inserted at line 7?
 (Choose two.)
 
A. float getVar() { return x;}
B. public float getVar() { return x; }
C. public double getVar() {return x;}
D. protected float getVar() {return x;}
E. public float getVar(float f) { return f;}

 정답ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
(정답 b, d)
접근지정자는 부모보다 같거나 커야한다.

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
문제 15 
 
class A {
	protected int method1 (int a, int b) { return 0; }
	}
	class B extends A{
	?????
	}
 
 물음표 자리에 들어가서 에러 없이 실행 가능한 것 2개 고르라. 
 A. public int method1 (int a, int b) {return 0;}
 B. private int method1 (int a, int b) {return 0;}
 C. private int method1 (int a, long b) {return 0;}
 D. public short method1 (int a, int b) {return 0;}
 E. static protected int method1 (int a, int b) {return 0;}
 
  정답ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 (ac) // 오버라이딩 규칙 물어보는 ac
 정답 (ac)
 B -> 오버라이딩 시도시 접근 지정자가 public 또는 protected 여야 하니까 에러. 
 d -> 오버라이딩 시도시 리턴형이 다르므로 에러
 e -> static 과 protected 위치가 바뀜. 
 c -> 오버라이딩 시도가 아니라 고유메소드이므로 에러 없음
 	  메소드 명 같고 매개변수가 다를 경우 오버로딩 시도로 보지 않고 고유 메소드로 보기 때문.
 
ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
문제 16) 
 
 
 
 class A {
 	int var = 3;
 	int printNumber(int num) {
 		return num+1;
 	}
 }
 class B extends A {
 	int var = 5;
 	int printNumber(int num) {
 		return num+2;
 	}
 }
 public class Test{
 	public static void main(String args[]) {
 		A a = new B(); // 객참멤버를 자기게 아니라 부모걸로 쓰면 고유멤버 호출 안된다. Var찾으로 부모걸로 간거다.
 		System.out.println( a.Var + "," + a.printNumber(0) );
 	}
 }
 a) compile 에러 b) "3,1" c) "3,2" d) "5,1" e) "5,2"
 
 정답 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 	(a.Var 가 B클래스 를 가리키는 걸까 A클래스를 가리키는 걸까)
 	
 
오버라이딩 (메소드) - 변수는 상관없다. 메소드명+매개변수 같으면 오버라이딩.
오버로드(메소드,속성변수)
a.Var => 고유멤버기 때문에 자식에서 호출안되고 부모로 올라간다
a.printNumber => 오버라이딩 됬기 때문에 자식의 printNumber()는  고유멤버가 아니라 호출된다.
객참멤버를 자기게 아니라 부모걸로 쓰면 고유멤버 호출 안된다. Var찾으로 부모걸로 간거다.

정답 : c

ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
번외문제)
메인 메서드의 
 A a = new B(); 를 B a = new B(); 로 고치면??
 
  정답 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 자식꺼에서만 호출하기 때문에 "5,2"가 정답.
 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 
 문제 17
 
 자식클래스의 생성자 안에 첫줄에는 super() 가 나와야 한다.
 
 super() 가 에러나면.. 부모쪽을 
 
class A {
	public A(){
		System.out.println("hello from a");
	}
}
class B extends A {
	public B(){
		System.out.println("hello from b");
		super();
	}
} 
public class Test {
 	public static void main(String args[]) {
 		A a = new B ();
 		}
 	}
  
  정답 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
// 정답 : 컴파일 에러
 	 
 super();가 첫째줄 이라면? 정답은 
 hello from a"
 hello from b"
 
 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 문제 18 ) 
class A {
	public final int method1 (int a, int b) {return 0;}
	}
class B extends A {
	Public int method1 (int a, int b) {return 1;}
	}
public class Test{
	public static void main(String args[]){
		B b = new B ();
		System.out.println( b.method1(0,1));
		}
	}
		
  정답 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ		

final이 붙은 메소드는 오버라이딩 안된다. *메소드 앞 final은 오버라이딩 금지 
정답 
compile 에러 .

 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 문제 19 ) 
class A {
	public String toString() {
			return "4";
			}
		}
	class B extends A {
		public String toString() + "3";
		}
	}
public class Text {
	public static void main(String[] args) {
		System.out.println(new B().toString());
		}
	}
	
  정답 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ		
	정답: 43
 
 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 문제20 ) 

Class A {
	public int getVal() { retunr 5; }
}
class B extends A [
 	public int getVal() { return 10; }
 }
 public class Text {
 	public static void main(String args[]){
 		B b= new B();
 		A a = (A)b;
 		int x = a.getval();
 		System.out.prinln(x);
 	}
 }
 정답 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ	
 
 정답 10
 
 		A a = (A)b; <--- 타입캐스팅 타입 연산자로 A 부모클래스로 자료형을 바꿨다.
 		객체 형 변환.

 ㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡㅡ
 
