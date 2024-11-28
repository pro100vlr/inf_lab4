1. Изначально я выполнила работу, где программа нарисовала мне корову. Затем я создала папку aafire-network, переместилась с помощью cd в эту папку. Создала файл Dockerfile, открыла его командой open

<img width="389" alt="Снимок экрана 2024-11-28 в 12 29 07" src="https://github.com/user-attachments/assets/3b170aa2-e078-455a-b1e6-7306998b40d2">

2.Записала в файл:

<img width="509" alt="Снимок экрана 2024-11-28 в 12 33 58" src="https://github.com/user-attachments/assets/de1fc55a-f3d6-4c9e-8e47-d0423396a972">
В данном файле написано :
FROM ubuntu:latest - Указывает базовый образ для создания нового Docker-образа.Используется последний доступный образ Ubuntu.
RUN apt-get update && apt-get install -y libaa-bin && apt-get install -y iputils-ping - эта команда выполняется внутри контейнера на этапе его сборки. Что качается команды по частям :
apt-get update: Обновляет список доступных пакетов в менеджере apt. Это нужно, чтобы получить самую свежую информацию о версиях.
apt-get install -y libaa-bin: Устанавливает пакет libaa-bin.
В пакете libaa-bin содержится aafire.
apt-get install -y iputils-ping: Устанавливает утилиту ping, которая позволяет проверять доступность сетевых узлов.
Флаг -y: Указывает системе автоматически подтверждать установку пакетов (без запроса от пользователя).

3. Создала образ, затем запустила контейнер.
   
<img width="567" alt="Снимок экрана 2024-11-28 в 12 53 20" src="https://github.com/user-attachments/assets/955309d6-fb25-4ff9-bcb1-3118190a3a9f">

<img width="523" alt="Снимок экрана 2024-11-28 в 12 54 01" src="https://github.com/user-attachments/assets/d9dbbeda-305b-42f4-84c3-1594ba6688a8">

В интерактивном режиме docker run -it aafire-ping запустила контейнер и получила 

<img width="445" alt="Снимок экрана 2024-11-28 в 13 21 00" src="https://github.com/user-attachments/assets/2313d4a5-f073-4761-a29c-5df0ddddcc60">

4.Запустила 2 контейнера в фоновом режиме и добавила sleep infinity, чтобы контейнер отложил остановку работы на бесконечное время (то есть не останавливался вообще) и заодно назвала контейнеры как kont1 и kont2
<img width="705" alt="Снимок экрана 2024-11-28 в 13 23 36" src="https://github.com/user-attachments/assets/72cb6ab5-234f-4543-8cd3-90f1f62ae2aa">

5.Создала сеть myNetwork и подключила контейнеры к нему:

<img width="591" alt="Снимок экрана 2024-11-28 в 13 26 49" src="https://github.com/user-attachments/assets/bc8924dc-25f4-4da2-9c50-36adea99e0bb">

6.Далее я вошла в оболочку контейнера, чтобы из него запинговать другой контейнер и отправила пинг к другому контейнеру из оболочки первого контейнера:

<img width="602" alt="Снимок экрана 2024-11-28 в 13 29 21" src="https://github.com/user-attachments/assets/684395bb-ad98-440a-b095-e3b150759e4b">

Здесь видно, что связь установлена успешна(пакеты поступают, затем прервала работу).

7.Потом вышла из первого контейнера с помощью exit

8.Сделала аналогичную вещь и с контейнером kont2:

<img width="588" alt="Снимок экрана 2024-11-28 в 13 36 10" src="https://github.com/user-attachments/assets/ed3dd8f3-4dbc-4d67-94aa-9ca725ddb6b0">

9.Теперь при помощи следующей команды можно увидеть настройки созданной мной сети:

<img width="695" alt="Снимок экрана 2024-11-28 в 13 37 11" src="https://github.com/user-attachments/assets/ee7727bb-d1eb-4260-a036-be4855b68a56">


10.Команда docker ps отображает список запущенных контейнеров в моей системе. Это полезный инструмент для управления и мониторинга активных контейнеров.

<img width="686" alt="Снимок экрана 2024-11-28 в 13 38 13" src="https://github.com/user-attachments/assets/6f7e08aa-e5f0-40dc-bf2f-8fdb9dcf710f">

Затем я остановила их работу:

<img width="716" alt="Снимок экрана 2024-11-28 в 13 53 10" src="https://github.com/user-attachments/assets/9ce7c92d-7f1b-4633-8687-50a3dfb90cda">

