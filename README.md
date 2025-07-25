# Автосервис
## Описание миссии, задач разрабатываемого программного продукта:
Миссия программы - Автоматизация выполнения различных видов деятельности автосервиса для повышения эффективности работы сервиса и наблюдения за статистическими показателями для улучшения работы.
В ходе эксплуатации планируется решить следующие задачи:
-   Простое формирование новых заявок и редактирование существующих
-   Управление списком сотрудников, формирование персонального расписания
-   Управление списком оказываемых услуг
-   Отслеживание статуса заявки

## Диаграмма классов
![](./img/Classes.jpg "Диаграмма классов")

### 📦 Список классов

- **Person** – абстрактный класс, от него наследуются Client и Employee.
- **Client** – класс, представляющий собой клиента сервиса.
- **Employee** – класс, представляющий собой сотрудника сервиса.
- **Auto** – класс, представляющий собой автомобиль.
- **EmployeeTimetable** – класс, представляющий собой расписание сотрудника.
- **Role** – класс, представляющий собой роль сотрудника. У каждой роли есть ряд прав (Permission).
- **Permission** – класс, представляющий собой определённое действие в системе. С помощью этого класса вместе с Role регулируются права пользователей в системе.
- **Service** – класс, представляющий собой оказываемую услугу.
- **Order** – класс, представляющий собой заявку на ремонт.
- **ServiceInOrder** – класс, связывающий услугу и заказ. С помощью него, можно видеть какой механик оказывал определённую услугу, в какие сроки.
- **SparePart** – класс, представляющий собой описание запчасти клиента.
- **PurchaseSparePart** – класс, представляющий собой запчасти, которые купил сам сервис.
- **Branch** – класс, представляющий собой филиал автосервиса.
- **BranchTimetable** – класс, представляющий собой расписание филиала.


## Диаграмма действий
### Выполнение заявки
![](./img/Activity.jpg "Выполнение заявки")

## Диаграмма прецедентов
![](./img/UseCase.jpg)

Диаграмма отображает взаимодействие пользователей с системой автосервиса. Она показывает, какие действия доступны различным ролям.

---

## 👥 Акторы и их действия

| Актор        | Доступные действия                                                  |
|--------------|---------------------------------------------------------------------|
| **Клиент**   | - Просмотр свободных мастеров и их графика                          | 
|              | - Просмотр статуса своей машины                                     |
| **Админ**    | - Управление заявками (добавление, удаление, просмотр)              |
|              | - Управление клиентами (просмотр, изменение, заказы)                 |
|              | - Работа с услугами и запчастями (добавление, описание, включение)   |
|              | - Управление сотрудниками (добавление, изменение, удаление, просмотр)|  
|              | - Доступ к спискам сотрудников и клиентов                            |
| **Директор** | - Просмотр филиалов                                                 |
|              |  - Работа с аналитикой (прибыль, популярные услуги)                  |
|              |  - Доступ к спискам сотрудников и клиентов                            |



---

## 🧾 Основные прецеденты

### 📦 Заявки
- Добавление заявки  
- Удаление заявки  
- Просмотр списка заявок  
- Просмотр конкретного заказа

### 👤 Клиенты
- Просмотр списка клиентов  
- Просмотр конкретного клиента  
- Изменение данных клиента  
- Просмотр заказов клиента

### 🛠 Услуги и запчасти
- Добавление услуги  
- Описание услуги  
- Включение услуги  
- Просмотр списка запчастей

### 👨‍🔧 Сотрудники
- Добавление сотрудника  
- Изменение сотрудника  
- Удаление сотрудника  
- Просмотр информации о сотруднике  
- Просмотр списка сотрудников

### 📈 Аналитика
- Просмотр прибыли  
- Самая популярная услуга

---

## 🗂 Обозначения

- 🟡 **Жёлтые овалы** — действия системы (прецеденты).
- 🟣 **Розовые овалы** — сущности или списки (например, заявки, клиенты).
- 👤 **Серые человечки** — акторы (пользователи системы: Клиент, Админ, Директор).

---

> 📌 Диаграмма позволяет визуально определить, какие функции доступны конкретной роли и как они взаимодействуют с объектами системы.

## ER-диаграмма
![](./img/ER.png)
## 🗂️ Структура базы данных

### 📦 Таблицы и их описание

#### **Clients**
- `id` – первичный ключ
- `Name` – имя клиента
- `Login` – логин
- `Password` – пароль
- `PhoneNum` – номер телефона
- `DelTime` – отметка удаления

#### **Autos**
- `id` – первичный ключ
- `id_Client` – внешний ключ на `Clients`
- `Brand` – марка авто
- `DelTime` – отметка удаления

#### **Employees**
- `id` – первичный ключ
- `Name` – имя
- `Login` – логин
- `Password` – пароль
- `PhoneNum` – номер телефона
- `Salary` – зарплата
- `AdditionalInfo` – доп. информация
- `id_Branch` – внешний ключ на `Branches`
- `id_role` – внешний ключ на `Roles`
- `DelTime` – отметка удаления

#### **Branches**
- `id` – первичный ключ
- `Address` – адрес филиала
- `id_Boss` – внешний ключ на `Employees` (руководитель)
- `PhoneNum` – номер телефона
- `DelTime` – отметка удаления

#### **Orders**
- `id` – первичный ключ
- `Price` – цена
- `Date_add` – дата создания
- `id_Employee` – внешний ключ на `Employees`
- `id_Branch` – внешний ключ на `Branches`
- `Status` – статус заказа
- `Date_Finish` – дата завершения
- `Date_Cancel` – дата отмены
- `id_Auto` – внешний ключ на `Autos`
- `DateDiagnostics` – дата диагностики
- `Comment` – комментарий

#### **Services**
- `id` – первичный ключ
- `Name` – название услуги
- `Price` – стоимость
- `time_Work` – продолжительность
- `DelTime` – отметка удаления

#### **ServiceInOrder**
- `id_Service` – внешний ключ на `Services`
- `id_Order` – внешний ключ на `Orders`
- `Count` – количество единиц услуги  
(вместе `id_Service + id_Order` — составной первичный ключ)

#### **Roles**
- `id` – первичный ключ
- `name` – название роли
- `DelTime` – отметка удаления

#### **Permissions**
- `id` – первичный ключ
- `Name` – имя действия
- `Code` – системное обозначение
- `DelTime` – отметка удаления

#### **RolePerm**
- `id_Role` – внешний ключ на `Roles`
- `id_Perm` – внешний ключ на `Permissions`  
(вместе `id_Role + id_Perm` — составной первичный ключ)

---

### 🔗 Связи между таблицами

- `Clients` ⟶ `Autos` — клиент владеет авто
- `Autos` ⟶ `Orders` — заказ связан с машиной
- `Employees` ⟶ `Orders` — заказ выполняет сотрудник
- `Branches` ⟶ `Employees`, `Orders` — филиал содержит сотрудников и заказы
- `Orders` ⟶ `ServiceInOrder` ⟶ `Services` — заказ включает услуги
- `Employees` ⟶ `Roles` — сотрудник имеет роль
- `Roles` ⟶ `Permissions` через `RolePerm` — роли связаны с правами доступа


