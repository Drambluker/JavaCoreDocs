# Объектно-ориентированное программирование

## Классы и объекты

Java является объектно-ориентированным языком, поэтому такие понятия как "класс" и "объект" играют в нем ключевую роль. Любую программу на Java можно представить как набор взаимодействующих между собой объектов.

Шаблоном или описанием объекта является класс, а объект представляет экземпляр этого класса. Можно еще провести следующую аналогию. У нас у всех есть некоторое представление о человеке - наличие двух рук, двух ног, головы, туловища и т.д. Есть некоторый шаблон - этот шаблон можно назвать классом. Реально же существующий человек (фактически экземпляр данного класса) является объектом этого класса.

Класс определяется с помощью ключевого слова `сlass`:

``` java
class Person {
    // ...
}
```

В данном случае класс называется `Person`. После названия класса идут фигурные скобки, между которыми помещается тело класса - то есть его поля и методы.

Любой объект может обладать двумя основными характеристиками: состояние - некоторые данные, которые хранит объект, и поведение - действия, которые может совершать объект.

Для хранения состояния объекта в классе применяются поля или переменные класса. Для определения поведения объекта в классе применяются методы. Например, класс `Person`, который представляет человека, мог бы иметь следующее определение:

``` java
class Person {
    String name;        // имя
    int age;            // возраст
    
    void displayInfo() {
        System.out.printf("Name: %s \tAge: %d\n", name, age);
    }
}
```

В классе `Person` определены два поля: `name` представляет имя человека, а `age` - его возраст. И также определен метод `displayInfo`, который ничего не возвращает и просто выводит эти данные в консоль.

Теперь используем данный класс. Для этого определим следующую программу:

``` java
public class Program {
    public static void main(String[] args) {
        Person tom;
    }
}

class Person {
    String name;    // имя
    int age;        // возраст
    
    void displayInfo() {
        System.out.printf("Name: %s \tAge: %d\n", name, age);
    }
}
```

Как правило, классы определяются в разных файлах. В данном случае для простоты мы определяем два класса в одном файле. Стоит отметить, что в этом случае только один класс может иметь модификатор `public` (в данном случае это класс `Program`), а сам файл кода должен называться по имени этого класса, то есть в данном случае файл должен называться `Program.java`.

Класс представляет новый тип, поэтому мы можем определять переменные, которые представляют данный тип. Так, здесь в методе `main` определена переменная `tom`, которая представляет класс `Person`. Но пока эта переменная не указывает ни на какой объект и по умолчанию она имеет значение `null`. По большому счету ее пока нельзя использовать, поэтому вначале необходимо создать объект класса `Person`.

## Конструкторы

Кроме обычных методов классы могут определять специальные методы, которые называются конструкторами. Конструкторы вызываются при создании нового объекта данного класса. Конструкторы выполняют инициализацию объекта.

Если в классе не определено ни одного конструктора, то для этого класса автоматически создается конструктор без параметров.

Выше определенный класс `Person` не имеет никаких конструкторов. Поэтому для него автоматически создается конструктор по умолчанию, который можно использовать для создания объекта `Person`. В частности, создадим один объект:

``` java
public class Program {
    public static void main(String[] args) {     
        Person tom = new Person(); // создание объекта
        tom.displayInfo();
         
        // изменяем имя и возраст
        tom.name = "Tom";
        tom.age = 34;
        tom.displayInfo();
    }
}

class Person {
    String name;    // имя
    int age;        // возраст
    
    void displayInfo() {
        System.out.printf("Name: %s \tAge: %d\n", name, age);
    }
}
```

Для создания объекта `Person` используется выражение `new Person()`. Оператор `new` выделяет память для объекта `Person`. И затем вызывается конструктор по умолчанию, который не принимает никаких параметров. В итоге после выполнения данного выражения в памяти будет выделен участок, где будут храниться все данные объекта `Person`. А переменная `tom` получит ссылку на созданный объект.

Если конструктор не инициализирует значения переменных объекта, то они получают значения по умолчанию. Для переменных числовых типов это число `0`, а для типа `String` и классов - это значение `null` (то есть фактически отсутствие значения).

После создания объекта мы можем обратиться к переменным объекта `Person` через переменную `tom` и установить или получить их значения, например, `tom.name = "Tom"`.

В итоге мы увидим в консоли:

```
Name: null		Age: 0
Name: Tom		Age: 34
```

Если необходимо, чтобы при создании объекта производилась какая-то логика, например, чтобы поля класса получали какие-то определенные значения, то можно определить в классе свои конструкторы. Например:

``` java
public class Program {
    public static void main(String[] args) {
        Person bob = new Person();          // вызов первого конструктора без параметров
        bob.displayInfo();
         
        Person tom = new Person("Tom");     // вызов второго конструктора с одним параметром
        tom.displayInfo();
         
        Person sam = new Person("Sam", 25); // вызов третьего конструктора с двумя параметрами
        sam.displayInfo();
    }
}

class Person{
    String name;    // имя
    int age;        // возраст
    
    Person() {
        name = "Undefined";
        age = 18;
    }
    
    Person(String n) {
        name = n;
        age = 18;
    }
    
    Person(String n, int a) {
        name = n;
        age = a;
    }
    
    void displayInfo() {
        System.out.printf("Name: %s \tAge: %d\n", name, age);
    }
}
```

Теперь в классе определено три конструктора, каждый из которых принимает различное количество параметров и устанавливает значения полей класса.

Консольный вывод программы:

```
Name: Undefined		Age: 18
Name: Tom		Age: 18
Name: Sam		Age: 25
```

## Ключевое слово this

Ключевое слово this представляет ссылку на текущий экземпляр класса. Через это ключевое слово мы можем обращаться к переменным, методам объекта, а также вызывать его конструкторы. Например:

