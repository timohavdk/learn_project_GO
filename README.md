# GO

---

## Инициализация переменных

- var - обычная переменная
- const - константное значение

Инициазизация перменной с использованием типа литералла значения (тип указывать не обязательно)
```go
x := 1 
```

Одновременная инициализация нескольких переменных
```go
var (
	x = 1
	y = 2
	z = 3
)
```

---

## Циклы

```go
for i := 1; i <= 10; i++ {
		
	}
```

В GO существует один вид цикла - for
* Инициализация параметра с которого начинается цикл в самом выражении цикла for 
может быть сделана только с помощью оператора присваивания - ':='

Либо с использованием 'var', но переменная выносится 
```go
var i = 1
	for i <= 10 {
		fmt.Println(i)
		i++
	}
```
---

## Условия

Аналогичные конструкции как и в JS, но пишутся без скобок

## Массивы 

```go
var x [10]string
```
Массив – это коллекция фиксированного размера. Акцент здесь ставится именно на фиксированный размер, поскольку, как только вы зададите длину массива, позже вы уже не сможете ее изменить.

Пример инициализации:
```go
var x [10]int
```
Данный массив заполниться значениями по умолчанию "0"
```go
var x [3]int{1 ,2, 3}
```
Данный массив заполниться полностью приведёнными значениями
```go
var x [3]int{1}
```
Данный массив заполниться только первым приведённым значением, остальные "0" [1, 0, 0]

### Использование цикла range

```go
for i, value := range x {
		fmt.Println(value, i)
	}
```
Первый элемент указвает на индекс элемента массива (i), второй указывает на значение этого элемента (value)б
заетм идёт присваивание того массива по котором проходят (:= range x)

```go
for _, value := range x {
		fmt.Println(value)
	}
```
Go не компилирует не используемые переменнные, поэтому нужно указывать символ "_", если переменная не будет использоваться

## Срезы

Срез это часть массива. Как и массивы, срезы индексируются и имеют длину. В отличии от массивов их длину можно изменить. Вот пример среза:
```go
var x []float64
```
Однако длина среза не может быть больше длинны массива, с которым он сввязан
```go
x := make([]float64, 5)
```
Создание среза с указанием длины (5)
```go
x := make([]float64, 5, 10)
```
Создание среза с указанием длины (5) и длины массива на котрый указывает срез (10)
```go
arr := [5]float64{1,2,3,4,5}
x := arr[0:5]
```
Другой способ создать срез — использовать выражение [low : high]. low - это позиция, с которой будет начинаться срез, а high - это позиция, где он закончится.

#### Функции срезов

- append
Добавляет элементы в конец среза
```go
slice1 := []int{1,2,3}
slice2 := append(slice1, 4, 5)
```
- copy
Копирует маскимально возможное количество элементов, остальные элементы игнорируются
```go
slice1 := []int{1,2,3}
slice2 := make([]int, 2)
copy(slice2, slice1)
```
В данном примере будут скопированны 1, 2

## Словари или Карты

Для использования необходимо сначала инициализировать карту

```go
x := make(map[string]int)
x["key"] = 10
fmt.Println(x["key"])
```
Выведет 10

Для удаления используется функция <i>delete</i>
```go
delete(x, "key")
```

Чтобы узнать он наличие элемента:
```go
name, ok := elements["Un"]
fmt.Println(name, ok)
```
Если элемент есть в словаре, возвращается значение по ключу и <i>true</i>, если нет, то результат <i>false</i>

---

## Функции

Аналогично с другими языками программирования

```go
func average(xs []float64) float64 {    
    total := 0.0
    for _, v := range xs {
        total += v
    }
    return total / float64(len(xs))
}
```
Общий вид функции возвращающая среднее значение в массиве

Возвращение нескольких значений:
```go
func f() (int, int) {
    return 5, 6
}
```

---

## Структуры

```go
type Circle struct {
    x float64
    y float64
    r float64
}

//Или

type Circle struct {
x, y, r float64
}
```

---

## Методы

```go
func (c *Circle) area() float64 {
    return math.Pi * c.r*c.r
}
```
(c *Circle) - получатель метода










