# ArcGIS Connector - Wide to Long Transformation

Проект для трансформации данных из Google Sheets (Wide формат) в Long формат и загрузки в ArcGIS Feature Layer.

## Требования

- Python 3.8+
- Anaconda или Jupyter Notebook
- Доступ к Google Sheets
- Аккаунт ArcGIS Online

## Установка

1. Установите зависимости:
```bash
pip install -r requirements.txt
```

2. Для работы с Google Sheets:
   - **Вариант A (OAuth - проще)**: При первом запуске откроется браузер для авторизации
   - **Вариант B (Service Account)**: 
     - Создайте Service Account в Google Cloud Console
     - Скачайте JSON ключ
     - Сохраните как `credentials.json` в папке проекта
     - Поделитесь Google Sheet с email из Service Account

3. Для работы с ArcGIS:
   - **Вариант 1 (OAuth - рекомендуется)**: При первом запуске откроется браузер для входа в ArcGIS
   - **Вариант 2 (API Key)**: Если есть API Key, используйте его в коде
   - **Вариант 3 (Username/Password)**: Менее безопасно, но работает

## Использование

1. Откройте `arcgis_connector.ipynb` в Jupyter Notebook
2. Запустите ячейки по порядку
3. При необходимости авторизуйтесь в Google и ArcGIS через браузер

## Структура данных

### Входные данные (Google Sheets)
- Дата, Область, Місто
- Значення 1-10
- long, lat (координаты)

### Выходные данные (ArcGIS Feature Layer)
- d_date, t_region, t_city
- i_value_1 до i_value_10
- Геометрия (точки на карте)

## Feature Layer ID
```
6f8eb77db2dc41cc8261eb836e4b35af
```

## Проблемы и решения

### Проблема: Не могу найти Client ID и Client Secret для ArcGIS
**Решение**: Используйте OAuth авторизацию через браузер:
```python
gis = GIS()  # Откроет браузер для входа
```

### Проблема: Ошибка доступа к Google Sheets
**Решение**: 
- Убедитесь, что таблица доступна (публичная или вы поделились доступом)
- Проверьте авторизацию в браузере

### Проблема: Ошибка при загрузке в ArcGIS
**Решение**:
- Проверьте права доступа к Feature Layer
- Убедитесь, что координаты в правильном формате (long, lat)
- Проверьте типы данных полей

## Результат

После выполнения скрипта:
- Данные из Google Sheets трансформированы в формат Wide to Long
- Точки нанесены на карту ArcGIS
- При клике на точку отображается popup с данными (Дата, Область, Місто, Значення 1-10)

## Формат сдачи проекта

Проект включает:
- `arcgis_connector.ipynb` - основной Jupyter Notebook с кодом
- `requirements.txt` - зависимости Python
- `README.md` - документация

**Рекомендуемый формат сдачи:**
1. GitHub репозиторий (ссылка на репозиторий)
2. Или ZIP-архив со всеми файлами проекта

## Контакты

При возникновении проблем проверьте:
1. Логи в Jupyter Notebook
2. Настройки доступа в Google Sheets
3. Права доступа в ArcGIS Online
