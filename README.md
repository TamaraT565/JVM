# JVM
Просмотрите код ниже и опишите (текстово или с картинками) каждую строку с точки зрения происходящего в JVM

Не забудьте упомянуть про:

ClassLoader’ы,
области памяти (стэк (и его фреймы), heap)
сборщик мусора

Код для исследования

public class JvmComprehension {

    public static void main(String[] args) {
        int i = 1;                      // 1
        Object o = new Object();        // 2
        Integer ii = 2;                 // 3
        printAll(o, i, ii);             // 4
        System.out.println("finished"); // 7
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5
        System.out.println(o.toString() + i + ii);  // 6
    }
}

Комментарии:
1. Объявлена переменная целых числел с наименованием i. Эта переменная будет храниться в stack.
2. ClassLoader загружает класс Object. Создан объект класса Object в heap (куча) (т.к. создали объект). Добавлена ссылка на объекта в stack.
3. ClassLoader загружает класс Integer.Ссылка переменной ii (Integer) будет храниться в stack.Значение переменной будет храниться в heap. 
4. Вызов метода printAll().В stack выделится память (frame), необходимая для выполнения метода.
5. Переменная uselessVar типа Integer будет создана в stack.Значение переменной будет храниться в heap.
6. Объект типа String создается heap.String передается методу println().После окончания работы метода println() его frame удаляется из stack.
7. В heap создается объект типа String "finished". String передается методу println() для вывода в консоли.После окончания работы метода println(), работа метода main() завершается, и его frame удаляется из stack.