``` java
public class Program {
    public static void main(String[] args) {         
        Person undef = new Person();
        undef.displayInfo();
         
        Person tom = new Person("Tom");
        tom.displayInfo();
         
        Person sam = new Person("Sam", 25);
        sam.displayInfo();
    }
}

class Person {
    String name;    // имя
    int age;        // возраст
    
    Person() {
        this("Undefined", 18);
    }
    
    Person(String name) {
        this(name, 18);
    }
    
    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    void displayInfo() {
        System.out.printf("Name: %s \tAge: %d\n", name, age);
    }
}
```

В третьем конструкторе параметры называются так же, как и поля класса. И чтобы разграничить поля и параметры, применяется ключевое слово `this`:

``` java
this.name = name;
```

Так, в данном случае указываем, что значение параметра `name` присваивается полю `name`.

Кроме того, у нас три конструктора, которые выполняют идентичные действия: устанавливают поля `name` и `age`. Чтобы избежать повторов, с помощью `this` можно вызвать один из конструкторов класса и передать для его параметров необходимые значения:

``` java
Person(String name) {
    this(name, 18);
}
```

В итоге результат программы будет тот же, что и в предыдущем примере.

## Инициализаторы

Кроме конструктора начальную инициализацию объекта вполне можно было проводить с помощью инициализатора объекта. Инициализатор выполняется до любого конструктора. То есть в инициализатор мы можем поместить код, общий для всех конструкторов:

``` java
public class Program {
    public static void main(String[] args) {
        Person undef = new Person();
        undef.displayInfo();
         
        Person tom = new Person("Tom");
        tom.displayInfo();
    }
}

class Person {
    String name;    // имя
    int age;        // возраст
     
    /*начало блока инициализатора*/
    {
        name = "Undefined";
        age = 18;
    }
    /*конец блока инициализатора*/
    
    Person() {}
    
    Person(String name) {
        this.name = name;
    }
    
    Person(String name, int age) { 
        this.name = name;
        this.age = age;
    }
    
    void displayInfo() {
        System.out.printf("Name: %s \tAge: %d\n", name, age);
    }
}
```

Консольный вывод:

```
Name: Undefined 	Age: 18
Name: Tom		Age: 18
```

## Статические поля и методы

Кроме обычных методов и полей класс может иметь статические поля, методы, константы и инициализаторы. Например, главный класс программы имеет метод `main`, который является статическим:

```java
public static void main(String[] args) {}
```

Для объявления статических переменных, констант, методов и инициализаторов перед их объявлением указывается ключевое слово `static`.

### Статические поля

При создании объектов класса для каждого объекта создается своя копия нестатических обычных полей. А статические поля являются общими для всего класса. Поэтому они могут использоваться без создания объектов класса.

Например, создадим статическую переменную:

```java
public class Program {
    public static void main(String[] args) {
        Person tom = new Person();
        Person bob = new Person();
         
        tom.displayId();                    // Id = 1
        bob.displayId();                    // Id = 2
        System.out.println(Person.counter); // 3
         
        // изменяем Person.counter
        Person.counter = 8;
         
        Person sam = new Person();
        sam.displayId();                    // Id = 8
    }
}

class Person {
    private int id;
    static int counter = 1;
     
    Person() {
        id = counter++;
    }
    
    public void displayId() {
        System.out.printf("Id: %d \n", id);
    }
}
```

Класс `Person` содержит статическую переменную `counter`, которая увеличивается в конструкторе и ее значение присваивается переменной `id`. То есть при создании каждого нового объекта `Person` эта переменная будет увеличиваться, поэтому у каждого нового объекта `Person` значение поля `id` будет на 1 больше чем у предыдущего.

Так как переменная `counter` статическая, то мы можем обратиться к ней в программе по имени класса:

```java
System.out.println(Person.counter); // получаем значение
Person.counter = 8;                 // изменяем значение
```

Консольный вывод программы:

```java
Id = 1
Id = 2
3
Id = 8
```

### Статические константы

Также статическими бывают константы, которые являются общими для всего класса.

```java
public class Program {
    public static void main(String[] args) {
        double radius = 60;
        System.out.printf("Radisu: %f \n", radius);             // 60
        System.out.printf("Area: %f \n", Math.PI * radius);     // 188,4
    }
}

class Math {
    public static final double PI = 3.14;
}
```

Стоит отметить, что на протяжении всех предыдущих тем уже активно использовались статические константы. В частности, в выражении:

```java
System.out.println("hello");
```

`out` как раз представляет статическую константу класса `System`. Поэтому обращение к ней идет без создания объекта класса `System`.

### Статические инициализаторы

Статические инициализаторы предназначены для инициализации статических переменных, либо для выполнения таких действий, которые выполняются при создании самого первого объекта. Например, определим статический инициализатор:

```java
public class Program {
    public static void main(String[] args) {
        Person tom = new Person();
        Person bob = new Person();
         
        tom.displayId();    // Id = 105
        bob.displayId();    // Id = 106
    }
}

class Person {
    private int id;
    
    static int counter;
     
    static {
        counter = 105;
        System.out.println("Static initializer");
    }
    
    Person() {
        id = counter++;
        System.out.println("Constructor");
    }
    
    public void displayId() {     
        System.out.printf("Id: %d \n", id);
    }
}
```

Статический инициализатор определяется как обычный, только перед ним ставится ключевое слово `static`. В данном случае в статическом инициализаторе мы устанавливаем начальное значение статического поля `counter` и выводим на консоль сообщение.

В самой программе создаются два объекта класса `Person`. Поэтому консольный вывод будет выглядеть следующим образом:

```
Static initializer
Constructor
Constructor
Id: 105
Id: 106
```

Стоит учитывать, что вызов статического инициализатора производится после загрузки класса и фактически до создания самого первого объекта класса.

### Статические методы

Статические методы также относятся ко всему классу в целом. Например, в примере выше статическая переменная `counter` была доступна извне, и мы могли изменить ее значение вне класса `Perso`n. Сделаем ее недоступной для изменения извне, но доступной для чтения. Для этого используем статический метод:

