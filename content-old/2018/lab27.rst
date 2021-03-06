Строки, объекты-коллекции, объекты-функции и их аргументы, объекты-итераторы, списковые включения.
##################################################################################################

:date: 2019-04-16 06:30
:summary: Строки, объекты-коллекции, объекты-функции и их аргументы, объекты-итераторы, списковые включения.
:status: published
:published: yes

.. default-role:: code

.. contents:: Содержание


Строки, объекты-коллекции, объекты-функции и их аргументы, объекты-итераторы, списковые включения.
==================================================================================================


Функции и их аргументы.
-----------------------

Существуют некоторые правила для создания функций в Python.

Блок функции начинается с ключевого слова def, после которого следуют название функции и круглые скобки ( () ).

Любые аргументы, которые принимает функция, должны находиться внутри этих скобок.

После скобок идет двоеточие ( : ) и с новой строки с отступом начинается тело функции.

После создания функции, ее можно исполнять вызывая из другой функции или напрямую из оболочки Python. 
Для вызова функции следует ввести ее имя и добавить скобки.

Вызывая функцию, мы можем передавать ей следующие типы аргументов:

Обязательные аргументы (Required arguments).

Аргументы-ключевые слова (Keyword argument).

Аргументы по умолчанию (Default argument).

Аргументы произвольной длины (Variable-length argumens).


Пустая функция (stub).
++++++++++++++++++++++

Иногда, когда вы пишете какой-нибудь код, вам нужно просто ввести определения функции, которое не содержит в себе код.

Вот пример:

.. code:: python

   def empty_function():
      pass
        
Оператор pass - это пустая операция, она означает, что когда оператор pass выполняется, не происходит ничего.


Ключевое слово return.
++++++++++++++++++++++

Выражение return прекращает выполнение функции и возвращает указанное после выражения значение. 
Выражение return без аргументов это то же самое, что и выражение return None. 
Соответственно, теперь становится возможным, например, присваивать результат выполнения функции какой либо переменной.

Так как в Python функции являются объектами, то можно результатом работы функции может быть даже функция. 


Обязательные аргументы (Required arguments).
++++++++++++++++++++++++++++++++++++++++++++

Если при создании функции мы указали количество передаваемых ей аргументов и их порядок,
то и вызывать ее мы должны с тем же количеством аргументов, заданных в нужном порядке.

Например:

.. code:: python

    def max(a,b):
      if a > b:
        print(a)
      else:
        print(b)

    # В описании функции указано, что она принимает 2 аргумента
 
    # Корректное использование функции
    max(5,6)
 
    # Некорректное использование функции
    max()
    max(3)
    max(12,7,3)



Аргументы-ключевые слова (Keyword argument).
++++++++++++++++++++++++++++++++++++++++++++

Аргументы - ключевые слова используются при вызове функции. 
Благодаря ключевым аргументам, вы можете задавать произвольный (то есть не такой каким он описа при создании функции)
порядок аргументов.


Например:

.. code:: python

    def person(name, age):
        print (name, "is", age, "years old")
 
    # Хотя в описании функции первым аргументом идет имя, мы можем вызвать функцию вот так
 
    person(age=23, name="John")



Аргументы по умолчанию (Default argument).
++++++++++++++++++++++++++++++++++++++++++


Аргумент по умолчанию, это аргумент, значение для которого задано изначально, при создании функции.

Например: 

.. code:: python

    def max(a=0, b=0):
      if a > b:
        print(a)
      else:
        print(b)



Эту функцию можно вызвать вообще без аргументов, тогда она выведет 0. 


Аргументы произвольной длины (Variable-length argumens).
++++++++++++++++++++++++++++++++++++++++++++++++++++++++


