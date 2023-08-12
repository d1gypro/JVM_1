## Код для исследования
```java

public class JvmComprehension {  //  ClassLoader записывает информацию о классе в метаспейс, а также туда же записываются все системные классы, необходимые для работы

    public static void main(String[] args) { // в стэке создается фрейм main
        int i = 1;                      // в фрейме main создается выделяется место под примитивную переменную типа инт и ей присваивается значение 1
        Object o = new Object();        // new Object() - в куче(heap) создается ссылочный объект класса Object, в фрейме main указываем ссылку "о" на ранее созданный объект в куче
        Integer ii = 2;                 // в куче создается ссылочный объект типа данных Integer, кладем туда "2", в фрейме main указываем ссылку "ii" на ранее созданный объект в куче  
        printAll(o, i, ii);             // в стэке создается фрейм printAll, i копируется в данный фрейм, указываются 2 ссылки в этом фрейме на ранее созданные объекты в куче: "о" и "ii"
        System.out.println("finished"); // в стэке создается фрейм системного метода System.out.println, который выводит на экран строку "finished"
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // в куче создается ссылочный объект типа данных Integer, кладем туда "700", в фрейме printAll указываем ссылку "uselessVar" на ранее созданный объект в куче  
        System.out.println(o.toString() + i + ii);  // в стэке создается фрейм системного метода System.out.println, который проводит операцию по выводу на экран "суммы" примеденного к стрингу объекта "o" и двух целочисленных переменных,
                                                    // получится в итоге строка со ссылкой на этот объект в куче "+" 12 (11 и 1)
    }
}
// во время работы программы происходит "Stop The World" - приостановка работы программы, во время которой, происходит удаление объектов из памяти, которые не используются
```