```java
public class Program {
    public static void main(String[] args) {
        Person.displayCounter();    // Counter: 1
         
        Person tom = new Person();
        Person bob = new Person();
         
        Person.displayCounter();    // Counter: 3
    }
}

class Person {
    private int id;
    private static int counter = 1;
     
    Person() {
        id = counter++;
    }
    
    // статический метод
    public static void displayCounter() {     
        System.out.printf("Counter: %d \n", counter);
    }
    
    public void displayId() {
        System.out.printf("Id: %d \n", id);
    }
}
```

Теперь статическая переменная недоступна извне, она приватная. А ее значение выводится с помощью статического метода `displayCounter`. Для обращения к статическому методу используется имя класса: `Person.displayCounter()`.

При использовании статических методов надо учитывать ограничения: в статических методах мы можем вызывать только другие статические методы и использовать только статические переменные.

Вообще методы определяются как статические, когда методы не затрагивают состояние объекта, то есть его нестатические поля и константы, и для вызова метода нет смысла создавать экземпляр класса. Например:

```java
public class Program {
    public static void main(String[] args) {
        System.out.println(Operation.sum(45, 23));          // 68
        System.out.println(Operation.subtract(45, 23));     // 22
        System.out.println(Operation.multiply(4, 23));      // 92
    }
}

class Operation {
    static int sum(int x, int y) {
        return x + y;
    }
    
    static int subtract(int x, int y) {
        return x - y;
    }
    
    static int multiply(int x, int y) {
        return x * y;
    }
}
```

В данном случае для методов `sum`, `subtract`, `multiply` не имеет значения, какой именно экземпляр класса `Operation` используется. Эти методы работают только с параметрами, не затрагивая состояние класса. Поэтому их можно определить как статические.

## Пакеты

Как правило, в Java классы объединяются в пакеты. Пакеты позволяют организовать классы логически в наборы. По умолчанию Java уже имеет ряд встроенных пакетов, например, `java.lang`, `java.util`, `java.io` и т.д. Кроме того, пакеты могут иметь вложенные пакеты.

Организация классов в виде пакетов позволяет избежать конфликта имен между классами. Ведь нередки ситуации, когда разработчики называют свои классы одинаковыми именами. Принадлежность к пакету позволяет гарантировать однозначность имен.

Чтобы указать, что класс принадлежит определенному пакету, надо использовать директиву package, после которой указывается имя пакета:

```java
package название_пакета;
```

Как правило, названия пакетов соответствуют физической структуре проекта, то есть организации каталогов, в которых находятся файлы с исходным кодом. А путь к файлам внутри проекта соответствует названию пакета этих файлов. Например, если классы принадлежат пакету `mypack`, то эти классы помещаются в проекте в папку `mypack`.

Классы необязательно определять в пакеты. Если для класса пакет не определен, то считается, что данный класс находится в пакете по умолчанию, который не имеет имени.

Например, создадим в папке для исходных файлов каталог `study`. В нем создадим файл `Program.java` со следующим кодом:

```java
package study;

public class Program {
    public static void main(String[] args) {
        Person kate = new Person("Kate", 32);
        kate.displayInfo();
    }
}

class Person {
    String name;
    int age;
 
    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    void displayInfo() {
        System.out.printf("Name: %s \t Age: %d \n", name, age);
    }
}
```

Директива `package study` в начале файла указывает, что классы `Program` и `Person`, которые здесь определены, принадлежат пакету `study`.

Когда мы работаем в среде разработки, например, в IntelliJ IDEA, то IDE берет на себя все вопросы компиляции пакетов и входящих в них файлов. Соответственно нам достаточно нажать на кнопку, и все будет готово. Однако если мы компилируем программу в командной строке, то мы можем столкнуться с некоторыми трудностями. Поэтому рассмотрим этот аспект.

Для компиляции программы вначале в командной строке/терминале перейдем к папке, где находится каталог с исходным кодом, например, каталог study.

В моём случае это каталог `C:\java` (то есть файл с исходным кодом расположен по пути `C:\java\study\Program.java`).

Для компиляции выполним команду

```bash
javac study\Program.java
```

После этого в папке study появятся скомпилированные файлы `Program.class` и `Person.class`. Для запуска программы выполним команду:

```bash
java study.Program
````

### Импорт пакетов и классов

Если нам надо использовать классы из других пакетов, то нам надо подключить эти пакеты и классы. Исключение составляют классы из пакета `java.lang` (например, `String`), которые подключаются в программу автоматически.

Например, знакомый по прошлым темам класс `Scanner` находится в пакете `java.util`, поэтому мы можем получить к нему доступ следующим способом:

```java
java.util.Scanner in = new java.util.Scanner(System.in);
```

То есть мы указываем полный путь к файлу в пакете при создании его объекта. Однако такое нагромождение имен пакетов не всегда удобно, и в качестве альтернативы мы можем импортировать пакеты и классы в проект с помощью директивы `import`, которая указывается после директивы `package`:

```java
package study;

import java.util.Scanner; // импорт класса Scanner

public class Program {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
    }
}
```

Директива `import` указывается в самом начале кода, после чего идет имя подключаемого класса (в данном случае класса `Scanner`).

В примере выше мы подключили только один класс, однако пакет `java.util` содержит еще множество классов. И чтобы не подключать по отдельности каждый класс, мы можем сразу подключить весь пакет:

```java
import java.util.*; // импорт всех классов из пакета java.util
```

Теперь мы можем использовать любой класс из пакета `java.util`.

Возможна ситуация, когда мы используем два класса с одним и тем же названием из двух разных пакетов, например, класс `Date` имеется и в пакете `java.util`, и в пакете `java.sql`. И если нам надо одновременно использовать два этих класса, то необходимо указывать полный путь к этим классам в пакете:

```java
java.util.Date utilDate = new java.util.Date();
java.sql.Date sqlDate = new java.sql.Date();
```

### Статический импорт

В Java есть также особая форма импорта - статический импорт. Для этого вместе с директивой `import` используется модификатор `static`:

```java
package study;