Вы также можете настроить функцию на прием любого количества аргументов, или ключевых аргументов, при помощи особого синтаксиса.
Чтобы получить бесконечное количество аргументов, мы используем \*args, а чтобы получить бесконечное количество ключевых аргументов,
мы используем \*kwargs. Сами слова “args” и “kwargs” не так важны. Это просто сокращение. Вы можете назвать их \*a и \*b, 
и они будут работать таким же образом. Главное здесь – это количество звездочек. Обратите внимание: в дополнение к конвенциям
\*args и \*kwargs, вы также, время от времени, будете видеть andkw. Давайте взглянем на следующий пример:


.. code:: python

    def many(*args, **kwargs):
        print( args )
        print( kwargs )
 
    many(1, 2, 3, name="Mike", job="programmer")



Сначала мы создали нашу функцию, при помощи нового синтаксиса, после чего мы вызвали его при помощи трех обычных аргументов,
и двух ключевых аргументов. Функция показывает нам два типа аргументов. Как мы видим, параметр args превращается в кортеж, 
а kwargs – в словарь. 



Область видимости.
++++++++++++++++++


Некоторые переменные скрипта могут быть недоступны некоторым областям программы. Все зависит от того, где вы объявили эти переменные.

В Python две базовых области видимости переменных:

Глобальные переменные.

Локальные переменные.


Переменные, объявленные внутри тела функции, имеют локальную область видимости, 
те, что объявлены вне какой-либо функции, имеют глобальную область видимости.


Это означает, что доступ к локальным переменным имеют только те функции, в которых они были объявлены,
в то время как доступ к глобальным переменным можно получить по всей программе в любой функции.


Например:

.. code:: python

    # глобальная переменная age
    age = 44
 
    def info():
        print(age) # Печатаем глобальную переменную age
 
    def local_info():
        age = 22 # создаем локальную переменную age 
        print(age)
 
    info() # напечатает 44
    local_info() # напечатает 22



Важно помнить, что для того чтобы получить доступ к глобальной переменной, достаточно лишь указать ее имя. 
Однако, если перед нами стоит задача изменить глобальную переменную внутри функции - необходимо использовать ключевое слово global.

Например:


.. code:: python

    # глобальная переменная age
    age = 13
 
    # функция изменяющая глобальную переменную
    def get_older():
        global age
        age += 1
 
    print(age) # напечатает 13
    get_older() # увеличиваем age на 1
    print(age) # напечатает 14


Упражнение 0.
+++++++++++++


Напишите функцию max, которая принимает произвольное количество аргументов (чисел) или один список, 
и возвращает максимальное число (из последовательности чисел, или из списка).

Напишите аналогичную функцию sum.



Справка по функциям и классам.
------------------------------

В языке python есть встроенные механизмы, позволяющие отображать справку
по библиотекам, функциям и классам языка python. К таким механизмам
относятся документ-строки и функция ``help()``. Данная функция позволяет
вывести справочную информацию о другом объекте. Даже если вы знаете про
интересующий вас объект, иногда бывает полезно посмотреть
документ-строку к нему.


.. code:: python

    help(print)


.. parsed-literal::

    Help on built-in function print in module builtins:
    
    print(...)
        print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
        
        Prints the values to a stream, or to sys.stdout by default.
        Optional keyword arguments:
        file:  a file-like object (stream); defaults to the current sys.stdout.
        sep:   string inserted between values, default a space.
        end:   string appended after the last value, default a newline.
        flush: whether to forcibly flush the stream.
    

Эта справка описывается в так называемых документ-строках. Они позволяют
нужную информацию сохранить и показать. Документ-строки описываются в
функциях, классах, модулях в начале.

.. code:: python

    def spam(a, b):
        '''
        This is an example function. It returns sum of a and b.
        
        a: first value
        b: second value
        
        returns: sum of a and b
        '''
        return a+b

.. code:: python

    help(spam)


.. parsed-literal::

    Help on function spam in module __main__:
    
    spam(a, b)
        This is an example function. It returns sum of a and b.
        
        a: first value
        b: second value
        
        returns: sum of a and b
    
    

