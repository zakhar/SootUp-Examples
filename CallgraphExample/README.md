# CallgraphExample

Пример использования SootUp для построения графа вызовов (Call Graph) с использованием алгоритма Class Hierarchy Analysis (CHA).

## Описание

Этот пример демонстрирует:
- Создание JavaView для анализа байт-кода
- Построение иерархии типов
- Создание графа вызовов с помощью CHA алгоритма
- Вывод информации о вызовах методов

## Требования

- Java 11 или выше
- Maven 3.6+

## Запуск

### Способ 1: Через Maven exec

```bash
cd CallgraphExample
mvn clean compile exec:java
```

### Способ 2: Через Maven exec с указанием main класса

```bash
cd CallgraphExample
mvn exec:java -Dexec.mainClass="sootup.examples.CallgraphExample"
```

### Способ 3: Через java напрямую

```bash
cd CallgraphExample
mvn compile
java -cp "$(mvn dependency:build-classpath -q -Dmdep.outputFile=/dev/stdout):target/classes" sootup.examples.CallgraphExample
```

## Ожидаемый результат

Программа выводит:
1. Подклассы класса A (например: [D, C])
2. Вызовы методов из графа вызовов:
   - `Call:<B: void calc(A)> -> <A: int calc(int)> via virtualinvoke ...`
   - `Call:<B: void calc(A)> -> <C: int calc(int)> via virtualinvoke ...`
   - `Call:<B: void calc(A)> -> <D: int calc(int)> via virtualinvoke ...`

## Версия SootUp

Этот пример использует SootUp версии 2.0.0.

## Дополнительная информация

- [Документация SootUp](https://soot-oss.github.io/SootUp/latest/)
- [Документация по построению графов вызовов](https://soot-oss.github.io/SootUp/latest/callgraphs/)