import static java.lang.System.*;
import static java.lang.Math.*;

public class Program {
    public static void main(String[] args) {
        double result = sqrt(20);
        out.println(result);
    }
}
```

Здесь происходит статический импорт классов `System` и `Math`. Эти классы имеют статические методы. Благодаря операции статического импорта мы можем использовать эти методы без названия класса. Например, писать не `Math.sqrt(20)`, а `sqrt(20)`, так как функция `sqrt()`, которая возвращает квадратный корень числа, является статической.

То же самое в отношении класса `System`: в нем определен статический объект `out`, поэтому мы можем его использовать без указания класса.

## Модификаторы доступа и инкапсуляция

Все члены класса в языке Java - поля и методы - имеют модификаторы доступа. В прошлых темах мы уже сталкивались с модификатором `public`. Модификаторы доступа позволяют задать допустимую область видимости для членов класса, то есть контекст, в котором можно употреблять данную переменную или метод.

В Java используются следующие модификаторы доступа:

- `public` - публичный, общедоступный класс или член класса. Поля и методы, объявленные с модификатором `public`, видны другим классам из текущего пакета и из внешних пакетов.
- `private` - закрытый класс или член класса, противоположность модификатору `public`. Закрытый класс или член класса доступен только из кода в том же классе.
- `protected` - такой класс или член класса доступен из любого места в текущем классе или пакете или в производных классах, даже если они находятся в других пакетах
- Модификатор по умолчанию. Отсутствие модификатора у поля или метода класса предполагает применение к нему модификатора по умолчанию. Такие поля или методы видны всем классам в текущем пакете.

Рассмотрим модификаторы доступа на примере следующей программы:

```java
public class Program {

    public static void main(String[] args) {

        Person kate = new Person("Kate", 32, "Baker Street", "+12334567");
        kate.displayName();                 // норм, метод public
        kate.displayAge();                  // норм, метод имеет модификатор по умолчанию
        kate.displayPhone();                // норм, метод protected
        //kate.displayAddress();            // ! Ошибка, метод private

        System.out.println(kate.name);      // норм, модификатор по умолчанию
        System.out.println(kate.address);   // норм, модификатор public
        System.out.println(kate.age);       // норм, модификатор protected
        //System.out.println(kate.phone);   // ! Ошибка, модификатор private
    }
}

class Person {
    String name;
    protected int age;
    public String address;
    private String phone;

    public Person(String name, int age, String address, String phone) {
        this.name = name;
        this.age = age;
        this.address = address;
        this.phone = phone;
    }

    public void displayName() {
        System.out.printf("Name: %s \n", name);
    }

    void displayAge() {
        System.out.printf("Age: %d \n", age);
    }

    private void displayAddress() {
        System.out.printf("Address: %s \n", address);
    }

    protected void displayPhone() {
        System.out.printf("Phone: %s \n", phone);
    }
}
```

В данном случае оба класса расположены в одном пакете - пакете по умолчанию, поэтому в классе `Program` мы можем использовать все методы и переменные класса `Person`, которые имеют модификатор по умолчанию, `public` и `protected`. А поля и методы с модификатором `private` в классе `Program` не будут доступны.

Если бы класс `Program` располагался в другом пакете, то ему были бы доступны только поля и методы с модификатором `public`.

Модификатор доступа должен предшествовать остальной части определения переменной или метода.

### Инкапсуляция

Казалось бы, почему бы не объявить все переменные и методы с модификатором `public`, чтобы они были доступны в любой точке программы вне зависимости от пакета или класса? Возьмем, например, поле `age`, которое представляет возраст. Если другой класс имеет прямой доступ к этому полю, то есть вероятность, что в процессе работы программы ему будет передано некорректное значение, например, отрицательное число. Подобное изменение данных не является желательным. Либо же мы хотим, чтобы некоторые данные были достуны напрямую, чтобы их можно было вывести на консоль или просто узнать их значение. Поэтому рекомендуется как можно больше ограничивать доступ к данным, чтобы защитить их от нежелательного доступа извне (как для получения значения, так и для его изменения). Использование различных модификаторов гарантирует, что данные не будут искажены или изменены не надлежащим образом. Подобное сокрытие данных внутри некоторой области видимости называется инкапсуляцией.

Так, как правило, вместо непосредственного применения полей используют методы доступа. Например:

```java
public class Program {

    public static void main(String[] args) {
        Person kate = new Person("Kate", 30);
        System.out.println(kate.getAge());      // 30
        kate.setAge(33);
        System.out.println(kate.getAge());      // 33
        kate.setAge(123450);
        System.out.println(kate.getAge());      // 33
    }
}

class Person {
    private String name;
    private int age = 1;

    public Person(String name, int age) {
        setName(name);
        setAge(age);
    }

    public String getName() {
        return this.name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return this.age;
    }

    public void setAge(int age) {
        if (age > 0 && age < 110)
            this.age = age;
    }
}
```

И затем вместо непосредственной работы с полями `name` и `age` в классе `Person` мы будем работать с методами, которые устанавливают и возвращают значения этих полей. Методы `setName`, `setAge` и наподобие еще называют мьютейтерами (mutator), так как они изменяют значения поля. А методы `getName`, `getAge` и наподобие называют аксессерами (accessor), так как с их помощью мы получаем значение поля.

Причем в эти методы мы можем вложить дополнительную логику. Например, в данном случае при изменении возраста производится проверка, насколько соответствует новое значение допустимому диапазону.

## Объекты как параметры методов

Объекты классов, как и данные примитивных типов, могут передаваться в методы. Однако в данном случае есть одна особенность - при передаче объектов в качестве значения передается копия ссылки на область в памяти, где расположен этот объект. Рассмотрим небольшой пример. Пусть у нас есть следующий класс `Person`:

```java
public class Program {

    public static void main(String[] args) {
        Person kate = new Person("Kate");
        System.out.println(kate.getName());     // Kate
        changeName(kate);
        System.out.println(kate.getName());     // Alice
    }
    
