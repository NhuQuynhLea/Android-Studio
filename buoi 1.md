# Buổi 1

## I. Syntax cơ bản

### _1. Nhập xuất_

**Xuất dữ liệu**

Xuất dữ liệu ra màn hình có 3 loại:

- **System.out.println(“ ”);**

> Ý nghĩa: Xuất kết quả ra màn hình đồng thời con trỏ chuột nhảy xuống dòng tiếp theo.

- System.out.print(“ ”);

> Ý nghĩa: Xuất kết quả ra màn hình nhưng con trỏ chuột không xuống dòng.

- System.out.printf(“ ”);

> Ý nghĩa: Xuất ra màn hình kết quả đồng thời có thể định dạng được kết quả đó nhờ vào các đối số thích hợp.

> Vd: ![](https://caodang.fpt.edu.vn/wp-content/uploads/3.jpg-1.png)

**Nhập dữ liệu**

- Để nhập dữ liệu từ bàn phím trong Java, chúng ta sử dụng lớp Scanner
- Lớp Scanner, là một lớp nằm trong gói java.util, được sử dụng để đọc dữ liệu đầu vào từ các nguồn khác nhau như luồng đầu vào, người dùng, tệp.
- Đầu tiên phải import thử viện vào: import java.util.Scanner;
- Sau đó ta gọi và khởi tạo đối tượng từ lớp Scanner:

```
Scanner sc = new Scanner(System.in);
```

- Khai báo 1 biến để lưu giá trị cho người dùng nhập vào:
  > vd: String name = sc.nextLine():

Trong việc sử dụng đối tượng từ lớp Scanner có rất nhiều cách để lấy kiểu dữ liệu thì tùy theo giá trị nhập vào từ người dùng. Chúng ta sử dụng dấu chấm (.) để lựa chọn.

> - next(): Nhận vào một String token (nhận vào 1 từ đầu tiên thay cả câu)
> - nextInt(): Nhận vào một số int
> - nextLong(): Nhận vào một số long
> - nextFloat(): Nhận vào một số float
> - nextDouble(): Nhận vào một số double
> - sc.nextLine(): Nhận vào một chuỗi String (Cả 1 câu)
> - nextByte(): Nhận vào một byte
> - nextBoolean(): Nhận vào một boolean

### _2. Biến trong Java_

![](https://viettuts.vn/images/java/cac-kieu-bien-trong-java.png)

Ví dụ về khai báo biến trong java:

```java
package vn.viettuts.bienvadulieu;

public class Bien {
    public static float PI = 3.14f;   // Đây là biến static
    int n;                            // Đây là biến instance

    public Bien () {
        char c = 'c';                 // Đây là biến local
    }
}
```

**Biến local**

- Biến local được khai báo trong các phương thức, hàm contructor hoặc trong các block.
- Biến local được tạo bên trong các phương thức, contructor, block và sẽ bị phá hủy khi kết thúc các phương thức, contructor và block.
- Không được sử dụng "access modifier" khi khai báo biến local.
- Bạn cần khởi tạo giá trị mặc định cho biến local trước khi có thể sử dụng.

```java
package vn.viettuts.bienvadulieu;

public class Bien {

    public void sayHello() {
        int n = 10;                     // Đây là biến local
        System.out.println("Gia tri cua n la: " + n);
    }

    public static void main(String[] args) {
        Bien bienLocal = new Bien();
        bienLocal.sayHello();
    }
}
```

**Biến instance**

- Biến instance được khai báo trong một lớp(class), bên ngoài các phương thức, constructor và các block.
- Biến instance được tạo khi một đối tượng được tạo bằng việc sử dụng từ khóa “new” và sẽ bị phá hủy khi đối tượng bị phá hủy.
- Biến instance có thể được sử dụng bởi các phương thức, constructor, block, ... Nhưng nó phải được sử dụng thông qua một đối tượng cụ thể.
- Bạn được phép sử dụng "access modifier" khi khai báo biến instance, mặc định là "default".
- Biến instance có giá trị mặc định phụ thuộc vào kiểu dữ liệu của nó. Ví dụ nếu là kiểu int, short, byte thì giá trị mặc định là 0, kiểu double thì là 0.0d, ... Vì vậy, bạn sẽ không cần khởi tạo giá trị cho biến instance trước khi sử dụng.
- Bên trong class mà bạn khai báo biến instance, bạn có thể gọi nó trực tiếp bằng tên khi sử dụng ở khắp nới bên trong class đó.

```java
package vn.viettuts.bienvadulieu;

public class Sinhvien {
    // biến instance "ten" kiểu String, có giá trị mặc định là null
    public String ten;

    // biến instance "tuoi" kiểu Integer, có giá trị mặc định là 0
    private int tuoi;

    // sử dụng biến ten trong một constructor
    public Sinhvien(String ten) {
        this.ten = ten;
    }

    // sử dụng biến tuoi trong phương thức setTuoi
    public void setTuoi(int tuoi) {
        this.tuoi = tuoi;
    }

    public void showStudent() {
        System.out.println("Ten  : " + ten);
        System.out.println("Tuoi : " + tuoi);
    }

    public static void main(String args[]) {
        Sinhvien sv = new Sinhvien("Nguyen Van A");
        sv.setTuoi(21);
        sv.showStudent();
    }
}
```

**Biến static**

- Biến static được khai báo trong một class với từ khóa "static", phía bên ngoài các phương thức, constructor và block.
- Biến static được tạo khi chương trình bắt đầu chạy và chỉ bị phá hủy khi chương trình dừng.
- Giá trị mặc định của biến static phụ thuộc vào kiểu dữ liệu bạn khai báo tương tự biến instance.
- Biến static được truy cập thông qua tên của class chứa nó, với cú pháp: <span style = "color:yellow">TenClass.tenBien</span>.
- Trong class, các phương thức sử dụng biến static bằng cách gọi tên của nó khi phương thức đó cũng được khai báo với từ khóa "static".

### _3. Toán tử trong Java_

- toán tử số học: +,-,\*,/,..
- toán tử quan hệ: ==, !=, >, <,...
- toán tử logic: &&, ||, !, ^
- toán tử điều kiện :
  > <biểu thức 1> ? <biểu thức 2> : <biểu thức 3>;
- toán tử gán

### _4.Arays_

- Mảng trong java lưu các phần tử theo chỉ số, chỉ số của phần tử đầu tiên là 0.

- Có hai kiểu mảng trong java:

  - Mảng một chiều
  - Mảng đa chiều

- Để khai báo một mảng, khai báo loại biến với dấu ngoặc vuông []:

  > dataType[] arr;
  >
  > dataType []arr;
  >
  > dataType arr[];

- Khởi tạo:

```Java
 // tạo một mảng có độ dài 4, thêm các phần tử sau tạo
String[] cars1 = new String[4];

// tạo một mảng không cần chỉ định số phần tử cụ thể
String[] cars2 = new String[] { "Honda", "BMW", "Ford", "Mazda" };

// tạo một mảng không cần chỉ định số phần tử cụ thể
// và không cần dùng từ khóa new
String[] cars3 = { "Honda", "BMW", "Ford", "Mazda" };
```

- Độ dài mảng trong Java:
  để biết có bao nhiêu phần tử một mảng, sử dụng thuộc tính length : VD car.length
- Sắp xếp mảng: phương thức Sort() có sẵn

```java
package vn.viettuts.array;

import java.util.Arrays;

public class DuyetArray2 {
    public static void main(String[] args) {
        String[] cars = { "Honda", "BMW", "Ford", "Mazda" };
        // sap xep mangr cars theo thu tu tang dan
        Arrays.sort(cars);
        System.out.println("Mảng cars sau khi được sắp xếp:");
        for (String car : cars) {
            System.out.println(car);
        }
    }
}
```

- Mảng đa chiều:
  > dataType[][] arr;
  >
  > dataType [][]arr;
  >
  > dataType arr[][];
  >
  > dataType []arr[];

### _5.Wrapper class_

Lớp Wrapper trong java cung cấp cơ chế để chuyển đổi kiểu dữ liệu nguyên thủy thành kiểu đối tượng và từ đối tượng thành kiểu dữ liệu nguyên thủy.

Ví dụ chuyển kiểu dữ liệu nguyên thủy thành kiểu Wrapper

```java
public class WrapperExample1 {
    public static void main(String args[]) {
        // Đổi int thành Integer
        int a = 20;
        Integer i = Integer.valueOf(a);// đổi int thành Integer
        Integer j = a;// autoboxing, tự động đổi int thành Integer trong nội bộ trình biên dịch

        System.out.println(a + " " + i + " " + j);
    }
}
```

Ví dụ chuyển kiểu Wrapper thành kiểu dữ liểu nguyên thủy

```java
public class WrapperExample2 {
    public static void main(String args[]) {
        // đổi Integer thành int
        Integer a = new Integer(3);
        int i = a.intValue();// đổi Integer thành int
        int j = a;// unboxing, tự động đổi Integer thành int trong nội bộ trình biên dịch

        System.out.println(a + " " + i + " " + j);
    }
}
```

### _6.String class_

Lớp java.lang.String được sử dụng để tạo đối tượng string.

Có 2 cách để tạo đối tượng String:

- String literal:

<span style = "color:yellow">String s = “GeeksforGeeks”;</span>

- Using new keyword

<span style = "color:yellow">String s = new String (“GeeksforGeeks”);</span>

**Các phương thức của lớp String trong java**

_1. int length(): Returns the number of characters in the String_

> "GeeksforGeeks".length(); // returns 13

_2. Char charAt(int i): Returns the character at ith index_

> "GeeksforGeeks".charAt(3); // returns ‘k’

_3.String substring (int i): Return the substring from the ith index character to end_

> "GeeksforGeeks".substring(3); // returns “ksforGeeks”

_4.String substring (int i, int j): Returns the substring from i to j-1 index_

_5.String concat( String str): Concatenates specified string to the end of this string_

> String s1 = ”Geeks”;
>
> String s2 = ”forGeeks”;
>
> String output = s1.concat(s2); // returns “GeeksforGeeks”

_6.int indexOf (String s): Returns the index within the string of the first occurrence of the specified string_

> String s = ”Learn Share Learn”;
>
> int output = s.indexOf(“Share”); // returns 6

_7.boolean equals( Object otherObj): Compares this string to the specified object_

> Boolean out = “Geeks”.equals(“Geeks”); // returns true
>
> Boolean out = “Geeks”.equals(“geeks”); // returns false

_8.boolean equalsIgnoreCase (String anotherString): Compares string to another string, ignoring case considerations._

_9.int compareTo( String anotherString): Compares two string lexicographically_

_10.String toLowerCase(): Converts all the characters in the String to lower case_

_11.String toUpperCase(): Converts all the characters in the String to upper case_

_12.String trim(): Returns the copy of the String, by removing whitespaces at both ends. It does not affect whitespaces in the middle_

> String word1 = “ Learn Share Learn “;
>
> String word2 = word1.trim(); // returns “Learn Share Learn”

_13. String replace (char oldChar, char newChar): Returns new string by replacing all occurrences of oldChar with newChar._

> String s1 = “feeksforfeeks“;
>
> String s2 = “feeksforfeeks”.replace(‘f’ ,’g’); // returns “geeksgorgeeks”

### _7.Math class_

Lớp Math cung cấp các hàm về toán học. Bạn không cần phải tạo đối tượng lớp Math vì các hàm trong lớp đó là static, để gọi hàm chỉ đơn giản viết tên lớp Math và tên phương thức cần gọi.

Trước khi gọi các hàm Math, bạn có thể import package để khỏi phải viết đầy đủ tên pack, như
<span style= "color:yellow"> import java.lang.Math;</span>

- Math.PI hằng số PI
- Math.abs()
- Math.ceil() trả về giá trị double là số làm tròn tăng bằng giá trị số nguyên gần nhất
- Math.floor() trả về double là số làm tròn giảm
- Math.max() lấy số lớn trong hai số
- Math.min lấy số nhỏ
- Math.pow
- Math.sqrt()
- Math.random(),...

## II. Regex

> Java Regex hoặc Regular Expression (biểu thức chính quy) là một API để định nghĩa một mẫu để tìm kiếm hoặc thao tác với chuỗi. Nó được sử dụng rộng rãi để xác định ràng buộc trên các chuỗi như xác thực mật khẩu, email, kiểu dữ liệu datetime, ...

_Lớp Matcher_

Nó implements interface MatchResult, cung cấp bộ máy xử lý biểu thức chính quy để thao tác với chuỗi ký tự
|Phương thức|Mô tả|
|-----------|------|
|boolean matches()|kiểm tra xem biểu thức chính quy có khớp với mẫu hay không.|
|boolean find()|tìm biểu thức tiếp theo khớp với mẫu.|
|boolean find(int start)|tìm biểu thức tiếp theo khớp với mẫu từ số bắt đầu đã cho.|
|String group()|trả về chuỗi con phù hợp.|
|int start()|trả về vị trí bắt đầu của chuỗi con phù hợp.|
| int end()|
trả về vị trí kết thúc của chuỗi con phù hợp.|
|int groupCount()|trả về tổng số các chuỗi con phù hợp.|

_Lớp Pattern_

Đây là phiên bản được biên dịch của một biểu thức chính quy. Nó được sử dụng để xác định một mẫu cho bộ máy regex.

| Phương thức                                              | Mô tả                                                                                            |
| -------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| static Pattern compile(String regex)                     | biên dịch regex đã cho và trả về thể hiện của Pattern.                                           |
| Matcher matcher(CharSequence input)                      | tạo một matcher khớp với đầu vào đã cho với mẫu.                                                 |
| static boolean matches(String regex, CharSequence input) | Nó biên dịch biểu thức chính quy và tìm kiếm các chuỗi con từ chuỗi input phù hợp với mẫu regex. |
| String[] split(CharSequence input)                       | chia chuỗi input đã cho thành mảng các kết quả trùng khớp với mẫu đã cho.                        |
| String pattern()                                         | trả về mẫu regex.                                                                                |

**Cú pháp Regex trong Java**

1.Các lớp ký tự Regex

| Regex         | Mô tả                                   |
| ------------- | --------------------------------------- |
| [...]         | trả về một ký tự phù hợp                |
| [abc]         | a, b, hoặc c                            |
| [^abc]        | Bất kỳ ký tự nào ngoại trừ a, b, hoặc c |
| [a-zA-Z]      | a tới z hoặc A tới Z                    |
| [a-d[m-p]]    | a tới d, hoặc m tới p: [a-dm-p]         |
| [a-z&&[def]]  | d, e, hoặc f                            |
| [a-z&&[^bc]]  | a tới z, ngoại trừ b và c: [ad-z]       |
| [a-z&&[^m-p]] | a tới z, ngoại trừ m tới p: [a-lq-z]    |
| [0-9]         | 0 tới 9                                 |

2. Số lượng ký tự trong Regex

| Regex  | Mô tả                                      |
| ------ | ------------------------------------------ |
| X?     | X xảy ra một hoặc không lần                |
| X+     | X xảy ra một hoặc nhiều lần                |
| X\*    | X xảy ra không hoặc nhiều lần              |
| X{n}   | X chỉ xảy ra n lần                         |
| X{n,}  | X xảy ra n hoặc nhiều lần                  |
| X{y,z} | X xảy ra ít nhất y lần nhưng nhỏ hơn z lần |

3. Ký tự đặc biệt trong Regex

| Regex | Mô tả                                                                                                                |
| ----- | -------------------------------------------------------------------------------------------------------------------- |
| .     | Bất kỳ ký tự nào                                                                                                     |
| ^     | Có 2 cách sử dụng: Đánh dấu bắt đầu của một dòng, một chuỗi.Nếu sử dụng trong dấu [...] thì nó có nghĩa là phủ định. |
| $     | Đánh dấu Kết thúc của một dòng                                                                                       |
| \d    | Bất kỳ chữ số nào, viết tắt của [0-9]                                                                                |
| \D    | Bất kỳ ký tự nào không phải chữ số, viết tắt của [^0-9]                                                              |
| \s    | Bất kỳ ký tự trống nào (như dấu cách, tab, xuống dòng, ...), viết tắt của [\t\n\x0B\f\r]                             |
| \S    | Bất kỳ ký tự trống nào không phải ký tự trống, viết tắt của [^\s]                                                    |
| \w    | Bất kỳ ký tự chữ nào (chữ cái và chữ số), viết tắt của [a-zA-Z_0-9]                                                  |
| \W    | Bất kỳ ký tự nào không phải chữ cái và chữ số, viết tắt của [^\w]                                                    |
| \b    | Ranh giới của một từ                                                                                                 |
| \B    | Không phải ranh giới của một từ                                                                                      |

## III. Class & Object

**Encapsulation**

- Tính đóng gói trong java là kỹ thuật ẩn giấu thông tin không liên quan và hiện thị ra thông liên quan. Mục đích chính của đóng gói trong java là giảm thiểu mức độ phức tạp phát triển phần mềm.

- Đóng gói cũng được sử dụng để bảo vệ trạng thái bên trong của một đối tượng. Việc chỉnh sửa đối tượng được thực hiện, xác nhận thông qua các phương thức.

**Inheritance**

> Kế thừa trong java là sự liên quan giữa hai class với nhau, trong đó có class cha (superclass) và class con (subclass). Khi kế thừa class con được hưởng tất cả các phương thức và thuộc tính của class cha. Tuy nhiên, nó chỉ được truy cập các thành viên public và protected của class cha. Nó không được phép truy cập đến thành viên private của class cha.

_Cú pháp kế thừa trong java_

Sử dụng từ khóa <span style= "color:yellow">extends</span> để kế thừa.

```java
class Subclass-name extends Superclass-name {
   //methods and fields
}
```

_Các kiểu kế thừa trong java_

![](https://viettuts.vn/images/java/cac-kieu-ke-thua.jpg)

Ví dụ về đơn kế thừa:

```java
class Animal {
    void eat() {
        System.out.println("eating...");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("barking...");
    }
}

public class TestInheritance1 {
    public static void main(String args[]) {
        Dog d = new Dog();
        d.bark();
        d.eat();
    }
}
```

Ví dụ về kế thừa nhiều cấp

```java
class Animal {
    void eat() {
        System.out.println("eating...");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("barking...");
    }
}

class BabyDog extends Dog {
    void weep() {
        System.out.println("weeping...");
    }
}

public class TestInheritance2 {
    public static void main(String args[]) {
        BabyDog d = new BabyDog();
        d.weep();
        d.bark();
        d.eat();
    }
}
```

Ví dụ về kế thừa thứ bậc

```java
class Animal {
    void eat() {
        System.out.println("eating...");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("barking...");
    }
}

class Cat extends Animal {
    void meow() {
        System.out.println("meowing...");
    }
}

public class TestInheritance3 {
    public static void main(String args[]) {
        Cat c = new Cat();
        c.meow();
        c.eat();
        // c.bark(); // compile error
    }
}
```

**Polymorphism**

- Đa hình trong java (Polymorphism) là một khái niệm mà chúng ta có thể thực hiện một hành động bằng nhiều cách khác nhau
- Có hai kiểu của đa hình trong java, đó là đa hình lúc biên dịch (compile) và đa hình lúc thực thi (runtime).
- Chúng ta có thể thực hiện đa hình trong java bằng cách nạp chồng phương thức và ghi đè phương thức.

_Nạp chồng phương thức_

> Nạp chồng phương thức trong java xảy ra nếu một lớp có nhiều phương thức có tên giống nhau nhưng khác nhau về kiểu dữ liệu hoặc số lượng các tham số.

_Ghi đè phương thức_

> Nếu lớp con cung cấp sự cài đặt cụ thể cho phương thức đã được cung cấp bởi một lớp cha của nó được gọi là ghi đè phương thức

Các nguyên tắc ghi đè phương thức trong java:

- Phương thức phải có tên giống với lớp cha.
- Phương thức phải có tham số giống với lớp cha.
- Lớp con và lớp cha có mối quan hệ kế thừa.

**Access Modifier**

- Có hai loại Access Modifier trong Java, đó là: Access Modifier và Non-access Modifier.
- Access Modifer trong Java xác định phạm vi có thể truy cập của biến, phương thức, constructor hoặc lớp.
  > Trong java, có 4 phạm vi truy cập của Access Modifier như sau:
  >
  > - private
  > - default
  > - protected
  > - public

![](https://images.viblo.asia/3efc9ede-d8e3-4b93-b1f0-7b46e1e773f3.png)

- Ngoài ra, còn có nhiều Non-access Modifier như static, abstract, synchronized, native, volatile, transient,...

**Modifier Static**

Trong java, Static có thể là:

- Biến static: Khi bạn khai báo một biến là static, thì biến đó được gọi là biến tĩnh, hay biến static.
- Phương thức static: Khi bạn khai báo một phương thức là static, thì phương thức đó gọi là phương thức static.
- Khối static: Được sử dụng để khởi tạo thành viên dữ liệu static.

_Biến static_

- Biến static là biến tĩnh,có thể được sử dụng để tham chiếu thuộc tính chung của tất cả đối tượng (mà không là duy nhất cho mỗi đối tượng)
- Sử dụng biến static giúp chương trình của bạn sử dụng bộ nhớ hiệu quả hơn

_Phương thức static_

- Một phương thức static thuộc lớp chứ không phải đối tượng của lớp.
- Một phương thức static gọi mà không cần tạo một instance của một lớp.
- Phương thức static có thể truy cập biến static và có thể thay đổi giá trị của nó.

```java
public class Student9 {
    int rollno;
    String name;
    static String college = "Bưu Chính Viễn Thông";

    static void change() {
        // Thay đổi thuộc tính static (thuộc tính chung của tất cả các đối tượng)
        college = "Đại Học Công Nghệ";
    }

    Student9(int r, String n) {
        rollno = r;
        name = n;
    }

    void display() {
        System.out.println(rollno + " - " + name + " - " + college);
    }

    public static void main(String args[]) {
        Student9.change();

        Student9 s1 = new Student9(111, "Thông");
        Student9 s2 = new Student9(222, "Minh");
        Student9 s3 = new Student9(333, "Anh");

        s1.display();
        s2.display();
        s3.display();
    }
}
```

- Phương thức static không thể sử dụng biến non-static hoặc gọi trực tiếp phương thức non-static.

- Từ khóa this và super không thể được sử dụng trong ngữ cảnh static.
  vd:

```java
class A {
    int a = 40;// non static

    public static void main(String args[]) {
        System.out.println(a);
    }
}
```

_Khối static_

- Được sử dụng để khởi tạo thành viên dữ liệu static.
- Được thực thi trước phương thức main tại lúc tải lớp.

```java
public class A2 {
    static {
        System.out.println("Khối static: hello !");
    }

    public static void main(String args[]) {
        System.out.println("Main: hello !");
    }
}
```

**Interfaces**

> Các trường của Interface là public, static và final theo mặc định và các phương thức là public và abstract.
>
> Một Interface trong Java là một tập hợp các phương thức trừu tượng (abstract).
>
> Một interface không phải là một lớp. Viết một interface giống như viết một lớp, nhưng chúng có 2 định nghĩa khác nhau. Một lớp mô tả các thuộc tính và hành vi của một đối tượng. Một interface chứa các hành vi mà một class triển khai.
>
> Trừ khi một lớp triển khai interface là lớp trừu tượng abstract, còn lại tất cả các phương thức của interface cần được định nghĩa trong class.
>
> Một interface khác với một class ở một số điểm sau đây:
>
> - Bạn không thể khởi tạo một interface.
> - Một interface không chứa bất cứ hàm Contructor nào.
> - Tất cả các phương thức của interface đều là abstract.
> - Một interface không thể chứa một trường nào trừ các trường vừa static và final.
> - Một interface không thể kế thừa từ lớp, nó được triển khai bởi một lớp.
> - Một interface có thể kế thừa từ nhiều interface khác.

vd:

```java
interface Printable{
    void print();
}
interface Showable{
    void print();
}

class TestTnterface1 implements Printable,Showable{
    public void print() {
        System.out.println("Hello");
    }

    public static void main(String args[]) {
        TestTnterface1 obj = new TestTnterface1();
        obj.print();
    }
}
```

Marker (hay Tagging) Interface:

- Đó là một Interface mà không có thành viên nào.
- Mục đích :

  - Tạo một cha chung: Như với EventListener interface, mà được kế thừa bởi hàng tá các interface khác trong Java API, bạn có thể sử dụng một tagging interface để tạo một cha chung cho một nhóm interface. Ví dụ, khi một interface kế thừa EventListener, thì JVM biết rằng interface cụ thể này đang được sử dụng trong một event.
  - Thêm một kiểu dữ liệu tới một class: Đó là khái niệm tagging. Một class mà triển khai một tagging interface không cần định nghĩa bất kỳ phương thức nào, nhưng class trở thành một kiểu interface thông qua tính đa hình (polymorphism).

  **Abstract Classes**

  > Một lớp được khai báo với từ khóa abstract là lớp abstract trong Java. Lớp abstract có nghĩa là lớp trừu tượng, nó có thể có các phương thức abstract hoặc non-abtract.

Phương thức trừu tượng:

- Một phương thức được khai báo là abstract và không có trình triển khai thì đó là phương thức trừu tượng.
- Phương thức abstract sẽ không có định nghĩa, được theo sau bởi dấu chấm phảy, không có dấu ngoặc nhọn theo sau
  > abstract void printStatus();

Ví dụ về lớp trừu tượng và phương thức trừu tượng:

```java
abstract class Bike{
  abstract void run();
}
class Honda4 extends Bike{
    void run() {
        System.out.println("running safely..");
    }

    public static void main(String args[]) {
        Bike obj = new Honda4();
        obj.run();
    }
}
```

Trong ví dụ này, Bike là lớp trừu tượng chỉ chứa một phương thức trừu tượng là run. Trình triển khai của nó được cung cấp bởi lớp Honda.
