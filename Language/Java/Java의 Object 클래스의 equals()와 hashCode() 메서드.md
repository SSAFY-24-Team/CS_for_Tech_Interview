![img_1.png](/img/Java의%20Object%20클래스의%20equals()와%20hashCode()%20메서드/img_1.png)
# Java의 Object 클래스의 equals()와 hashCode() 메서드
## Object 클래스란?
- Java의 최상위 클래스
- 모든 클래스는 이 Object클래스를 상속해서 만들어지며, 기본 메서드를 제공함

## equals 메서드란
- Object 클래스가 갖고있는 기본 메서드 중 하나
- 객체가 같은지 비교하는 기능 수행
- 기본적으로 객체 주소가 같은지 검사한다.
```java
class Person {
    String name;

    public Person(String name) {
        this.name = name;
    }

public class Example {
    public static void main(String[] args) {
        Person person1 = new Person("홍길동");
        Person person2 = new Person("홍길동");

        // == 은 객체타입인경우 주소값을 비교한다. 서로다른 객체는 다른 주소를 가지고 있기 때문에 false가 출력됨
        System.out.println(person1 == person2);
        // equals또한 객체타입인경우 주소값을 비교하기 때문에 false가 출력된다.
        System.out.println(person1.equals(person2));
    }
}
```

### equals() 오버라이딩
- 위의 Person 객체들은 각기 다른 힙 영역에 만들어져 주소 값이 다르므로 false가 나옴.
- 하지만 개발자의 의도는 name 속성이 같으므로 true 가 나와야 한다.
- 이때 equals() 메서드를 오버라이딩 해서 비교하고자 하는 필드를 선택한다.
```java
import java.util.Objects;

class Person {
    String name;

    public Person(String name) {
        this.name = name;
    }

    // 객체 주소 비교가 아닌 Person 객체의 사람 이름이 동등한지 비교로 재정의 하기 위해 오버라이딩
    public boolean equals(Object o) {
        if (this == o) return true; // 만일 현 객체 this와 매개변수 객체가 같을 경우 true
        if (!(o instanceof Person)) return false; // 만일 매개변수 객체가 Person 타입과 호환되지 않으면 false
        Person person = (Person) o; // 만일 매개변수 객체가 Person 타입과 호환된다면 다운캐스팅(down casting) 진행
        return Objects.equals(this.name, person.name); // this객체 이름과 매개변수 객체 이름이 같을경우 true, 다를 경우 false
    }
}

public class Main {
    public static void main(String[] args) {
        Person p1 = new Person("홍길동");
        Person p2 = new Person("홍길동"); // 동명이인

        System.out.println(p1.equals(p2)); // true
    }
}
```

## hashCode 메서드
- 객체의 주소 값을 해싱해서 해시 코드를 생성한다.
- 서로 같은 객체는 같은 해시 코드를 갖고 있다.
- 다른 객체는 해시 코드가 달라야 한다.
```java
class Person {
    String name;

    public Person(String name) {
        this.name = name;
    }
}

public class Main {
    public static void main(String[] args) {
        Person p1 = new Person("홍길동");
        Person p2 = new Person("홍길동");

        // 객체 인스턴스마다 각기 다른 주해시코드(주소))를 가지고 있다.
        System.out.println(p1.hashCode()); // 622488023
        System.out.println(p2.hashCode()); // 1933863327
    }
}
```

### hashCode 오버라이딩
![img.png](/img/Java의%20Object%20클래스의%20equals()와%20hashCode()%20메서드/img.png)
- equals() 메서드를 오버라이딩 하면 다음과 같은 오류 문구가 나타난다.
- equals() 메서드를 오버라이딩 하면, hashCode()메서드도 함꼐 오버라이딩 하라는 경고문이다.
- 자바의 권장사항인데, hash 값을 사용하는 HashMap이나 HashTable 자료구조에서 오류가 날 수 있기 때문이다.