    static void changeName(Person p){
        p.setName("Alice");
    }
}

class Person {

    private String name;
 
    Person(String name) {
        this.name = name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public String getName() {
        return this.name;
    }
}
```

Здесь в метод `changeName` передается объект `Person`, у которого изменяется имя. Так как в метод будет передаваться копия ссылки на область памяти, в которой находится объект `Person`, то переменная `kate` и параметр `p` метода `changeName` будут указывать на один и тот же объект в памяти. Поэтому после выполнения метода у объекта `kate`, который передается в метод, будет изменено имя с `"Kate"` на `"Alice"`.

От этого случая следует отличать другой случай:

```java
public class Program {

    public static void main(String[] args) {
        Person kate = new Person("Kate");
        System.out.println(kate.getName());     // Kate
        changePerson(kate);
        System.out.println(kate.getName());     // Kate - изменения не произошло
                                                // kate хранит ссылку на старый объект
    }
    
    static void changePerson(Person p) {
        p = new Person("Alice");    // p указывает на новый объект
        p.setName("Ann");
    }
    
    static void changeName(Person p) {
        p.setName("Alice");
    }
}

class Person {

    private String name;
 
    Person(String name) {
        this.name = name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public String getName() {
        return this.name;
    }
}
```

В метод `changePerson` также передается копия ссылки на объект `Person`. Однако в самом методе мы изменяем не отдельные значения объекта, а пересоздаем объект с помощью конструктора и оператора `new`. В результате в памяти будет выделено новое место для нового объекта `Person`, и ссылка на этот объект будет присвоена параметру `p`:

```java
static void changePerson(Person p) {
    p = new Person("Alice");    // p указывает на новый объект
    p.setName("Ann");           // изменяется новый объект
}
```

То есть после создания нового объекта `Person` параметр `p` и переменная `kate` в методе `main` будут хранить ссылки на разные объекты. Переменная `kate`, которая передавалась в метод, продолжит хранить ссылку на старый объект в памяти. Поэтому её значение не меняется.

## Внутренние и вложенные классы

Классы могут быть вложенными (nested), то есть могут быть определены внутри других классов. Частным случаем вложенных классов являются внутренние классы (inner class). Например, имеется класс `Person`, внутри которого определен класс `Account`:

```java
public class Program {

    public static void main(String[] args) {
        Person tom = new Person("Tom", "qwerty");
        tom.displayPerson();
        tom.account.displayAccount();
    }
}

class Person {

    private String name;
    Account account;
 
    Person(String name, String password) {
        this.name = name;
        account = new Account(password);
    }
    
    public void displayPerson() {
        System.out.printf("Person \t Name: %s \t Password: %s \n", name, account.password);
    }
 
    public class Account {
        private String password;
         
        Account(String pass) {
            this.password = pass;
        }
        
        void displayAccount() {
            System.out.printf("Account Login: %s \t Password: %s \n", Person.this.name, password);
        }
    }
}
```

Внутренний класс ведет себя как обычный класс за тем исключением, что его объекты могут быть созданы только внутри внешнего класса.

Внутренний класс имеет доступ ко всем полям внешнего класса, в том числе закрытым с помощью модификатора `private`. Аналогично внешний класс имеет доступ ко всем членам внутреннего класса, в том числе к полям и методам с модификатором `private`.

Ссылку на объект внешнего класса из внутреннего класса можно получить с помощью выражения `Внешний_Класс.this`, например, `Person.this`.

Объекты внутренних классов могут быть созданы только в том классе, в котором внутренние классы опеределены. В других внешних классах объекты внутреннего класса создать нельзя.

Еще одной особенностью внутренних классов является то, что их можно объявить внутри любого контекста, в том числе внутри метода и даже в цикле:

```java
public class Program{

    public static void main(String[] args) {
        Person tom = new Person("Tom");
        tom.setAccount("qwerty");
    }
}

class Person {

    private String name;
 
    Person(String name) {
        this.name = name;
    }
     
    public void setAccount(String password) {
        
        class Account {
            void display() {
                System.out.printf("Account Login: %s \t Password: %s \n", name, password);
            }
        }
        
        Account account = new Account();
        account.display();
    }
}
```

### Статические вложенные классы

Кроме внутренних классов также могут быть статические вложенные классы. Статические вложенные классы позволяют скрыть некоторую комплексную, или другими словами составную, информацию внутри внешнего класса:

```java
class Math {

    public static class Factorial {
     
        private int result;
        private int key;
         
        public Factorial(int number, int x) {
            result = number;
            key = x;
        }
         
        public int getResult() {
            return result;
        }
         
        public int getKey() {
            return key;
        }
    }
     
    public static Factorial getFactorial(int x) {
        int result = 1;
        for (int i = 1; i <= x; i++) {
            result *= i;
        }
        return new Factorial(result, x);
    }
}
```

Здесь определен вложенный класс для хранения данных о вычислении факториала. Основные действия выполняет метод `getFactorial`, который возвращает объект вложенного класса. И теперь используем классы в методе `main`:

```java
public static void main(String[] args) {
    Math.Factorial fact = Math.getFactorial(6);
    System.out.printf("Факториал числа %d равен %d \n", fact.getKey(), fact.getResult());
}
```

## Перечисления enum

Кроме отдельных примитивных типов данных и классов в Java есть такой тип как `enum` или перечисление. Перечисления представляют набор логически связанных констант. Объявление перечисления происходит с помощью оператора `enum`, после которого идет название перечисления. Затем идет список элементов перечисления через запятую:

```java
enum Day {
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY,
    SUNDAY
}
```

Перечисление фактически представляет новый тип, поэтому мы можем определить переменную данного типа и использовать её:

```java
public class Program {
    public static void main(String[] args) {
        Day current = Day.MONDAY;
        System.out.println(current);    // MONDAY
    }
}

enum Day {
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY,
    SUNDAY
}
```

Перечисления могут использоваться в классах для хранения данных:

```java
public class Program {
    public static void main(String[] args) {
        Book b1 = new Book("War and Peace", "L. Tolstoy", Type.BELLETRE);
        System.out.printf("Book '%s' has a type %s \n", b1.name, b1.getType());
    }
}

class Book {
    private Type bookType;
    String name;
    String author;
   
