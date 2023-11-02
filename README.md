Здравствуйте, меня зовут Петр. Здесь я поделюсь мыслями о тестовом задании и коротко прорезюмирую решение.

Task 1: Grid Representation
Основная проблема - выбрать алгоритм заполнения сетки. Я выбрал случайную генерацию пар координат и сохранение их в множество.
Использование структуры данных "множество" избавляет от необходимости проверки повторения пары координат, поскольку
множество не может содержать дубликаты. Такой алгоритм имеет линейную сложность, но наличие фактора случайности портит картину.
Можно решить эту задачу создав всевозможные пары координат, перемешать список с ними и взять нужное количество.
Такой алгоритм имеет большую сложность (N^2) и требует больше памяти. Зато не зависит от генерации случайных чисел

Task 2: Tower Coverage
Тут бы я предложил использовать не плоскость(grid) а трехмерный массив. На первом уровне оставить открытые и блокированные
клетки и вышки, а на втором уровне(слое) располагать покрытие вышек. Но в ТЗ нужно работать с Grid, поэтому и работал с
друмерным массивом. В принципе, сложностей нет. Ставим вышку и в квадрате "вокруг" неё ставим покрытие.

Task 3: Optimization Problem
Уже сложная задача, несколько конфликтующая c Task 4. Если располагать минимум вышек, они (в идеале) не будут пере-
крывать друг друга, из-за чего поиск пути между ними будет невозможен.
Но есть более сложная задача - расставить их логично. Так, в моем решении, они ставятся даже у краев, что неоптимально.
Написание оптимального алгоритма с минимизацией вышек я бы совместил с bonus task 1, а пока что сделал неоптимальный
и "ленивый" алгоритм.

Task 4: Path Reliability
Эта задача конфликтует с предыдущей. Чтобы добиться минимума башен, необходимо, чтобы своими радиусами они лишь касались.
В таком случае, между ними невозможно найти путь. Я устанавливал башни в Task 3 специально не оптимально(чтобы они
пересекались радиусами), и добавил(возможно лишнее) условие, что если они касаются радиусами(а не находятся в радиусе),
то между ними есть связь. Если такое решение не подходит, окей, можно немного изменить алгоритм размещения башен из Task 3

Task 5: Visualization
Здесь все просто:
1. Отображение сетки города изначально с препятствиями и зонами, которые необходимо покрыть.
2. Отображение города с покрытием и вышками (и препятствиями, если процент застройки высокий).
3. Отображение пути из одной вышки в другую.
Использовал Matplotlib. Не знаю, что ещё писать.

Bonus tasks (optional):
1. Это уже NP задача, для её решения нужно хорошо подумать и потратить ещё день-два на её решение. Решение предыдущих
задач заняло у меня прилично времени, и я предпочел отправить задание без её решения.

2. Тут уже точно нужно использовать трехмерный массив. Причем я бы предложил для вышки с каждым уровнем сигнала для ка-
ждого уровня сигнала использовать соответствующий "уровень" в массиве, для чистоты ришения. Ну и это просто задача сложнее,
чем предыдущая.


Test assignment 
for the Junior Python Developer position


Imagine that a telecommunications company is working on designing an efficient 7G-network layout for a new city. The city can be represented as a grid, where some blocks are obstructed and cannot have towers, while others can. The goal is to provide the maximum coverage with the minimum number of towers.

Task 1: Grid Representation

Create a class CityGrid that can represent the city as an N x M grid. During the initialization of the class, obstructed blocks are randomly placed with coverage >30% (we can change this parameter).

Task 2: Tower Coverage

Each tower has a fixed range R (in blocks) within which it provides coverage. This coverage is a square, with the tower in the center.
Implement a method in the CityGrid class to place a tower and visualize its coverage.

Task 3: Optimization Problem

Design an algorithm to place the minimum number of towers such that all of non-obstructed blocks are within the coverage of at least one tower. The algorithm cannot place towers on obstructed blocks.
Implement a method in the CityGrid class to display the placement of towers.

Task 4: Path Reliability

Imagine that data is transmitted between towers. For simplicity, assume that each tower can directly communicate with any other tower within its range.
Design an algorithm to find the most reliable path between two towers. The reliability of a path decreases with the number of hops (tower-to-tower links). So, a path with fewer hops is more reliable.

Task 5: Visualization

Implement functions to visualize the CityGrid, including obstructed blocks, towers, coverage areas, and data paths.
Use any Python plotting library of your choice, such as matplotlib or seaborn.

Bonus tasks (optional):
1. Extend the optimization problem: Now towers have a cost, and you have a limited budget. Modify your algorithm to maximize coverage while staying within the budget.

2. Consider different types of towers with different ranges and costs. How would this change your optimization approach?

