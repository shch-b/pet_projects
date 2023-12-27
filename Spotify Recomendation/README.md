# Музыкальные рекомендации

## Описание
База данных Spotify содержит более 100 млн треков, из которых 98% практически никогда не прослушиваются. В свободном доступе распространяется большое количество датасетов, содержащих основную информацию о треках, прослушиваемых на Spotify, содержащих общую информацию о композиции и другие характеристики треков, например, стиль, танцевальность, энергичность. 
Всего в различных сырых или преобработанных датасетах содержится от 19 до 40 различных атрибутов, характеризующих тот или иной трек.
Наполненность треков также различная, т.к. различны методы их сбора. В основном для сбора данных используется специализированная библиотека Spotipy.
Мной предварительно были собраны 5 наборов данных (перечень и ссылки ниже в описании на англ. яз.). Всего данные наборы содержат примерно 3 млн записей о композициях, при этом % пересечений в данных наборах минимален - 79 тыс. одинаковых треков в 2-х датасетах, содержащих 1 млн и 1,2 млн композиций. Недостатки датасетов - отсутствие в некоторых наборах некоторых атрибутов, например данных о популярности, моде, годе выпуска, жанре.

Всего для работы были определены 19 необходимых для дальнейшего анализа атрибутов.

**Цель работы**: 

*Основная*: разработать рекомендательную модель, которая на вход будет получать трек/артиста/стиль и на выходе будет выдавать перечень рекомендуемых треков, совпадающих по определенным характеристикам целевому треку/артисту/стилю и пр. В научных публикациях и статьях встречал некоторые обзоры, как вообще формируются плейлисты. Попробовать также применить адаптированную модель для формирования "настроенческих" плейлистов. Для этого потребуется найти и изучить дополнительные ресурсы и наборы данных, содержащих подобную информацию.

*Второстепенные*: 
1) используя методы ML научиться предсказывать некоторые значения и характеристики треков, которые отсутсвуют в наборе. Например, предположительно среди 3 млн треков у 450 тыс. будет отсутствовать значения популярности, которые можно предсказать. Например, используя сведения из пересечений датасетов (в одном датасете есть трек А с указанной популярностью, в другом для аналогичного трека популярность не указана). Аналогично для других отсутсвующих характеристик.
2) провести общий EDA собранного массива, описать музыку в числах в различных разрезах, найти некоторые неоднозначные взаимосвязи
3) выдвинуть и проверить некоторые гипотезы, например, подтвердить или опровергнуть утверждения типа "композиции в стиле ХХХ, созданные после 2020 года громче и энергичнее аналогичных треков в таком же стиле на ХХ%, но меньше по инструментальности ...".
Для подобного анализа также будут использованы дополнительные наборы, например, собираемые в рамках проекта https://everynoise.com/, с помощью которых начальный набор будет обогащен и дополнен.

*Третьестепенные*: 
1) попробовать собрать отсутсвующую информацию с помощью Spotipy
2) на основании доп данных о популярности треков и топ-списках сравнить Spotify с Я.Музыкой

# В чем возможная ценность

Существующий EDA, который проводится на основании разных наборов данных, как мне кажется не достаточно полный, т.к. выполняется "в общем" - таких треков в стиле А в 2010 на Х% больше, чем в 2011, корреляция между енергичностью и танцевальностью 0,7. В основной массе похожих проектов изучаются общие количественные характеристики, но полноценной исследовательской работы не проводится.
+ не совсем понятен принцип сбора датасетов, методиrа попадания трека в датасет. В данном проекте массив собран из различных источников и, возможно, такой объединенный массив для анализа позволит внести больше случайности в выборку, которая будет лучше характеризовать всю генсовокупность песен Spotify. 
-------------------------------------------------------------------
# Spotify Recomendation Project

## Description
Spotify includs more than 100 million songs, maybe 98% of songs have never been listened. The main idea of porject is to collect data about songs/tracks from Spotify, to study the main characteristics of songs, their distribution, differences, explore music in the context of styles and other attributes. 
Based on the analysis, I want to develop a prototype of a recommendation system for selecting songs for certain queries and creating playlists for some conditions.

1) **Load and transform Spotify tracks databases from Kaggle**

Data (examples, not full list):
https://www.kaggle.com/datasets/thedevastator/spotify-tracks-genre-dataset  https://www.kaggle.com/datasets/cesaregarza/everynoise-database-with-spotify-features  https://www.kaggle.com/datasets/tonygordonjr/spotify-dataset-2023 
https://www.kaggle.com/datasets/amitanshjoshi/spotify-1million-tracks
https://www.kaggle.com/datasets/rodolfofigueroa/spotify-12m-songs

Datasets provide comprehensive information about Spotify tracks:
- track name, id, artists name, album name, etc.
- release year
- track characteristics, for example: popularity, danceability, energy, valence, tempo, etc.

Each dataset contains different list of characteristics, sometimes in some dataset there isn't 2 or 3 characteristics like popularity or time signature, or mode. Sometimes - different types and writing styles of names

2) **Data preprocessing**:
- data cleaning (omissions, duplicates, etc.)
- datasets comparision, intersection search 
- cast
- formation of samples for training and forecasting of individual variables (popularity)
- ...

3) **Data enrichment**. For example with additional datasets:
- https://www.kaggle.com/datasets/georgeggcoco/closeness-of-music-genres/code
- https://www.kaggle.com/datasets/cesaregarza/everynoise-database-with-spotify-features

4) EDA

5) Modeling, clasterisation, segmentation.

6) ?? Hypothesis, A/B testing
For example: the tempo/energy/volume... of tracks in the XXX style after 2020 is higher by YY% than tracks from 2010-2020, but their instrumentality has decreased
