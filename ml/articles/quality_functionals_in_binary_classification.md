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

![equation](https://latex.codecogs.com/gif.latex?F_1&space;=&space;\dfrac{2}{\dfrac{1}{Precision}&space;&plus;&space;\dfrac{1}{Recall}}&space;=&space;\dfrac{2TP}{2TP&space;&plus;&space;FP&space;&plus;&space;FN})

6. ### F_beta-мера

![equation](https://latex.codecogs.com/gif.latex?F_{\beta}&space;=&space;\dfrac{1}{\dfrac{\alpha}{Precision}&space;&plus;&space;\dfrac{1&space;-&space;\alpha}{Recall}}&space;=&space;\dfrac{1}{\alpha}\dfrac{Precision&space;\cdot&space;Recall}{Recall&space;&plus;&space;(\dfrac{1}{\alpha}&space;-&space;1)&space;\cdot&space;Precision}&space;\newline&space;\beta^2&space;=&space;\dfrac{1}{\alpha}&space;-&space;1&space;\newline&space;F_{\beta}&space;=&space;(1&space;&plus;&space;\beta^2)&space;\cdot&space;\dfrac{P&space;\cdot&space;R}{R&space;&plus;&space;\beta^{2}\cdot&space;P})

При использовании F_beta-меры линии уровня «перекашиваются», один из критериев (точность или полнота) становится важнее при
оптимизации.

7. ### Specificity (True Negative Rate)

Показывает процент правильно классифицированных объектов негативного класса.

![equation](https://latex.codecogs.com/gif.latex?TNR&space;=&space;\dfrac{TN}{TN&space;&plus;&space;FP})

8. ### False Positive Rate (fall-out, false alarm rate)

Показывает долю объектов негативного класса, которые мы ошибочно отнесли к положительному.

![equation](https://latex.codecogs.com/gif.latex?FPR&space;=&space;\dfrac{FP}{TN&space;&plus;&space;FP})

9. ### Коэффициент Мэтьюса (MCC)

Применяется на несбалансированных выборках. Лежит в отрезке [-1, 1].

![equation](https://latex.codecogs.com/gif.latex?MCC&space;=&space;\dfrac{TP&space;\cdot&space;TN&space;-&space;FP&space;\cdot&space;FN}{\sqrt{(TP&space;&plus;&space;FP)(TP&space;&plus;&space;FN)(TN&space;&plus;&space;FP)(TN&space;&plus;&space;FN)}})

Давайте разберёмся, что означает эта «сложная формула». Рассмотрим среднее геометрическое точности и полноты:

![equation](https://latex.codecogs.com/gif.latex?\sqrt{P&space;\cdot&space;R}&space;=&space;\sqrt{\dfrac{TP}{TP&space;&plus;&space;FP}&space;\cdot&space;\dfrac{TP}{TP&space;&plus;&space;FN}}&space;=&space;\dfrac{TP}{\sqrt{(TP&space;&plus;&space;FP)&space;\cdot&space;(TP&space;&plus;&space;FN)}})

Теперь возьмём среднее геометрическое точности и полноты класса 0 (т.е. считая это класс положительным), перемножив эти
средние геометрические, получим:

![equation](https://latex.codecogs.com/gif.latex?\sqrt{P&space;\cdot&space;P_0&space;\cdot&space;R&space;\cdot&space;R_0}&space;=&space;\dfrac{TP&space;\cdot&space;TN}{\sqrt{(TP&space;&plus;&space;FP)(TP&space;&plus;&space;FN)(TN&space;&plus;&space;FP)(TN&space;&plus;&space;FN)}})

10. ### Каппа Коэна (Cohen's Kappa)

Его идея довольно простая: поскольку использование точности (Accuracy) вызывает сомнение в задачах с сильном дисбалансом классов, надо её значения немного перенормировать. Делается это с помощью статистики chance adjusted index: мы точность нашего решения (Accuracy) пронормируем с помощью точности, которую можно было получить случайно (Accuracychance). Под случайной здесь понимаем точность решения, которое получено из нашего случайной перестановкой ответов.

11. ### Сбалансированная точность (Balanced Accuracy)

![equation](https://latex.codecogs.com/gif.latex?BA&space;=&space;\dfrac{R_1&space;&plus;&space;R_0}{2}&space;=&space;\dfrac{1}{2}\left(\dfrac{TP}{TP&space;&plus;&space;FN}&space;&plus;&space;\dfrac{TN}{TN&space;&plus;&space;FP}\right&space;))

Если в бинарной задаче классификации представителей двух классов примерно поровну, то TP + FN ≈ TN + FP ≈ m/2 и сбалансированная точность примерно равна точности обычной (Accuracy).