    Book(String name, String author, Type type) {
        this.bookType = type;
        this.name = name;
        this.author = author;
    }
    
    String getType() {
        switch (bookType) {
            case BELLETRE: return "Belletre";
            case SCIENCE: return "Science";
            case SCIENCE_FICTION: return "Science fiction"; 
            case PHANTASY: return "Phantasy";
            default: return "Undefined";
        }
    }
}

enum Type {
    SCIENCE,
    BELLETRE,
    PHANTASY,
    SCIENCE_FICTION
}
```

Само перечисление объявлено вне класса, оно содержит четыре жанра книг. Класс `Book` кроме обычных переменных содержит также переменную типа нашего перечисления. В конструкторе мы ее также можем присвоить, как и обычные поля класса.

С помощью конструкции `switch`/`case` можно проверить принадлежность значения `bookType` определенной константе перечисления. Пример работы программы:

```
Book 'War and Peace' has a type Belletre
```

### Методы перечислений

Каждое перечисление имеет статический метод `values()`. Он возвращает массив всех констант перечисления:

```java
public class Program {
    public static void main(String[] args) {
        Type[] types = Type.values();
        for (Type s : types) {
            System.out.println(s);
        }
    }
}

enum Type {
    SCIENCE,
    BELLETRE,
    PHANTASY,
    SCIENCE_FICTION
}
```

Метод `ordinal()` возвращает порядковый номер определенной константы (нумерация начинается с 0):

```java
System.out.println(Type.BELLETRE.ordinal());    // 1
```

### Конструкторы, поля и методы перечисления

Перечисления, как и обычные классы, могут определять конструкторы, поля и методы. Например:

```java
public class Program {
    public static void main(String[] args) {
        System.out.println(Color.RED.getCode());        // #FF0000
        System.out.println(Color.GREEN.getCode());      // #00FF00    
    }
}

enum Color {
    RED("#FF0000"), BLUE("#0000FF"), GREEN("#00FF00");

    private String code;

    Color(String code) {
        this.code = code;
    }
    
    public String getCode() {
        return code;
    }
}
```

Перечисление `Color` определяет приватное поле `code` для хранения кода цвета, а с помощью метода `getCode()` оно возвращается. Через конструктор передается для него значение. Следует отметить, что конструктор по умолчанию приватный, то есть имеет модификатор `private`. Любой другой модификатор будет считаться ошибкой. Поэтому создать константы перечисления с помощью конструктора мы можем только внутри перечисления.

Также можно определять методы для отдельных констант:

```java
public class Program {
    public static void main(String[] args) {
        Operation op = Operation.SUM;
        System.out.println(op.action(10, 4));   // 14
        op = Operation.MULTIPLY;
        System.out.println(op.action(6, 4));    // 24
    }
}

enum Operation {
    SUM {
        public int action(int x, int y) {
            return x + y;
        }
    },
    SUBTRACT {
        public int action(int x, int y) {
            return x - y;
        }
    },
    MULTIPLY {
        public int action(int x, int y) {
            return x * y;
        }
    };

    public abstract int action(int x, int y);
}
```

## Наследование

Одним из ключевых аспектов объектно-ориентированного программирования является наследование. С помощью наследования можно расширить функционал уже имеющихся классов за счет добавления нового функционала или изменения старого. Например, имеется следующий класс `Person`, описывающий отдельного человека:

```java
class Person {

    String name;
    public String getName() {
        return name;
    }
     
    public Person(String name) {
        this.name=name;
    }
   
    public void display() {
        System.out.println("Name: " + name);
    }
}
```

И, возможно, впоследствии мы захотим добавить еще один класс, который описывает сотрудника предприятия - класс `Employee.` Так как этот класс реализует тот же функционал, что и класс `Person`, поскольку сотрудник - это также и человек, то было бы рационально сделать класс `Employee` производным (наследником, подклассом) от класса `Person`, который, в свою очередь, называется базовым классом, родителем или супер-классом:

```java
class Employee extends Person {
    public Employee(String name) {
        super(name); // если базовый класс определяет конструктор
                     // то производный класс должен его вызвать
    }
}
```

Чтобы объявить один класс наследником от другого, надо использовать после имени класса-наследника ключевое слово `extends`, после которого идет имя базового класса. Для класса `Employee` базовым является `Person`, и поэтому класс `Employee` наследует все те же поля и методы, которые есть в классе `Person`.

Если в базовом классе определены конструкторы, то в конструкторе производного класса необходимо вызвать один из конструкторов базового класса с помощью ключевого слова `super`. Например, класс `Person` имеет конструктор, который принимает один параметр. Поэтому в классе `Employee` в конструкторе нужно вызвать конструктор класса `Person`. То есть вызов `super(name)` будет представлять вызов конструктора класса `Person`.

При вызове конструктора после слова `super` в скобках идет перечисление передаваемых аргументов. При этом вызов конструктора базового класса должен идти в самом начале в конструкторе производного класса. Таким образом, установка имени сотрудника делегируется конструктору базового класса.

Причем даже если производный класс никакой другой работы не производит в конструкторе, как в примере выше, все равно необходимо вызвать конструктор базового класса.

Использование классов:

```java
public class Program {
    public static void main(String[] args) {
        Person tom = new Person("Tom");
        tom.display();
        Employee sam = new Employee("Sam");
        sam.display();
    }
}

class Person {

    String name;
    public String getName() {
        return name;
    }
      
    public Person(String name) {
        this.name = name;
    }
   