При написании своих программ не забывайте использовать документ-строки.
А если не знаете, что делает и какие параметры принимает функция или
для чего нужен кусок кода — не ленитесь заглядывать в справку, прежде чем
обращаться за помощью к гуглу и тем более преподавателю.

Упражнение 1.
+++++++++++++

Сколько аргументов принимает функция ``open``? Чем отличается
``mode="xb"`` и ``mode="wb"``? \*\*\*

Работа со строками
------------------

На практике со строками приходится работать достаточно часто. В виде
строк поступает вход из команды ``input()``, в виде текста читается
информация из файла. Поэтому важно разобрать, как именно можно работать
с текстовыми данными.

Текстовый данные в языке пайтон описываются классом ``str``:

.. code:: python

    print(type("qwerty"))


.. parsed-literal::

    <class 'str'>
    

При этом строка представляет из себя объект-коллекцию и есть возможность
получить доступ к отдельным ее элементам по индексу:

.. code:: python

    print("qwerty"[3])


.. parsed-literal::

    r
    

Строки в языке python являются неизменяемым типом, то есть для того,
чтобы изменить, удалить символ из строки или соединить 2 строки в одну,
в памяти создается другой объект-строка с результатом.

Первый метод строк, который мы рассмотрим -- это метод
``str.split(sep=None, maxsplit=-1)``. Он позволяет разбить строку на
список строк по определённому разделителю. Разделитель передаётся в
метод первым аргументом. Иногда необходимо разбить не всю строку, а
только первые ``n`` участков. Тогда используется аргумент ``maxsplit``,
который показывает, на сколько максимальным может быть индекс у результата
(т.е. максимальное количество частей — ``maxsplit + 1``):

.. code:: python

    s = "value1,value2,value3,value4,value5"
    
    for i in range(6):
        print(i, s.split(",", maxsplit=i))


.. parsed-literal::

    0 ['value1,value2,value3,value4,value5']
    1 ['value1', 'value2,value3,value4,value5']
    2 ['value1', 'value2', 'value3,value4,value5']
    3 ['value1', 'value2', 'value3', 'value4,value5']
    4 ['value1', 'value2', 'value3', 'value4', 'value5']
    5 ['value1', 'value2', 'value3', 'value4', 'value5']
    

Существует и противоположный метод -- ``str.join(iterable)``. Он
позволяет объединить список (или другой *итерируемый* объект) *строк* в одну.
При этом разделителем будет выступать исходная строка, у которой
мы и вызываем данный метод. ``join`` **НЕ ПРЕОБРАЗОВЫВАЕТ**
объект из коллекции в строку. Следовательно, если в коллекции встретится
не строка, метод вылетит с ошибкой.

.. code:: python

    lst = ['value1', 'value2', 'value3', 'value4', 'value5']
    
    print(";\n".join(lst))


.. parsed-literal::

    value1;
    value2;
    value3;
    value4;
    value5
    

Метод строк ``str.isdigit()`` позволяет проверить, состоит ли строка из
цифр.

.. code:: python

    print("asdf".isdigit())
    print("1234".isdigit())


.. parsed-literal::

    False
    True
    

При обработке строк бывает полезно привести их к нижнему или верхнему
регистру. Для этого могут использоваться методы ``str.lower()`` и
``str.upper()`` соответственно. Методы ``str.islower()`` и
``str.isupper()`` позволяют проверить, принадлежат ли все символы строки
к верхнему или к нижнему регистру соответственно.

.. code:: python

    print("QwErTy".islower())
    print("QwErTy".lower())


.. parsed-literal::

    False
    qwerty
    

Упражнение 2.
+++++++++++++

На вход вашей программе подаётся строка, состоящая из слов, разделённых
символом ``;``. Подсчитайте количество чисел, слов в нижнем и верхнем
регистре, и всех остальных слов. \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

Довольно часто вам приходится подставлять значения различных переменных
в ваши строки. Существует несколько способов сделать это. Рассмотрим
каждый из способов.

