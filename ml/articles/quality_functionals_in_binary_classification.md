## Функциналы качества в бинарной классификации

1. ### Accuracy

Доля объектов, на которых алгоритм выдал правильные ответы.

![equation](https://latex.codecogs.com/gif.latex?Accuracy&space;=&space;\dfrac{1}{m}\sum\limits_{i&space;=&space;1}^{m}I\[a_i&space;=&space;y_i\])

Явный недостаток: невалидна в случае дисбаланса классов, потому что с точки зрения точности выгодно почти всегда
выдавать метку самого популярного класса.


![equation](https://latex.codecogs.com/gif.latex?Accuracy&space;=&space;\dfrac{TN&space;&plus;&space;TP}{TP&space;&plus;&space;TN&space;&plus;&space;FP&space;&plus;&space;FN})

2. ### Виды ошибок классификатора

    * ошибка первого рода (Type 1 Error) -- объект ошибочно относится к положительному классу;
    * ошибка второго рода (Type 2 Error) -- объект ошибочно относится к отрицательному классу.


3. ### Recall (TPR, Sensitivity, Hit Rate)

Показывает, какой процент объектов нами правильно классифицирован.

![equation](https://latex.codecogs.com/gif.latex?TPR&space;=&space;\dfrac{TP}{TP&space;&plus;&space;FN})

4. ### Precision (Positive Predictive Value)

Показывает, какой процент положительных объектов правильно классифицирован.

![equation](https://latex.codecogs.com/gif.latex?PPV&space;=&space;\dfrac{TP}{TP&space;&plus;&space;FP})


Точность и полнота -- "ортогональные" критерии качества. Легко построить алгоритм со 100%-й полнотой: он все объекты относит к классу 1, но при этом точность может быть очень низкой. Нетрудно построить алгоритм с близкой к 100% точностью: он относит к классу 1 только те объекты, в которых уверен, при этом полнота может быть низкая.


5. ### F_1-мера

Это просто среднее гармоническое Precision и Recall. Его максимизация приводит к максимизации и Precision, и Recall.

![equation](https://latex.codecogs.com/gif.latex?F_1&space;=&space;\dfrac{2}{\dfrac{1}{Precision}&space;&plus;&space;\dfrac{1})

6. ### F_beta-мера

![equation](https://latex.codecogs.com/gif.latex?F_{\beta}&space;=&space;\dfrac{1}{\dfrac{\alpha}{Precision}&space;&plus;&space;\dfrac{1&space;-&space;\alpha}{Recall}}&space;=&space;\dfrac{1}{\alpha}\dfrac{Precision&space;\cdot&space;Recall}{Recall&space;&plus;&space;(\dfrac{1}{\alpha}&space;-&space;1)&space;\cdot&space;Precision}&space;\newline&space;\beta^2&space;=&space;\dfrac{1}{\alpha}&space;-&space;1&space;\newline&space;F_{\beta}&space;=&space;(1&space;&plus;&space;\beta^2)&space;\cdot&space;\dfrac{P&space;\cdot&space;R}{R&space;&plus;&space;\beta^{2}\cdot&space;P})