    public void display() {
        System.out.println("Name: " + name);
    }
}

class Employee extends Person {
    public Employee(String name) {
        super(name); // если базовый класс определяет конструктор
                     // то производный класс должен его вызвать
    }
}
```

Производный класс имеет доступ ко всем методам и полям базового класса (даже если базовый класс находится в другом пакете) кроме тех, которые определены с модификатором `private`. При этом производный класс также может добавлять свои поля и методы:

```java
public class Program {
    public static void main(String[] args) {
        Employee sam = new Employee("Sam", "Microsoft");
        sam.display();  // Sam
        sam.work();     // Sam works in Microsoft
    }
}

class Person {

    String name;
    public String getName() {
        return name;
    }
      
    public Person(String name) {
        this.name=name;
    }
   
    public void display(){
          
        System.out.println("Name: " + name);
    }
}
class Employee extends Person{

    String company;
      
    public Employee(String name, String company) {
      
        super(name);
        this.company=company;
    }
    public void work(){
        System.out.printf("%s works in %s \n", getName(), company);
    }
}
```

В данном случае класс `Employee` добавляет поле `company`, которое хранит место работы сотрудника, а также метод `work`.

### Переопределение методов

Производный класс может определять свои методы, а может переопределять методы, которые унаследованы от базового класса. Например, переопределим в классе `Employee` метод `display`:

```java
public class Program {
    public static void main(String[] args) {
        Employee sam = new Employee("Sam", "Microsoft");
        sam.display(); // Sam
                       // Works in Microsoft
    }
}

class Person {

    String name;
    public String getName() {
        return name;
    }
      
    public Person(String name) {
        this.name = name;
    }
   
    public void display() {
        System.out.println("Name: " + name);
    }
}

class Employee extends Person {

    String company;
      
    public Employee(String name, String company) {
        super(name);
        this.company=company;
    }
    
    @Override
    public void display() {
        System.out.printf("Name: %s \n", getName());
        System.out.printf("Works in %s \n", company);
    }
}
```

Перед переопределяемым методом указывается аннотация `@Override`. Данная аннотация в принципе необязательна.

При переопределении метода он должен иметь уровень доступа не меньше, чем уровень доступа в базовом классе. Например, если в базовом классе метод имеет модификатор `public`, то и в производном классе метод должен иметь модификатор `public`.

Однако в данном случае мы видим, что часть метода `display` в `Employee` повторяет действия из метода `display` базового класса. Поэтому мы можем сократить класс `Employee`:

```java
class Employee extends Person {

    String company;
      
    public Employee(String name, String company) {
        super(name);
        this.company=company;
    }
    
    @Override
    public void display() {      
        super.display();
        System.out.printf("Works in %s \n", company);
    }
}
```

С помощью ключевого слова `super` мы также можем обратиться к реализации методов базового класса.

### Запрет наследования

Хотя наследование очень интересный и эффективный механизм, но в некоторых ситуациях его применение может быть нежелательным. И в этом случае можно запретить наследование с помощью ключевого слова `final`. Например:

```java
public final class Person {}
```

Если бы класс `Person` был бы определен таким образом, то следующий код был бы ошибочным и не сработал, так как мы тем самым запретили наследование:

```java
class Employee extends Person {}
```

Кроме запрета наследования можно также запретить переопределение отдельных методов. Например, в примере выше переопределен метод `display()`, запретим его переопределение:

```java
public class Person {

    //........................
     
    public final void display() {
        System.out.println("Имя: " + name);
    }
}
```

В этом случае класс `Employee` не сможет переопределить метод `display`.

### Динамическая диспетчеризация методов

Наследование и возможность переопределения методов открывают нам большие возможности. Прежде всего мы можем передать переменной супер-класса ссылку на объект подкласса:

```java
Person sam = new Employee("Sam", "Oracle");
```

Так как `Employee` наследуется от `Person`, то объект `Employee` является в то же время и объектом `Person`. Грубо говоря, любой работник предприятия одновременно является человеком.

Однако несмотря на то, что переменная представляет объект `Person`, виртуальная машина видит, что в реальности она указывает на объект `Employee`. Поэтому при вызове методов у этого объекта будет вызываться та версия метода, которая определена в классе `Employee`, а не в `Person`. Например:

```java
public class Program {
    public static void main(String[] args) {
        Person tom = new Person("Tom");
        tom.display();
        Person sam = new Employee("Sam", "Oracle");
        sam.display();
    }
}

class Person {

    String name;
     
    public String getName() {
        return name;
    }
    
    public Person(String name) {
        this.name = name;
    }
  
    public void display() {
        System.out.printf("Person %s \n", name);
    }
}

class Employee extends Person {

    String company;
     
    public Employee(String name, String company) {
        super(name);
        this.company = company;
    }
    
    @Override
    public void display() {
        System.out.printf("Employee %s works in %s \n", super.getName(), company);
    }
}
```

Консольный вывод данной программы:

```
Person Tom
Employee Sam works in Oracle
```

При вызове переопределенного метода виртуальная машина динамически находит и вызывает именно ту версию метода, которая определена в подклассе. Данный процесс еще называется **dynamic method lookup** или динамический поиск метода или динамическая диспетчеризация методов.

## Класс Object и его методы

Хотя мы можем создать обычный класс, который не является наследником, но фактически все классы наследуются от класса `Object`. Все остальные классы, даже те, которые мы добавляем в свой проект, являются неявно производными от класса `Object`. Поэтому все типы и классы могут реализовать те методы, которые определены в классе `Object`. Рассмотрим эти методы.

### toString

Метод `toString` служит для получения представления данного объекта в виде строки. При попытке вывести строковое представления какого-нибудь объекта, как правило, будет выводиться полное имя класса. Например:

```java
public class Program {
    public static void main(String[] args) {
        Person tom = new Person("Tom");
        System.out.println(tom.toString()); // Будет выводить что-то наподобие Person@7960847b
    }
}

class Person {

    private String name;
     
