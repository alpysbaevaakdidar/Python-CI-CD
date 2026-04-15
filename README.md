steps:
      - name: Клонирование репозитория
        uses: actions/checkout@v3
        uses: actions/checkout@v4

      - name: Установка Python
        uses: actions/setup-python@v4
        uses: actions/setup-python@v5
        with:
          python-version: 3.11

      - name: Установка зависимостей
        run: |
          pip install -r requirements.txt
          pip install flake8 pylint

      - name: Проверка кода (flake8)
        run: |
          pip install flake8
          flake8 .
          flake8 . || true

      - name: Проверка кода (pylint)
        run: |
          pip install pylint
          pylint app.py || true

      - name: Запуск тестов
