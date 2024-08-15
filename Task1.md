## Тест-кейсы для ручки register

**Метод:** POST

**Описание:** Тест-кейсы проверяют корректность работы ручки регистрации пользователя.

**1. Позитивная проверка: Успешная регистрация**

* **Входные данные:**
    * login: "valid_login"
    * email: "valid_email@example.com"
    * password: "StrongPassword123"
    * confirmPassword: "StrongPassword123"
* **Ожидаемый результат:**
    * code: 200
    * result: "Пользователь зарегистрирован успешно"
    * В базе данных создана новая запись пользователя с указанными данными.

**2. Позитивная проверка: Регистрация с пробелами в логине и email**

* **Входные данные:**
    * login: " login_with_spaces "
    * email: " email@example.com  "
    * password: "StrongPassword123"
    * confirmPassword: "StrongPassword123"
* **Ожидаемый результат:**
    * code: 200
    * result: "Пользователь зарегистрирован успешно"
    * В базе данных создана новая запись пользователя с логином "login_with_spaces" и email "email@example.com".

**3. Негативная проверка: Отсутствует обязательное поле login**

* **Входные данные:**
    * email: "valid_email@example.com"
    * password: "StrongPassword123"
    * confirmPassword: "StrongPassword123"
* **Ожидаемый результат:**
    * code: 400
    * result: "Ошибка: Отсутствует поле login"

**4. Негативная проверка: Неверный формат email**

* **Входные данные:**
    * login: "valid_login"
    * email: "invalid_email"
    * password: "StrongPassword123"
    * confirmPassword: "StrongPassword123"
* **Ожидаемый результат:**
    * code: 400
    * result: "Ошибка: Неверный формат email"

**5. Негативная проверка: Пароли не совпадают**

* **Входные данные:**
    * login: "valid_login"
    * email: "valid_email@example.com"
    * password: "StrongPassword123"
    * confirmPassword: "WrongPassword"
* **Ожидаемый результат:**
    * code: 400
    * result: "Ошибка: Пароли не совпадают"

**6. Негативная проверка: Пользователь с таким логином уже существует**

* **Входные данные:**
    * login: "existing_login"
    * email: "new_email@example.com"
    * password: "StrongPassword123"
    * confirmPassword: "StrongPassword123"
* **Ожидаемый результат:**
    * code: 409
    * result: "Ошибка: Пользователь с таким логином уже существует"

**7. Негативная проверка: Пользователь с таким email уже существует**

* **Входные данные:**
    * login: "new_login"
    * email: "existing_email@example.com"
    * password: "StrongPassword123"
    * confirmPassword: "StrongPassword123"
* **Ожидаемый результат:**
    * code: 409
    * result: "Ошибка: Пользователь с таким email уже существует"

