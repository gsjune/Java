# Java

제1장 프로그램의 작성 방법

‘위에서 아래로’가 아니라 ‘밖에서 안으로’ 작성

변수의 초기화 = 변수 선언 + 대입


제2장 식과 연산자(Math.max, Integer.parseInt, Random, Scanner)

형 변환(cast)

int m = Math.max(a, b);
int n = Math.min(a, b);

String age = “31”;
int n = Integer.parseInt(age);

int random = new java.util.Random().nextInt(90);

String name = new java.util.Scanner(System.in).nextLine();
int age = new java.util.Scanner(System.in).nextInt();

Scanner scanner = new Scanner(System.in);
String name = scanner.next();
int age = scanner.netInt();

제3장 조건분기와 반복

boolean clear = true;
if (clear == true) {
} else {
}

if (s.equals(“저녁”)) {
}

if (!(age >= 20)) {
}

int fortune = new java.util.Random().nextInt(3) + 1;
switch (fortune) {
    case 1:
        System.out.println(“very good”);
        break;
    case 2:
        System.out.println(“good”);
        break;
    default:
        System.out.println(“not bad”);
        break;

제4장 배열

int[] score = new int[5];
int count = score.length;

int[] score = {20, 30, 40, 50, 80}
for (int i = 0; i < score.length; i++) {
    System.out.println(score[i])
}
for (int value : score) {
    System.out.println(value);
}

String s = “Java로 개발”;
System.out.println(s.length());

int[][] scores = new int[2][3]; // 2행 3열
scores[0][0] = 40;
scores[0][1] = 50;
scores[0][2] = 60;
scores[1][0] = 80;
scores[1][1] = 60;
scores[1][2] = 70;

## 메소드(리턴, 오버로드)
- 호출과 정의, 호출1과 정의1/호출2와 정의2
- create method cf. import static method...
- 호출 hello(name: "June", age: 43)
- 정의 hello(String name, int age)
- 메소드 return answer;
- 오버로드(인수의 타입/수가 다른 경우)

제6장 복수 클래스를 사용한 개발(API, printf)

int plus = CalcLogic.add(a, b);
int plus = sample.sample6.logic.CalcLogic.add(a, b);

API

int[] heights = {172, 149, 152, 191, 155};
Arrays.sort(heights); // 오름차순 정렬
for (int h : heights) {
    System.out.println(h);
}

출력 포맷 printf

제8장 인스턴스와 클래스

정의한 클래스로 메인에서 인스턴스를 생성할 수 있다.
Hero 클래스를 정의하면 Hero 타입의 변수 이용 가능
Hero hero = new Hero();

hero.name = “june”;
hero.hp = 100;
System.out.println(“용사 ” + hero.name + “을 생성했습니다!”)

hero.sit(5);
hero.slip();
hero.sit(25);
hero.run();

new 연산자를 사용하여 클래스로부터 인스턴스를 생성(인스턴스화)하여 클래스 타입 변수에 인스턴스가 담겨 있을 때, ‘변수명.필드명’이나 ‘변수명.메소드명()’으로 인스턴스의 필드나 메소드를 이용할 수 있다.

제9장 클래스

필드의 초깃값을 자동 설정하도록 클래스창에서 생성자(constructor) 작성
메인창에서 new 할 때 인수를 넘겨줌
System.out.println(hero.name);
System.out.println(hero.hp);

Hero() { // 기본 생성자
    this.hp = 100;
    this.name = “june”;
}

Hero(String name) { // 생성자 오버로드
    this.hp = 100;
    this.name = name;
}

Hero() { // 생성자에서 다른 생성자를 호출
    this(“김영웅”);
    this.Hero(“김영웅”); // 에러
}

제10장 캡슐화(getter/setter, IllegalArgumentException)

getter와 setter
모든 필드 private
메소드를 통해 접근하도록 클래스를 설계

Hero 클래스에 getName 메소드를 추가
public class Hero {
    private String name;
    
    public String getName() {
        return name;
    }
}

King 클래스의 talk() 메소드를 수정
public class King {
    void talk(Hero hero) {
        System.out.println(“용사 ” + hero.getName() + “이여”);
    }
}

캡슐화 전
public class Hero {
    String name;
}







캡슐화 후
public class Hero {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

setter 메소드 안에서 값의 타당성 검사
String name;

public void setName(String name) {
    if (name == null) {
        throw new IllegalArgumentException(“이름은 null 아니어야”);
    }
    if (name.length() <= 1) {
        throw new IllegalArgumentException(“이름이 너무 짧음”);
    }
    if (name.length() >= 8) {
        throw new IllegalArgumentException(“이름이 너무 긺”);
    }
    this.name = name;
}

setName이 바르게 기능하는지 확인
public class Main {
    public static void main(String[] args) {
        Hero hero = new Hero();
        hero.setName(“”);
    }
}

제11장 상속(오버라이드)

public class SuperHero extends Hero {
    private boolean flying; // 추가한 필드

    // 추가한 메소드
    public void fly() {
        flying = true;
        System.out.println(“날았다!”);
    }
    public void land() {
        flying = false;
        System.out.println(“착지했다!);
    }
}

public class Main {
    public static void main(String[] args) {
        SuperHero superHero = new SuperHero();
        superHero.run();
    }
}

override

public class SuperHero extends Hero {
    private boolean flying;

    public void fly() {
        flying = true;
        System.out.println(“날았다!”);
    }
    public void land() {
        flying = false;
        System.out.println(“착지했다!);
    }

    @Override
    public void run() {
        System.out.println(“퇴각했다”);
    }
}

제12장 추상클래스와 인터페이스(오버라이드 강제)

추상 메소드를 가지려면 반드시 추상클래스여야 한다.

public abstract class Character {
    String name;
    int hp;
    public void run() {
        System.out.println(name + “은 도망쳤다”);
    }
    
    public abstract void attack(Kinoko kinoko);
}

오버라이드 강제
public class Dancer extends Character { // 빨간 줄

    public void dance() {
        System.out.println(this.name + “은 ...”);
    }
}

인터페이스에 선언된 메소드는 자동적으로 public abstract가 되고, 필드는 public static final이 된다.

제13장 다형성(오버라이드, instanceof)

선언을 대충 상위개념으로 하고, new는 하위개념으로 한다.

Character character1 = new Character();
Character character2 = new SuperHero();

public abstract class Monster {
    public void run() {
        System.out.println(“몬스터는 도망쳤다”);
    }
}

public class Slime extends Monster {
    @Override
    public void run() {
        System.out.println(“슬라임은 슬금슬금 도망쳤다”);
    }
}

public class Main {
    public static void main(String[] args) {
        Slime slime = new Slime();
        Monster monster = new Slime();
        slime.run();
        monster.run();
    }
}







public class Main {
    public static void main(String[] args) {
        Character character = new Wizard();

        if (character instanceof Hero) {
            Hero hero = (Hero) character;
        } else {
            System.out.println(“형변환 불가”);
        }
    }
}

다형성의 메리트를 활용(코드의 중복 제거)
public class Main {
    public static void main(String[] args) {
        Character[] characters = new Character[5];
        characters[0] = new Hero();
        characters[1] = new Hero();
        characters[2] = new Thief();
        characters[3] = new Wizard();
        characters[4] = new Wizard();

        for (Character character : characters) {
            character.setHp(character.getHp() + 50);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        // 타입은 Monster로 퉁 치기
        Monster[] monsters = new Monster[3];
        monsters[0] = new Slime();
        monsters[1] = new Goblin();
        monsters[2] = new DeathBat();
        
        // 동작은 안에 담긴 객체를 따름
        for (Monster monster : monsters) {
            monster.run();
        }
    }
}

# 매일
연습문제
제15, 16장
녹화강좌
plus
