# Модель, основанная на архитектуре PointNet по сегментации 3D облаков точек, обученная на датасете S3DIS.

## Структура проекта:
### Папка models:

- Содержит папки Area_1,...Area_6 - папки, в которых содержится датасет S3DIS.

- Папка camera - содержит настройки камеры для визуализации облака точек.

- Папка checkpoints - содержит сохранения модели в процессе обучения.

- Папка sliding_windows - содержит скользящие окна, необходимые для обучения и тестирования модели.

- Файлы objects.json и spaces.json - json-файлы, содержащие ID объектов и названий 
объектов и ID пространств и их названий.

- Файл s3dis_summary.csv - суммирующий файл по датасету, формируется в результате
обработка датасета

### Файлы приложения:

- settings.py - файл с настройками модели, структуры папок, визуализации.

- summarizer.py - модуль обработки набора данных для формирования s3dis_summary.csv, разметки облаков точек и
скользящих окон.

- dataset.py - классы для представления набора данных и создание dataloader'ов.

- model.py - модель нейронной сети, реализующая архитектуру PointNet

- trainer.py - класс для тренировки, тестирования и визуализации сегментации модели.

- visualizer.py - класс для рендера облака точек.

- main.py - основной, запускающий приложение модуль.

## Запуск приложения:

1. Загрузить исходный код
2. Перейти в папку с проектом
3. скачать файл 
Stanford3dDataset_v1.2_Aligned_Version.zip с сайта https://cvg-data.inf.ethz.ch/s3dis/
и распаковать его в папку models.
4. Ввести команду `python main.py -h`, который выведет справку по пользованию приложением.
5. Запустить необходимую команду.

## Особенности:

- При запуске `python main.py` запустится процесс дообучения модели, которая сохранена в последнем
чекпоинте в папке checkpoints, чтобы начать обучения новой сети, необходимо удалить папку checkpoints.

- Если необходимо посмотреть процесс обработки датасета, то необходимо очистить папку models, кроме удаления
папки checkpoints (если нет необходимости заново обучать модель) и скачать файл 
Stanford3dDataset_v1.2_Aligned_Version.zip с сайта https://cvg-data.inf.ethz.ch/s3dis/
и распаковать его в папку models, а далее необходимо запустить любую операцию в приложении,
обработка датасета произойдет перед выполняемым действием.

- Если есть обученная модель на определенном наборе данных (all, movable, structural), то
при всех дальнейших действиях в параметре --objects указывать тоот же набор.

- PNG файлы визуализации сегментации будут располагатьсяв папке camera.