    public Person(String name) {
        this.name=name;
    }
}
```

Полученное значение (в данном случае `Person@7960847b`) вряд ли может служить хорошим строковым описанием объекта. Поэтому метод `toString()` нередко переопределяют. Например:

```java
public class Program {
    public static void main(String[] args) {
        Person tom = new Person("Tom");
        System.out.println(tom.toString()); // Person Tom
    }
}

class Person {

    private String name;
    
    public Person(String name) {
        this.name = name;
    }
     
    @Override
    public String toString() {
        return "Person " + name;
    }
}
```

### Метод equals

Метод `equals` сравнивает два объекта на равенство:

```java
public class Program {

    public static void main(String[] args) {
        Person tom = new Person("Tom");
        Person bob = new Person("Bob");
        System.out.println(tom.equals(bob)); // false
         
        Person tom2 = new Person("Tom");
        System.out.println(tom.equals(tom2)); // true
    }
}

class Person {

    private String name;
     
    public Person(String name) {
        this.name=name;
    }
     
    @Override
    public boolean equals(Object obj) {
        if (!(obj instanceof Person)) return false;
 
        Person p = (Person)obj;
        return this.name.equals(p.name);
    }
}
```

Метод `equals` принимает в качестве параметра объект любого типа, который мы затем приводим к текущему, если они являются объектами одного класса.

Оператор `instanceof` позволяет выяснить, является ли переданный в качестве параметра объект объектом определенного класса, в данном случае класса `Person`. Если объекты принадлежат к разным классам, то их сравнение не имеет смысла, и возвращается значение `false`.

Затем сравниваем по именам. Если они совпадают, возвращаем `true`, что будет говорить, что объекты равны.

### Метод hashCode

Метод `hashCode` позволяет задать некоторое числовое значение, которое будет соответствовать данному объекту, другими словами хэш-код. По данному числу, например, можно сравнивать объекты.

Например, выведем хэш-код вышеопределенного объекта:

```java
Person tom = new Person("Tom");
System.out.println(tom.hashCode()); // 2036368507
```

Но мы можем задать свой алгоритм определения хэш-кода объекта:

```java
class Person {

    private String name;
    
    public Person(String name) {
        this.name=name;
    }
     
    @Override
    public int hashCode() {
        return 10 * name.hashCode() + 20456;
    }
}
```

### Получение типа объекта и метод getClass

Метод `getClass` позволяет получить тип данного объекта:

```java
Person tom = new Person("Tom");
System.out.println(tom.getClass()); // class Person
```

## Абстрактные классы

Кроме обычных классов в Java есть абстрактные классы. Абстрактный класс похож на обычный класс. В абстрактном классе также можно определить поля и методы, но в то же время нельзя создать объект или экземпляр абстрактного класса. Абстрактные классы призваны предоставлять базовый функционал для классов-наследников. А производные классы уже реализуют этот функционал.

При определении абстрактных классов используется ключевое слово `abstract`:

```java
public abstract class Human {

    private String name;
     
    public String getName() {
        return name;
    }
}
```

Но главное отличие состоит в том, что мы не можем использовать конструктор абстрактного класса для создания его объекта. Например, следующим образом:

```java
Human h = new Human();
```

Кроме обычных методов абстрактный класс может содержать абстрактные методы. Такие методы определяются с помощью ключевого слова `abstract` и не имеют никакой реализации:

```java
public abstract void display();
```

Производный класс обязан переопределить и реализовать все абстрактные методы, которые имеются в базовом абстрактном классе. Также следует учитывать, что если класс имеет хотя бы один абстрактный метод, то данный класс должен быть определен как абстрактный.

Зачем нужны абстрактные классы? Допустим, мы делаем программу для обслуживания банковских операций и определяем в ней три класса: `Person`, который описывает человека, `Employee`, который описывает банковского служащего, и класс `Client`, который представляет клиента банка. Очевидно, что классы `Employee` и `Client` будут производными от класса `Person`, так как оба класса имеют некоторые общие поля и методы. И так как все объекты будут представлять либо сотрудника, либо клиента банка, то напрямую мы от класса `Person` создавать объекты не будем. Поэтому имеет смысл сделать его абстрактным.

```java
public class Program {

    public static void main(String[] args) {
        Employee sam = new Employee("Sam", "Leman Brothers");
        sam.display();
        Client bob = new Client("Bob", "Leman Brothers");
        bob.display();
    }
}

abstract class Person {

    private String name;
     
    public String getName() {
        return name;
    }
    
    public Person(String name) {
        this.name = name;
    }
  
    public abstract void display();
}

class Employee extends Person {

    private String bank;
     
    public Employee(String name, String company) {
        super(name);
        this.bank = company;
    }
     
    public void display() {
        System.out.printf("Employee Name: %s \t Bank: %s \n", super.getName(), bank);
    }
}

class Client extends Person {
    
    private String bank;

    public Client(String name, String company) {
        super(name);
        this.bank = company;
    }
     
    public void display() {
        System.out.printf("Client Name: %s \t Bank: %s \n", super.getName(), bank);
    }
}
```

Другим хрестоматийным примером является система геометрических фигур. В реальности не существует геометрической фигуры как таковой. Есть круг, прямоугольник, квадрат, но просто фигуры нет. Однако же и круг, и прямоугольник имеют что-то общее и являются фигурами:

```java
// абстрактный класс фигуры
abstract class Figure {

    float x; // x-координата точки
    float y; // y-координата точки
  
    Figure(float x, float y) {
        this.x=x;
        this.y=y;
    }
    
    // абстрактный метод для получения периметра
    public abstract float getPerimeter();
    // абстрактный метод для получения площади
    public abstract float getArea();
}

// производный класс прямоугольника
class Rectangle extends Figure {

    private float width;
    private float height;

    // конструктор с обращением к конструктору класса Figure
    Rectangle(float x, float y, float width, float height) {
        super(x,y);
        this.width = width;
        this.height = height;
    }
     
    public float getPerimeter() {
        return width * 2 + height * 2;
    }
     
    public float getArea() {
        return width * height;
    }
}
```
