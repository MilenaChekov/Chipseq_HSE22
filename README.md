# Chipseq_HSE22
в data приложен файл адаптеров (в колабе пришлось прикладывать, потому что путь к ним в триммоматик не нашла) и отчеты fastqc, а также таблица пиков xslx

<img width="883" alt="Снимок экрана 2022-12-19 в 22 21 49" src="https://user-images.githubusercontent.com/60537367/208503397-31fd8d90-7b4c-4e8c-80d3-d0c4ec1ce8fa.png">
<img width="1015" alt="Снимок экрана 2022-12-19 в 22 22 01" src="https://user-images.githubusercontent.com/60537367/208503430-eff2fae4-76ab-4993-be89-49fe89390979.png">
для начала смотрим с помощью fastqc файл. качество в целом хорошее, есть адаптеры

проверяем, вырезает ли их триммоматик (minlen ставим 50, так как такие риды ожидаем, по адаптерам поставила как в мануале, так как ожидаем 100% совпадение с адаптерами и как-то особо подбирать параметры не надо)

<img width="858" alt="Снимок экрана 2022-12-19 в 22 25 21" src="https://user-images.githubusercontent.com/60537367/208504088-4ec31da6-91a1-4d99-b666-bf350f725146.png">
<img width="821" alt="Снимок экрана 2022-12-19 в 22 25 31" src="https://user-images.githubusercontent.com/60537367/208504109-7c9718d4-f63b-4041-8a7a-60c2de1caa83.png">
действительно, от адаптеров избавились


картирование прошло хорошо

при запуске mac2 выдает, что ничего не нашел, поставьте --nomodel и extsize, поставила extsize 100 (рид*2)

получаем пики, обьединяем реплики, затем с помощью bedtools пересекаем аннотацию e.coli с нашими пиками

получаем вот такую таблицу


затем получаем из пиков fasta файл, запускаем в chipmunk

результаты:




примечание:
сначала я как-то получила вот такие пики для 1 образца только, и воспроизвести в будущем у меня почему-то не получилось, хотя вроде делала все то же самое, гены вот такие, и вроде данный транскрипционный фактор правда с ними связан (надо было возможно там и остановиться), соответственно моимв тоже нашла
<img width="281" alt="Снимок экрана 2022-12-19 в 23 33 36" src="https://user-images.githubusercontent.com/60537367/208516174-4a2ab7ce-2cb7-418b-889f-7b4b3f752013.png">
по ней видим, что наш фактор относится к оперону Uxu, можем проверить в интернете
<img width="916" alt="Снимок экрана 2022-12-19 в 23 49 17" src="https://user-images.githubusercontent.com/60537367/208520442-89bfe234-772d-465c-9df5-20a90b56ff09.png">
а также вот с кем он взаимодействует еще

судя по всему, функция белка - участие в углеводном обмене

результаты:
![image](https://user-images.githubusercontent.com/60537367/208517904-3e530791-d2ef-4603-b080-666c175107a1.png)
<img width="580" alt="Снимок экрана 2022-12-19 в 23 44 16" src="https://user-images.githubusercontent.com/60537367/208517966-84955b96-77a5-4c39-bc89-9964fae5cee7.png">
