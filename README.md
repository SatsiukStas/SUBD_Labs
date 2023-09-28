Тема: Отель
Выполнил: Сацюк Станислав Владимирович
Группа: 153504

Функциональные требования:
1. Авторизация и управление пользователями: 
    Регистрация новых пользователей с указанием имени, фамилии, адреса электронной почты и пароля;
    Вход в систему с использованием логина и пароля.
   
2.Управление пользователями (CRUD):
    Создание новых пользователей с указанием основной информации;
    Просмотр информации о пользователях;
    Редактирование данных пользователя;
    Удаление данных пользователя.
    
3.Система ролей:
    Определение различных ролей пользователей (например, администратор, сотрудник авиакомпании, клиент и т.д.);
    Привязка ролей к пользователям;
    Управление правами доступа на основе ролей.
    
4.Журналирование действий пользователя:
    Регистрация всех действий, совершаемых пользователями в системе;
    Запись даты, времени и идентификатора пользователя при каждом действии.
    
5.Бронирование номеров:
    Регистрация всех действий, совершаемых пользователями в системе;
    Выбор необходимых условий и услуг.
    
6.Управление работой ремонтников и уборщиков:
  Контроль привязки работников к номерам.

Описание сущночтей БД:
1.Пользователь (Users):
    user_id (Идентификатор пользователя): INT (Primary Key)
    first_name (Имя): VARCHAR
    last_name (Фамилия): VARCHAR
    email (Адрес электронной почты): VARCHAR (уникальное значение)
    password (Пароль): varchar(Хешированный пароль)

    Ограничения: Нет дополнительных ограничений
    Связи: Относится к Roles(Many-to-One), Booking(One-to-Many).
    
  2.Роль (Roles):
    role_id (Идентификатор роли): INT (Primary Key)
    role_name (Название роли): VARCHAR (уникальное значение)

    Ограничения: Нет дополнительных ограничений.
    Связи: Связана с Users (One-to-Many).

  3.Журнал действий пользователя (UserActionLogs):
    action_id (Идентификатор действия): INT (Primary Key)
    user_id (Идентификатор пользователя): INT (Foreign Key)
    action_date_time (Дата и время действия): DATETIME
    action_description (Описание действия): VARCHAR

    Ограничения: Нет дополнительных ограничений.
    Связи: Связь с сущностью User (пользователь) Many-to-One.
    
  4.Бронирования (Bookings):
    booking_id (Идентификатор бронирования): INT (Primary Key)
    creation_date (Дата): DATETIME
    arrival_date (Дата заезда): DATETIME
    departure_date (Дата отъезда): DATETIME
    user_id (Идентификатор пользователя): INT (Foreign Key)
    room_id (Идентификатор номера): INT (Foreign Key)

    Ограничения: Нет дополнительных ограничений.
    Связи: Связь с User(Many-to-One), Services через таблицу ServicesBookings(Many-to-Many)

  5.Услуги (Services):
    service_id(Идентификатор услуги): INT (Primary Key)
    service_name(Наименование услуги): VARCHAR
    price(Цена услуги): INT

    Ограничения: Нет дополнительных ограничений.
    Связи: Связь с Bookings через таблицу ServicesBookings(Many-to-Many)

  6.Номера (Rooms):
    room_id(Идентификатор номера): INT (Primary Key)
    cleaenr_id (Идентификатор уборщика): INT (Foreign Key)
    repairer_id (Идентификатор ремонтника): INT (Foreign Key)
    room_type_id (Идентификатор типа номера): INT (Foreign Key)
    room_number(Номер комнаты): INT

    Ограничения: Нет дополнительных ограничений.
    Связи: Связь с Bookings(One-to-Many), RoomTypes(Many-to-One), Employees через таблицу RoomsEmployees(Many-to-Many)

  7.Типы номеров (RoomTypes):
    room_type_id(Идентификатор типа номера): INT (Primary Key)
    type_name(Наименование типа): VARCHAR
    max_people(Максимальное количество человек): INT
    price(Цена номера): INT

    Ограничения: Нет дополнительных ограничений.
    Связи: Связь с Rooms(One-to-Many)

  8.Сотрудники (Employees):
    employee_id(Идентификатор сотрудника): INT (Primary Key)
    employee_type_id (Идентификатор типа сотрудника): INT (Foreign Key)
    name(ФИО сотрудника): VARCHAR
    phone(Телефон): VARCHAR

    Ограничения: Нет дополнительных ограничений.
    Связи: Связь с Rooms через таблицу RoomsEmployees(Many-to-Many), EmployeeTypes(Many-to-One)

  9.Типы сотрудников (EmployeeTypes):
    employee_type_id(Идентификатор типа работника): INT (Primary Key)
    type_name(Наименование типа сотрудника): VARCHAR
    salary(Зарплата): INT

    Ограничения: Нет дополнительных ограничений.
    Связи: Связь с Employees(One-to-Many)

  10.Отзывы (Reviews):
    review_id(Идентификатор отзыва): INT (Primary Key)
    user_id (Идентификатор пользователя): INT (Foreign Key)
    text(Текст отзыва): VARCHAR
    mark(Оценка): INT(mark<=5)

    Ограничения: Нет дополнительных ограничений.
    Связи: Связь с Users(One-to-One)

https://ru.paste.pics/PHEH9
