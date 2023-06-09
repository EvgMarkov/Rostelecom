
Тестирование авторизации в ЛК "Ростелеком" https://b2c.passport.rt.ru/

Требования описаны в документе по ссылке https://lms.skillfactory.ru/assets/courseware/v1/f78e146f0eb3ace247a28b07e66467de/asset-v1:SkillFactory+QAP-3.0+2021+type@asset+block/Требования_SSO_для_тестирования_last.doc 

Реализованы тесты к "Стандартная авторизация по логину и паролю"<br>

План тестирования https://docs.google.com/document/d/1A8VJr8j6uE7i2IWWjds_6C-_PlMZDfkzLA_TucRJ5rI/edit?usp=sharing

Тест-кейсы https://docs.google.com/spreadsheets/d/138bUrmjh2UZ7r_gHpKGr8qk1hxT77BbZD94z2Kx94Ng/edit?usp=sharing

На вкладке "Форма авторизации" описаны тест-кейсы по проверке наличия на странице авторизации всех описанных в требованиях элементов<br>
На вкладке "Авторизация" описаны тест-кейсы по авторизации в ЛК Ростелеком<br>
Найденные баги описаны на вкладке "Баги" в документе с тест-кейсами

При создании тест-кейсов использованы техники позитивного тестирования для проверки авторизации на сайте различными способами, описанными в технических требованиях, и негативного тестирования для проверки невозможности доступа в личный кабинет с неподходящими данными и оповещения пользователя об ошибке доступа. В негативном тестировании используются классы эквивалентности для подбора вариантов данных для тестов.

При проведении тестов возможно появление капчи в форме авторизации. В этом случае сразу после ввода данных в полях логин и пароль нужно кликнуть в поле ввода капчи и за 20 сек. ввести текст с картинки. Если не успеть это сделать, тест будет провален.

Негативные тесты на авторизацию с пустым паролем отмечены как xfail, т.к. все время падают - на сайте нет предупреждения о вводе пароля.

__________________________________________________________________________________________________________________________________

В каталоге /pages располагаются файлы

base_page.py - описание класса BasePage - страница сайта<br>
auth_page.py - описание класса AuthPage, наследующего BasePage - страница авторизации<br>
locators.py - описание класса AuthLocators - используемые локаторы на странице авторизации<br>
settings.py - данные об эл.почте, телефоне, пароле и другие, которые используются для тестов<br>

В каталоге /tests располагаются файлы с тестами:

test_auth_page_elements.py - проверки наличия на странице авторизации всех описанных в требованиях элементов (FT-001 - FT-010)<br>
test_positive_auth.py - реализация позитивных тест-кейсов авторизации пользователя в ЛК Ростелеком (AT-001 - AT-005)<br>
test_negative_auth.py - реализация негативных тест-кейсов авторизации пользователя в ЛК Ростелеком (AT-006 - AT-019)<br>

В корне

conftest.py - фикстура с веб-драйвером и пост-обработкой ошибки (скриншот)<br>
requirements.txt - файл с требуемыми для проекта библиотеками (pytest, pytest-selenium, selenuim)<br>
terminal.txt - файл с результатом работы тестов 

Для запуска нужно выполнить в корне проекта команду python -m pytest -v --driver Chrome --driver-path=chromedriver.exe tests/ 