Первый и самый простой способ — простой сбор строк по кусочкам. При
этом переменные необходимо привести к строковому виду. Такой способ
порождает путаницу в коде и дополнительный мусор в памяти, так что
лучше стараться его избегать.

.. code:: python

    s = "Value1 = " + str(5) + ", Value2 = " + str(7.5) + ";"
    
    print(s)


.. parsed-literal::

    Value1 = 5, Value2 = 7.5;
    

Второй способ аналогичен форматированию в языке С. Этот метод довольно
прост, хотя и не слишком гибок. К достоинствам можно отнести, что он
является самым быстрым из перечисленных.

.. code:: python

    s = "Value1 = %02d, Value2 = %05.2f" % (5, 7.5)
    
    print(s)


.. parsed-literal::

    Value1 = 05, Value2 = 07.50
    

Третий способ — метод ``str.format()``. Он является наиболее pythonic
способом и обладает очень гибкими возможностями. Кроме простой
подстановки значений он также может

1. Позволяет получать значения в виде списка
2. Указывать номера аргументов
3. Использовать словари с названиями аргументов
4. Обращаться к атрибутам объектов и элементам коллекций
5. Является callabe и может передаваться в качестве аргумента другим
   функциям

Приведем пример к каждому из пунктов:

.. code:: python

    # 1
    args = [1, 2, 3]
    s = "{};{};{}".format(*args)
    print("1:\t", s)
    
    # 2
    s = "{2};{0};{1};{2};{1}".format(1, 2, 3)
    print("2:\t", s)
    
    # 3
    s = "{a};{c};{c};{b};{a}".format(a=1, b=2, c=3)
    print("3:\t", s)
    
    # 4
    s = "{0[1]}".format([1, 2, 3])
    print("4.1:\t", s)
    
    class Vector:
        def __init__(self, x, y):
            self.x = x
            self.y = y
    vec = Vector(5,6)
    
    s = "x: {0.x}; y: {0.y}".format(vec)
    print("4.2:\t", s)
    
    #5
    lst = [[0,1], [1,3], [5,6]]
    o_map = map("x={0[0]}, y={0[1]}".format, lst)
    for i, elem in enumerate(o_map):
        print("5.{}:\t".format(i+1), elem)
    


.. parsed-literal::

    1:	 1;2;3
    2:	 3;1;2;3;2
    3:	 1;3;3;2;1
    4.1:	 2
    4.2:	 x: 5; y: 6
    5.1:	 x=0, y=1
    5.2:	 x=1, y=3
    5.3:	 x=5, y=6
    

Упражнение 3.
+++++++++++++

Написать функцию, которая принимает на вход список чисел и возвращает
строку, содержащую минимум, максимум, и среднее значение в формате
(включая переносы строк):

.. raw:: html   

    min: 1 <br/>
    max: 10 <br/>
    mean: 5 *****

Цикл ``for``.
-------------

Цикл ``for`` может использоваться для различных целей.

Во многих современных языках программирования используют такие сущности, как итераторы. Основное их назначение – это 
упрощение навигации по элементам объекта, который, как правило, представляет собой некоторую коллекцию (список, словарь и т.п.).
Язык Python, в этом случае, не исключение и в нем тоже есть поддержка итераторов. Итератор представляет собой 
объект перечислитель, который для данного объекта выдает следующий элемент, либо бросает исключение, если элементов больше нет.

Основное место использования итераторов – это цикл for. Если вы перебираете элементы в некотором списке 
или символы в строке с помощью цикла for, то, фактически, это означает, что при каждой итерации цикла 
происходит обращение к итератору, содержащемуся в строке/списке, с требованием выдать следующий элемент,
если элементов в объекте больше нет, то итератор генерирует исключение, обрабатываемое в рамках цикла 
for незаметно для пользователя.

Как уже было сказано, объекты, элементы которых можно перебирать в цикле for, содержат в себе объект итератор, для того, 
чтобы его получить необходимо использовать функцию iter(), а для извлечения следующего элемента из итератора – функцию next().

