# hse21_hw3
**Сравнение RNA-seq данных перепрограммированных SRR3414629, SRR3414630, SRR3414631 и контрольных SRR3414635, SRR3414636, SRR3414637 мышиных эмбриональных фибробластов и нахождение генов, которые наиболее сильно изменяют свою экспрессию в этом процессе:**

## 1) Ссылки на Google Colab 
* По первой части: https://colab.research.google.com/drive/1JBOKndF5FhoQwbXzeZarR-FnNfYYQ68H
* По второй части: https://colab.research.google.com/drive/1JxxpLYljj-9jsZoraEDJYCEdKhwr8jq1#scrollTo=BBJpGbSWGXCW
## 2) Скриншоты и статистика из файла Multiqc:
<img width="1185" alt="Снимок экрана 2021-12-01 в 16 18 40" src="https://user-images.githubusercontent.com/91221560/144242537-ee013bf4-81f3-406f-9c8f-ac026b55e0bc.png">

 <img width="1120" alt="Снимок экрана 2021-12-01 в 16 21 18" src="https://user-images.githubusercontent.com/91221560/144242570-38b87ce5-42af-4966-800c-af331054c5b9.png">
 
 <img width="1120" alt="Снимок экрана 2021-12-01 в 16 21 28" src="https://user-images.githubusercontent.com/91221560/144242594-cd51ab43-1b19-42cb-8c3b-37239a655e7e.png">


<img width="1120" alt="Снимок экрана 2021-12-01 в 16 21 39" src="https://user-images.githubusercontent.com/91221560/144242672-ff116d09-4e80-4468-85de-721fa2fdb2e1.png">


<img width="1127" alt="Снимок экрана 2021-12-01 в 16 22 07" src="https://user-images.githubusercontent.com/91221560/144242690-7015be02-78de-40a0-8f80-d363cf344ee2.png">

<img width="1127" alt="Снимок экрана 2021-12-01 в 16 22 17" src="https://user-images.githubusercontent.com/91221560/144242710-e4f9521b-b4af-48d5-afe8-0ee11f5ca3b8.png">

<img width="1127" alt="Снимок экрана 2021-12-01 в 16 22 23" src="https://user-images.githubusercontent.com/91221560/144242727-1e28930c-1553-4a0d-a26a-fa7b89fc5618.png">

<img width="1127" alt="Снимок экрана 2021-12-01 в 16 22 36" src="https://user-images.githubusercontent.com/91221560/144242753-abed52a7-24bf-44ef-91ef-b45bab79eac3.png">

<img width="1127" alt="Снимок экрана 2021-12-01 в 16 22 45" src="https://user-images.githubusercontent.com/91221560/144242789-07111087-b2f2-4682-9f37-ab1e7e39939a.png">

## 3) Таблица со статистикой по каждому из 6 образцов:
<img width="1102" alt="Снимок экрана 2021-12-01 в 17 11 36" src="https://user-images.githubusercontent.com/91221560/144249502-a3159afa-7f87-485d-a9e6-c28d6d6cce96.png">

## Подсчет:

<img width="1102" alt="Снимок экрана 2021-12-01 в 17 17 42" src="https://user-images.githubusercontent.com/91221560/144250865-15956654-bbac-422b-9f2d-c220766dde49.png">
<img width="1102" alt="Снимок экрана 2021-12-01 в 17 18 14" src="https://user-images.githubusercontent.com/91221560/144250894-649e5065-4c68-40ad-b910-b093825930be.png">

<img width="1102" alt="Снимок экрана 2021-12-01 в 17 18 41" src="https://user-images.githubusercontent.com/91221560/144250912-d11451d6-84b6-4a94-a4b1-6eec5628eefb.png">

## 4) Получаем ALL.counts и ALL.info:

<img width="1102" alt="Снимок экрана 2021-12-01 в 17 24 30" src="https://user-images.githubusercontent.com/91221560/144251952-f52aa91c-7200-4f9f-a114-ebbec696650f.png">
<img width="1131" alt="Снимок экрана 2021-12-01 в 17 25 12" src="https://user-images.githubusercontent.com/91221560/144251993-59295deb-c115-4077-aada-2e4b013b256e.png">

**Поиск генов, которые значимо поменяли свою экспрессию в результате перепрогроммирования с помощью R-пакета DESeq2:**

## 5) Графики из анализа DESeq2:

* MA-plot:
На этом графике 1 точка - это 1 ген, мы установили раннее порог на значимость pvalue 0.01, гены с таким pvalue обозначены синим цветом.
По оси X - средняя экспрессия генов (правее - больше экспрессии), по Y - log fold change.

* Анализируя полученный график, видим, что больше генов, у которых экспрессия возросла, так как больше точек у которых log fold change больше 0.

* Log2(Fold change) = log2(Среднее значение RPM эксперимент / Среднее значение RPM контроль).

<img width="545" alt="Снимок экрана 2021-12-01 в 17 38 32" src="https://user-images.githubusercontent.com/91221560/144254234-4904c4f2-ac4e-43c0-8667-c404f966832b.png">

* Тепловая карта показывает, что все контрольные образцы похожи между собой и все перепрограмированные образцы похожи между собой, а образцы контроль отличаются от образцов эксперимента. По диагонали идентичны так как там c1 с c1, с2 с c2 и тд

<img width="828" alt="Снимок экрана 2021-12-01 в 18 02 39" src="https://user-images.githubusercontent.com/91221560/144259049-123cebeb-4e7c-45ab-8b48-783545c2ab86.png">

* На следующем графике видна разница экспрессий (20 наиболее дифференциально экспрессированных генов), например если посмотреть на первую строчку, то видим, что в контроле этот ген сильно экспрессировался (красный цвет), а в эксперименте его экспрессия упала (оранжевый цвет). Значения обозначены цветами:
<img width="814" alt="Снимок экрана 2021-12-01 в 18 09 06" src="https://user-images.githubusercontent.com/91221560/144259909-dcc61687-3286-48a5-81b3-e3b99ef87247.png">

