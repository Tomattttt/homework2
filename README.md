# Шерстобитова Тамара ФТ-320008 (2)
## Создание контейнера FastAPI
FastAPI — это современный, быстрый (высокопроизводительный) веб-фреймворк для построения API на Python, основанный на стандартных типах Python.

Работа была выполнена в WSL. В корневой директории данного проекта (предварительно сохраненного на компьютер) я создала Dockerfile, без расширения txt. В него занесла необходимые данные для контейнеризации. 

# Используем официальный образ Python в качестве базового образа
FROM python:3.9-slim

# Устанавливаем рабочую директорию в контейнере
WORKDIR /app

# Копируем текущую директорию в рабочую директорию контейнера
COPY . /app

# Устанавливаем зависимости
RUN pip install --no-cache-dir -r requirements.txt

# Открываем порт, на котором будет работать приложение
EXPOSE 8000

# Команда для запуска приложения
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]

Далее перехожу в директорию своего проекта: cd /home/tomat/fastapi-fastapi-741b95a и собираю образ с помощью команды docker build -t myfastapiapp .

![image](https://github.com/user-attachments/assets/a280890f-bca1-41a4-9845-2fb95e9f2c7d)

Далее запускаю контейнер с помощью команды docker run -d -p 8000:8000 myfastapiapp

![image](https://github.com/user-attachments/assets/4a36aaab-7301-4070-bb3b-3d477858db2b)

Завершаю работу проверкой, что контейнер был успешно запущен командой docker ps

![image](https://github.com/user-attachments/assets/664e6603-a542-405e-80c2-e3b3ccd3a0a5)

Теперь приложение FastAPI должно быть доступно по адресу http://localhost:8000

Проверка логов контейнера в реальном времени с помощью команды docker logs -f a434ff8bfa80

![image](https://github.com/user-attachments/assets/6439fff5-1a39-44bd-86d1-0f7178dc7bfe)