Вызов функции next(itr) каждый раз возвращает следующий элемент из списка, а когда эти элементы заканчиваются, 
генерируется исключение StopIteration.

.. code:: python

    >>> itr = iter(num_list)
    >>> print(next(itr))
    1
    >>> print(next(itr))
    2
    >>> print(next(itr))
    3
    >>> print(next(itr))
    4
    >>> print(next(itr))
    5
    >>> print(next(itr))
    Traceback (most recent call last):
     File "<pyshell#12>", line 1, in <module>
        print(next(itr))
    StopIteration


Самый простой пример использования цикла:

.. code:: python

    for i in range(5):
        print(i)


.. parsed-literal::

    0
    1
    2
    3
    4
    

При помощи этого цикла можно итерироваться по любому объекту-коллекции:

.. code:: python

    lst = ["qwerty", 12345, 34.42]
    
    for i in lst:
        print(i)


.. parsed-literal::

    qwerty
    12345
    34.42
    

Но в таком случае встает вопрос, что же общего между объектом-коллекцией
и диапазоном значений? ``range`` является функцией. Попробуем
посмотреть, что эта функция возвращает:

.. code:: python

    a = range(5)
    
    print("object:\n\t", a)
    print("type:\n\t", type(a))
    print("Methods and attributes:\n\t", dir(a))