### equals만 재정의할 경우
```java
class Person {
    public String name;

    public Person(String name) {
        this.name = name;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Person p = (Person) o;
        return Objects.equals(name, p.name);
    }
}

public class ClassTest {
    public static void main(String[] args) throws Exception {
        Person p1 = new Person("홍길동");
        Person p2 = new Person("홍길동");

        // 두 객체의 해시 코드
        System.out.println(p1.hashCode()); // 460141958
        System.out.println(p2.hashCode()); // 1163157884

        // 해시코드가 달라도, equals를 재정의 했기 때문에 동등함
        System.out.println(p1.equals(p2)); // true

        // 리스트를 생성하고 두 객체 데이터를 추가한다.
        List<Person> people = new ArrayList<>();
        people.add(p1);
        people.add(p2);
        
        // 그리고 리스트의 길이를 출력한다.
        System.out.println(people.size()); // 2
    }
}
```
```java
public static void main(String[] args) {
    Set<Car> cars = new HashSet<>();
    cars.add(new Car("foo"));
    cars.add(new Car("foo"));

    System.out.println(cars.size());
}
```
- 위 코드에서는 오류가 없었지만, 아래 코드 Set에서 같은 값을 가져도 다른 객체로 인식했다.
- 따라서 hashCode()메서드도 오버라이딩 해서 주소 기반이 아닌, 이름을 해싱하는 방식으로 처리해주어야 한다.

```java
class Person {
    public String name;

    public Person(String name) {
        this.name = name;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Person p = (Person) o;
        return Objects.equals(name, p.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name); // name 필드의 해시코드를 반환한다.
    }
}

public class ClassTest {
    public static void main(String[] args) throws Exception {
        Person p1 = new Person("홍길동");
        Person p2 = new Person("홍길동");

        // 두 객체의 해시 코드
        System.out.println(p1.hashCode()); // 54150093
        System.out.println(p2.hashCode()); // 54150093

        // 해시코드가 달라도, equals를 재정의 했기 때문에 동등함
        System.out.println(p1.equals(p2)); // true

        // SET를 생성하고 두 객체 데이터를 추가한다.
        Set<Person> people = new HashSet<>();
        people.add(p1);
        people.add(p2);

        // 그리고 SET의 길이를 출력한다.
        System.out.println(people.size()); // 1
    }
}
```

## 예제 질문
### Java Object 클래스의 equals()와 hashCode()는 무엇인가요?

<details>
   <summary> 예비 답안 보기 (👈 Click)</summary>
<br />

`equals()` 메서드는 객체의 동등성을 비교하며, 기본적으로 객체의 주소를 비교합니다. 이를 오버라이딩하여 객체의 필드를 비교할 수 있습니다.  
`hashCode()` 메서드는 객체의 해시 코드를 반환하며, 해시 기반의 자료 구조에서 객체를 빠르게 검색하거나 저장할 때 사용됩니다.  
두 메서드를 함께 오버라이딩해야 `HashMap`, `HashSet` 같은 컬렉션에서 객체 비교 시 의도한 결과를 얻을 수 있습니다.

</details>

### hashCode()를 오버라이딩해야 하는 이유는 무엇인가요?

<details>
   <summary> 예비 답안 보기 (👈 Click)</summary>
<br />

`hashCode()`를 오버라이딩하지 않고 `equals()`만 오버라이딩할 경우, 같은 값을 가지는 객체도 서로 다른 해시 코드를 가질 수 있습니다.  
이로 인해 `HashSet`, `HashMap` 등의 자료구조에서 중복된 객체를 다른 객체로 인식할 수 있습니다.  
따라서 `equals()` 메서드를 오버라이딩할 때는, `hashCode()`도 같이 오버라이딩하여 일관된 동작을 보장해야 합니다.

</details>



## 레퍼런스
- https://inpa.tistory.com/entry/JAVA-%E2%98%95-equals-hashCode-%EB%A9%94%EC%84%9C%EB%93%9C-%EA%B0%9C%EB%85%90-%ED%99%9C%EC%9A%A9-%ED%8C%8C%ED%97%A4%EC%B9%98%EA%B8%B0