.. parsed-literal::

    object:
    	 range(0, 5)
    type:
    	 <class 'range'>
    Methods and attributes:
    	 ['__bool__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__reversed__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'count', 'index', 'start', 'step', 'stop']
    

То есть ``range`` -- это класс, и мы вызываем его конструктор. Объект
этого класса является итерируемым, а значит с ним может работать цикл
``for``. Чтобы создать итератор из объекта, воспользуемся функцией
``iter()``:

.. code:: python

    iterator = iter(a)
    
    print("object:\n\t", iterator)
    print("type:\n\t", type(iterator))
    print("Methods and attributes:\n\t", dir(iterator))


.. parsed-literal::

    object:
    	 <range_iterator object at 0x0000012FA12F9CF0>
    type:
    	 <class 'range_iterator'>
    Methods and attributes:
    	 ['__class__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__length_hint__', '__lt__', '__ne__', '__new__', '__next__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__setstate__', '__sizeof__', '__str__', '__subclasshook__']
    

Итератор — объект, который знает свое текущее состояние и может
вычислить следующее значение. Такой подход не приводит к созданию
дополнительных больших объектов в памяти и, таким образом, делает
программу более эффективной. Никакой лишней информации при этом в памяти
не хранится.

Для того, чтобы перейти к следующему состоянию, используется функция
``next()``.

.. code:: python

    print(next(iterator))
    print(next(iterator))
    print(next(iterator))
    print(next(iterator))
    print(next(iterator))


.. parsed-literal::

    0
    1
    2
    3
    4
    

Но что же происходит, когда мы пытаемся получить следующий объект, но
его не существует?

.. code:: python

    next(iterator)


::


    ---------------------------------------------------------------------------

    StopIteration                             Traceback (most recent call last)

    <ipython-input-19-4ce711c44abc> in <module>()
    ----> 1 next(iterator)
    

    StopIteration: 


В таком случае выпадает ошибка ``StopIteration``, которая говорит, что
следующий объект получить невозможно. Это и является признаком конца
итерации. На эту ошибку и ориентируется цикл ``for``.

Упражнение 4.
+++++++++++++

Вам дана функция на языке python:

::

    def print_map(function, iterable):
        for i in iterable:
            print(function(i))

Требуется переписать данную функцию не используя цикл for. \*\*\*\*

Рассмотрим несколько примеров итерируемых объектов, которые есть в языке
python (кроме ``range``).

**map(function, iterable)**

В начале рассмотрим функцию ``map(func, iterable)``. Эта функция
позволяет применить некоторую другую функцию ``func`` ко всем элементам
другого итерируемого объекта ``iterable``. **Обратите внимание, что
объект-функция передается без круглых скобок**

.. code:: python

    def baz(value):
        return value * value
    
    lst = [1, 2, 3, 4, 5]
    
    for i in map(baz, lst):
        print(i)


.. parsed-literal::

    1
    4
    9
    16
    25
    

**zip(iterable[, iterable, ...])**

Функция ``zip(iterable[, iterable, ...])`` позволяет параллельно
итерироваться по большому количеству итерируемых объектов, получая из
них соответствующие элементы в виде кортежа. Итератор прекращает свою
работу, когда один из переданных объектов закончится.

.. code:: python

    names = ["Alex", "Bob", "Alice", "John", "Ann"]
    age = [25, 17, 34, 24, 42]
    sex = ["M", "M", "F", "M", "F"]
    
    for values in zip(names, age, sex):
        print("name: {:>10} age: {:3} sex: {:2}".format(*values))


.. parsed-literal::

    name:       Alex age:  25 sex: M 
    name:        Bob age:  17 sex: M 
    name:      Alice age:  34 sex: F 
    name:       John age:  24 sex: M 
    name:        Ann age:  42 sex: F 
    

**filter(func, iterable)**

Пробегает по итерируемому объекту и возвращает только те элементы,
которые удовлетворяют условию, описанному в функции ``func``.

.. code:: python

    def bar(x):
        if abs((34-x*x))**0.5 > x:
            return True
        return False
    
    for i in filter(bar, [0, 1, 2, 3, 4, 5]):
        print(i)


.. parsed-literal::

    0
    1
    2
    3
    4
    

**enumerate(iterable, start=0)**

Принимает на вход итерируемый объект и возвращает пары (индекс элемента,
элемент). Индексация начинается со ``start``, который по умолчанию равен 0.

.. code:: python

    names = ["Alex", "Bob", "Alice", "John", "Ann"]
    
    for idx, elem in enumerate(names, 1):
        print("{:02}: {:>7}".format(idx, elem))


.. parsed-literal::

    01:    Alex
    02:     Bob
    03:   Alice
    04:    John
    05:     Ann
    

Кажется, что концепция генерации объектов налету, без предварительного
выделения памяти под целый массив, является довольно удобной и полезной.
Объекты-итераторы могут хранить, например, списки запросов к серверу,
логи системы и другую информацию, которую можно обрабатывать
последовательно. В таком случае, нам хочется научиться создавать
подобные объекты.

Для этих целей может использоваться ключевое слово ``yield``. Функция, в
которой содержится это ключевое слово, становится функцией-генератором.
Из такой функции можно создать объект-итератор. При вызове функции
``next()`` выполнение этой функции дойдет до первого встреченного
ключевого слова ``yield``, после чего, подобно действию ``return``,
управление перейдет основной программе. Поток управления вернется обратно
в функцию при следующем вызове ``next()`` и продолжит выполнение с того
места, на котором остановился ранее.

Рассмотрим, каким образом можно написать свою собственную функцию
``range()``:

.. code:: python

    def my_range(a, b=None, step=1):
        if b is None:
            a, b = 0, a
        _current = a
        while True:
            yield _current
            _next = _current + step
            if (_next - b)*(_current - b) <= 0:
                break
            _current = _next
                
    for i in my_range(5):
        print(i, end = " ")
    print()
    
    for i in my_range(1, 5):
        print(i, end = " ")
    print()
    
    for i in my_range(1, 10, 2):
        print(i, end = " ")
    print()
    
    for i in my_range(10, 0, -3):
        print(i, end = " ")
    print()


.. parsed-literal::

    0 1 2 3 4 
    1 2 3 4 
    1 3 5 7 9 
    10 7 4 1 
    

Упражнение 5.
+++++++++++++

Напишите генератор, выводящий первые n чисел Фибоначчи. \*\*\*

Кроме генераторов можно создавать целые итерируемые объекты, наподобие
``list``, или ``dict``, но об этом будет сказано немного позже.

Включения (list-, dict- comprehensions)
---------------------------------------

Еще одним очень мощным инструментом языка Python являются так называемые
*list comprehensions*. Они позволяют создавать списки из других
итерируемых объектов "на лету", при этом сочетают в себе возможности map
и filter.

Рассмотрим простой пример list comprehension, создающий список из
квадратов целых чисел:

.. code:: python

    a = [i*i for i in range(10)]
    
    print(type(a))
    print(*a)


.. parsed-literal::

    <class 'list'>
    0 1 4 9 16 25 36 49 64 81
    

Таким образом, list comprehension выглядит как список от выражения,
зависящего от элемента из итерируемого объекта. Однако, он может быть
гораздо более сложным. Вместо выражения может быть поставлена любая
функция от аргумента:

.. code:: python

    def eggs(x):
        return x-x*x/2+x*x*x/3-x*x*x*x/4
    
    a = [eggs(i) for i in range(5)]
    
    print(*a)


.. parsed-literal::

    0.0 0.5833333333333333 -1.3333333333333335 -12.75 -46.66666666666667
    

Кроме того, на значения итерируемых переменных можно накладывать
условия, которые также являются выражением:

.. code:: python

    a = [i*i for i in range(10) if i%2==0]
    
    print(*a)


.. parsed-literal::

    0 4 16 36 64
    

Таким образом, полная форма list comprehension имеет вид:

**[<expression(var)> for <var> in <iterable> if <condition(var)>]**

Однако, и это еще не всё. В одном list comphehension мы можем
итерироваться сразу по нескольким переменным:

.. code:: python

    a = [10*i+j for i in range(5) for j in range(5) if i>j]
    
    print(*a)


.. parsed-literal::

    10 20 21 30 31 32 40 41 42 43
    

Если необходимо в одном list comphehension использовать несколько
циклов, зависящих друг от друга, то стоит помнить, что циклы читаются
слева направо:

.. code:: python

    a = ["i={}, j={}, k={}".format(i,j,k) for i in range(5) for j in range(i) for k in range(j,i)]
    
    print(*a, sep="\n")


.. parsed-literal::

    i=1, j=0, k=0
    i=2, j=0, k=0
    i=2, j=0, k=1
    i=2, j=1, k=1
    i=3, j=0, k=0
    i=3, j=0, k=1
    i=3, j=0, k=2
    i=3, j=1, k=1
    i=3, j=1, k=2
    i=3, j=2, k=2
    i=4, j=0, k=0
    i=4, j=0, k=1
    i=4, j=0, k=2
    i=4, j=0, k=3
    i=4, j=1, k=1
    i=4, j=1, k=2
    i=4, j=1, k=3
    i=4, j=2, k=2
    i=4, j=2, k=3
    i=4, j=3, k=3
    

Упражнение 6.
+++++++++++++

Написать функцию ``flatten(tensor)``, принимающую на вход многомерный
список и возвращающую одномерный список всех элементов. Использовать
list comprehensions \*\*\*

Двумерные списки нужно создавать при помощи вложенных list
comprehensions. При этом во внутреннем можно использовать переменную,
созданную во внешнем.

**НИ В КОЕМ СЛУЧАЕ НЕЛЬЗЯ СОЗДАВАТЬ ДВУМЕРНЫЕ СПИСКИ ТАК: [[0] * n] * n**

.. code:: python

    a = [[x*y for y in range(10)] for x in range(10)]
    
    for i in a:
        print(("{:02} "*10).format(*i))


.. parsed-literal::

    00 00 00 00 00 00 00 00 00 00 
    00 01 02 03 04 05 06 07 08 09 
    00 02 04 06 08 10 12 14 16 18 
    00 03 06 09 12 15 18 21 24 27 
    00 04 08 12 16 20 24 28 32 36 
    00 05 10 15 20 25 30 35 40 45 
    00 06 12 18 24 30 36 42 48 54 
    00 07 14 21 28 35 42 49 56 63 
    00 08 16 24 32 40 48 56 64 72 
    00 09 18 27 36 45 54 63 72 81 
    

Упражнение 7.
+++++++++++++

Даны два списка a и b. Необходимо для всех положительных элементов i и j
из этих списков составить таблицу, в которой сосчитать модуль разности i
и j. \*\*\*

Интересной особенностью является то, что при замене квадратных скобок на
круглые создается объект-генератор это позволяет пользоваться удобной
конструкцией и при этом экономить память.

Кроме list comprehensions существуют также dict comprehensions. Они
позволяют в той же манере создавать словари. Рассмотрим пример:

.. code:: python

    names = ["Alex", "Bob", "Alice", "John", "Ann"]
    age = [25, 17, 34, 24, 42]
    
    d = {n : a for n,a in zip(names, age)}
    
    print(d)


.. parsed-literal::

    {'Alex': 25, 'Bob': 17, 'Alice': 34, 'John': 24, 'Ann': 42}
    

Безымянные функции (lambdas)
----------------------------

Некоторые из используемых функций, например ``map`` и ``filter`` требуют
передачи в качестве одного из аргументов функции. Очень часто такие
функции являются простыми однострочниками и не используются в дальнейшем
в программе. Однако при этом мы вынуждены выделять место, объявлять
функцию и вообще писать много лишнего кода. Для таких случаев можно
использовать безымянные функции — ``lambda``. Такие функции создаются
"на лету", а после использования удаляются из памяти. При этом,
lambda-функции являются объектами и их можно сохранять в переменные и
использовать в дальнейшем как обычные функции.

Приведем пример:

.. code:: python

    def foo(x):
        return x*x
    
    bar = lambda x: x*x
    
    print(foo(34))
    print(bar(34))


.. parsed-literal::

    1156
    1156
    

Используем lambda-функцию в качестве аргумента ``map``:

.. code:: python

    for i in map(lambda x: x*x, range(5)):
        print(i)


.. parsed-literal::

    0
    1
    4
    9
    16
    

lambda-функция не может содержать присваивания или нескольких операций.
Все операции в lambda-функции должны быть представлены в виде пайплайна,
когда каждая следующая функция вызывается от результата предыдущей, или
выражения. Внутри lambda-функций могут вызываться другие функции (и
другие lambda-функции тоже).

Объявление lambda-функции создает в памяти callable-объект, который
можно вызвать прямо на месте:

.. code:: python

    print( ( lambda x: int(int(input()) > x) ) (5) )


.. parsed-literal::

    7
    1
    

lambda-функция может принимать несколько аргументов, a может и не иметь
аргументов вовсе.

.. code:: python

    names = ["Alex", "Bob", "Alice", "John", "Ann"]
    age = [25, 17, 34, 24, 42]
    
    for i in map(lambda x, y: "{} is {} years old".format(x,y), names, age):
        print(i)
        
    print( (lambda: input()) () )


.. parsed-literal::

    Alex is 25 years old
    Bob is 17 years old
    Alice is 34 years old
    John is 24 years old
    Ann is 42 years old
    6
    6
    

Самые отчаянные могут попытаться с использованием lambda-функций
реализовывать даже очень сложные программы. Но тогда вам придется
освоить рекурсию при использовании lambda-функций, а это уже не совсем
тривиальная задача. Циклов то не будет. Ниже приведен пример функции,
вычисляющей факториал числа.

.. code:: python

    fact = lambda x: (
                    lambda f, *a: f(f, *a)
                    )(
                            lambda fun, n: 
                                    1 if n<=1 else n * fun(fun, n-1),
                     x)
    
    fact(3)

Упражнение 8 \* (для храбрых).
++++++++++++++++++++++++++++++

Реализуйте вычисление n-го числа Фибоначчи используя только
lambda-функции \*\*\*

Для групп 838 и 843
===================

.. _`Кратчайшие пути в невзвешенных графах`: /algo/extra/BFS.pdf

`Кратчайшие пути в невзвешенных графах`_
